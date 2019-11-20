FROM nginx
RUN apt-get update -qq && apt-get -y install apache2-utils

# establish where Nginx should look for files

ENV RAILS_ROOT /var/www/app

# Set our working directory inside the image

WORKDIR $RAILS_ROOT

# create log directory

RUN mkdir log


COPY server/nginx.conf /tmp/docker.nginx


RUN envsubst '$RAILS_ROOT' < /tmp/docker.nginx > /etc/nginx/conf.d/default.conf

EXPOSE 80

CMD [ "nginx", "-g", "daemon off;" ]
