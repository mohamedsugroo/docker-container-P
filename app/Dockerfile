FROM ruby:2.6.5
RUN apt-get update -qq && apt-get install -y build-essential libpq-dev nodejs
# Set an environment variable where the Rails app is installed to inside of Docker image
ENV RAILS_ROOT /var/www/app
RUN gem install bundler
RUN gem install puma

RUN mkdir -p $RAILS_ROOT
# Set working directory
WORKDIR $RAILS_ROOT
# Adding gems
COPY  Gemfile Gemfile
COPY  Gemfile.lock Gemfile.lock
RUN bundle install --jobs 20 --retry 5 --without development test
# Adding project files
COPY . .

RUN bundle install

EXPOSE 3000
