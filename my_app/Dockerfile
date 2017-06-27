# Base image:
FROM ruby:2.4.1
 
# Install dependencies
RUN apt-get update -qq && apt-get install -y build-essential libpq-dev nodejs
 
# Set an environment variable where the Rails app is installed to inside of Docker image:
ENV RAILS_ROOT /var/www/my_rails_app
ENV RAILS_ENV production
RUN mkdir -p $RAILS_ROOT
 
WORKDIR $RAILS_ROOT
 
# Gems:
COPY Gemfile* ./
RUN gem install bundler
RUN bundle install
 
#COPY config/puma.rb config/puma.rb
 
# Copy the main application.
COPY . .

EXPOSE 3000
 
# The default command that gets ran will be to start the Puma server.
CMD bundle exec puma -C config/puma.rb

# FROM phusion/passenger-ruby23
# # set some rails env vars
# ENV RAILS_ENV production
# ENV BUNDLE_PATH /bundle

# # set the app directory var
# ENV APP_HOME /home/app
# WORKDIR $APP_HOME
# RUN apt-get update -qq

# # Install apt dependencies
# RUN apt-get install -y --no-install-recommends \
#   build-essential \
#   curl libssl-dev \
#   git \
#   unzip \
#   zlib1g-dev \
#   libxslt-dev \
#   mysql-client \
#   sqlite3

# # install bundler
# RUN gem install bundler
# COPY Gemfile* ./
# RUN bundle install
# ADD . .

# # compile assets!
# RUN bundle exec rake assets:precompile
# EXPOSE 3000
# CMD ["/sbin/my_init"]