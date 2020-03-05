FROM ruby:2.5.1

RUN apt-get update && apt-get -y upgrade && apt-get install -y nodejs
RUN gem install rails --version 5.2.0
RUN mkdir -p /opt/app

COPY ./app /opt/app

ONBUILD WORKDIR /opt/app
ONBUILD RUN bundle install
ONBUILD RUN rake db:create
ONBUILD RUN rake db:migrate
ONBUILD RUN rake db:seed

# rake db:migrate. Migrations setup the tables in the database. Using rake db:migrate you can apply any new changes to your schema.
# rake db:seeds loads the data from db/seeds.rb into the database. This is generally used for development and production databases. It's
#	permanent data that you use to start an empty application. 
# 's' is an alias for 'server'
# -b binds an IP address
# -p specifies port