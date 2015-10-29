FROM php:5.6-fpm
RUN apt-get update && apt-get install -y php5-common php5-cli php5-fpm php5-mcrypt php5-mysqlnd php5-apcu php5-gd php5-imagick php5-curl php5-intl
ADD devops-pool.conf /etc/php5/fpm/pool.d/
COPY ./src /myapp
WORKDIR /myapp
VOLUME /myapp
RUN usermod -u 1000 www-data
RUN rm /usr/local/bin/php && \
    ln -s /usr/bin/php5 /usr/local/bin/php
CMD ["php5-fpm", "-F"]
EXPOSE 9000
