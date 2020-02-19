FROM debian

ENV TS3SERVER_LICENSE=accept

WORKDIR /home/teamspeak

EXPOSE 9987/udp 10011 30033

RUN apt-get update -y && apt-get upgrade -y &&\
	apt-get install -y wget bzip2 &&\
	wget https://files.teamspeak-services.com/releases/server/3.11.0/teamspeak3-server_linux_amd64-3.11.0.tar.bz2 &&\
	tar -xf teamspeak3-server_linux_amd64-3.11.0.tar.bz2 &&\
	rm teamspeak3-server_linux_amd64-3.11.0.tar.bz2

WORKDIR /home/teamspeak/teamspeak3-server_linux_amd64/

ENTRYPOINT sh ts3server_minimal_runscript.sh

# docker build -t ex01 .				to start
# docker run -it --rm -p=9987:9987/udp  -p=10011:10011 -p=30033:30033 ex01	to execute

# https://www.teamspeak.de/en/index/
# https://files.teamspeak-services.com/releases/server/3.11.0/teamspeak3-server_linux_amd64-3.11.0.tar.bz2
# tar x, --extract, --get	Extract files from an archive.
# -f, --file=ARCHIVE	Use archive file (or device) ARCHIVE.
# docker build -t ex01 . && docker run -it --rm -p=9987:9987/udp  -p=10011:10011 -p=30033:30033 ex01
# https://support.teamspeak.com/hc/en-us/articles/360002712257-Which-ports-does-the-TeamSpeak-3-server-use-
# The WORKDIR	instruction sets the working directory for any RUN, CMD, ENTRYPOINT, COPY and ADD instructions that follow it in the Dockerfile
# An ENTRYPOINT	allows you to configure a container that will run as an executable.
# The EXPOSE	instruction informs Docker that the container listens on the specified network ports at runtime.
# https://support.teamspeak.com/hc/en-us/articles/360002712257-Which-ports-does-the-TeamSpeak-3-server-use-	WHICH PORTS DOES THE TEAMSPEAK 3 SERVER USE
# https://support.teamspeak.com/hc/en-us/articles/360002712998-How-to-accept-the-server-license-agreement-Server-3-1-0-	HOW TO ACCEPT THE SERVER LICENSE AGREEMENT