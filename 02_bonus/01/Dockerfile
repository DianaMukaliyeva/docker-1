FROM debian

RUN apt-get update -y && apt-get upgrade -y\
	&& apt-get install -y vim valgrind build-essential git
RUN mkdir project

COPY . project

WORKDIR /project

ENTRYPOINT /bin/bash