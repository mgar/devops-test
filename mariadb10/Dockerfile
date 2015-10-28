FROM mariadb
COPY ./db/structure.sql /tmp/structure.sql
RUN /bin/bash -c "/usr/bin/mysqld_safe &" && \
  sleep 5 && \
  mysql -h 127.0.0.1 -u root < /tmp/structure.sql
