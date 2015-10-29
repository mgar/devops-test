FROM centos
USER root

RUN yum update -y
RUN yum -y install mariadb-server

ADD db/structure.sql /tmp/structure.sql
RUN /usr/libexec/mariadb-prepare-db-dir
RUN /usr/bin/mysqld_safe --basedir=/usr & \
   sleep 10s && \
   /usr/bin/mysqladmin -u root password 'root' && \
   mysql --user=root --password=root < /tmp/structure.sql && \
   mysql -u root -proot -e "GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY 'root';" && \
   mysql -u root -proot -e "FLUSH PRIVILEGES;" && \
   mysqladmin shutdown --password=root
EXPOSE 3306
ENV TERM dumb
CMD ["--basedir=/usr"]
ENTRYPOINT ["/usr/bin/mysqld_safe"]
