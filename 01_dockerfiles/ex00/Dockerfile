FROM alpine
RUN apk update && apk upgrade && apk add --no-cache vim
# https://docs.alpinelinux.org/user-handbook/0.1a/Working/apk.html#_upgrading_packages
# The --no-cache argument prevents apk from caching the package index - something that would normally take up precious space, as well as go stale quickly.

ENTRYPOINT vim
# An ENTRYPOINT allows you to configure a container that will run as an executable

#	docker build -t ex00 .		Build
#	--tag , -t				Name and optionally a tag in the ‘name:tag’ format
#	docker run --rm -ti ex00	Run
