FROM ubuntu

RUN apt-get update -y && apt-get upgrade -y &&\
	apt-get install -y wget openssh-server ca-certificates postfix

RUN wget https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh && bash script.deb.sh
RUN EXTERNAL_URL="http://gitlab.example.com" apt-get install -y gitlab-ce tzdata

# RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
RUN sed -i "s/# grafana\['enable'\] = true/grafana['enable'] = false/g" /etc/gitlab/gitlab.rb
EXPOSE 443 80 22

ENTRYPOINT (/opt/gitlab/embedded/bin/runsvdir-start &) && sleep 2 && gitlab-ctl reconfigure && tail -f /dev/null

# https://gitlab.com/gitlab-org/omnibus-gitlab/issues/4257
#			For those running in a container, and not using our own docker image. The package is expecting an init system to start our runit service.
#			Without an initsystem. You need to start it yourself. After installing and before running reconfigure, run: /opt/gitlab/embedded/bin/runsvdir-start & to start the runit service in the background.