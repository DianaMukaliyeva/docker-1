FROM ruby:2.4.1

RUN apt-get update && apt-get -y upgrade && apt-get install -y nodejs sqlite3
RUN gem install sprockets --version 3.7.2
RUN gem install rails --version 5.1
RUN mkdir -p /opt/app

COPY ./app /opt/app

ONBUILD WORKDIR /opt/app
ONBUILD RUN bundle install
ONBUILD RUN rake db:create
ONBUILD RUN rake db:migrate
ONBUILD RUN rake db:seed
#'s' is an alias for 'server'
# -b binds an IP address
# -p specifies port