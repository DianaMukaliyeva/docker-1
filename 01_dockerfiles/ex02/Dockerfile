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


# My Dockerfile will create a container that launch an application called "Rails Signup Thankyou". This application requires:
# 	Ruby 2.5.1
# 	Rails 5.2.0 

# --------------------------------TO TEST -----------------------------------

# mkdir ft_rails
# mv Dockerfile ./ft_rails
# cd ft_rails
# git clone https://github.com/RailsApps/rails-signup-thankyou.git app
# docker build -t ft-rails:on-build .
# cd ..
# echo "FROM ft-rails:on-build
# EXPOSE 3000
# CMD [\"rails\", \"s\", \"-b\", \"0.0.0.0\", \"-p\", \"3000\"]" > Dockerfile
# docker build -t ex02 . && docker run -it --rm -p 3000:3000 ex02

# ----------------------------------------------------------------------------

# 's' is an alias for 'server'
# -b binds an IP address
# -p specifies port
# mkdir -p. The -p flag will create nested directories.
# ONBUILD instruction adds to the image a trigger instruction to be executed at a later time, when the image is used as the base for another build.
# COPY instruction copies new files or directories from <src> and adds them to the filesystem of the container at the path <dest>.
# WORKDIR instruction sets the working directory for any RUN, CMD, ENTRYPOINT, COPY and ADD instructions that follow it in the Dockerfile
# bundle install. Install all of the required gems
# Rake		is a utility built into Ruby and Rails, which provides an efficient way for managing database changes:
#	rake db:create. When you create your Rails application for the first time, it will not have a database yet. In order for it to start,
#			you will need to make sure the database is up and running.
#	rake db:migrate. Migrations setup the tables in the database. Using rake db:migrate you can apply any new changes to your schema.
#	rake db:seeds loads the data from db/seeds.rb into the database. This is generally used for development and production databases.
#			It's permanent data that you use to start an empty application. 
# https://dev.to/neshaz/how-to-use-rake-db-commands-in-the-correct-way--50o2