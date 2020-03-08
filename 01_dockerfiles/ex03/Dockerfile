FROM ubuntu

RUN apt-get update -y && apt-get upgrade -y &&\
	apt-get install -y wget openssh-server ca-certificates postfix

RUN wget https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh && bash script.deb.sh
RUN apt-get install -y  --no-install-recommends gitlab-ce tzdata

RUN apt-get clean
# RUN rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN sed -i "s/# grafana\['enable'\] = true/grafana['enable'] = false/g" /etc/gitlab/gitlab.rb
# “ruby_block[authorize Grafana with GitLab] action run” takes a lot of time and I disabled it

EXPOSE 443 80 22

ENTRYPOINT (/opt/gitlab/embedded/bin/runsvdir-start &) && sleep 2 && gitlab-ctl reconfigure && tail -f /dev/null

# docker build -t ex03 .				to start
# docker run -it --rm -p 8080:80 -p 8022:22 -p 8443:443 --privileged ex03	to execute

# https://about.gitlab.com/install/?version=ce#ubuntu , but instead of curl I used wget

# (tail -f /dev/null)	needed to keep Docker containers runnig: http://bigdatums.net/2017/11/07/how-to-keep-docker-containers-running/
# (/opt/gitlab/embedded/bin/runsvdir-start &)	The package is expecting an init system to start our runit service. We need to start it ourrself.
#		https://gitlab.com/gitlab-org/omnibus-gitlab/issues/4257
