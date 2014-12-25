FROM centos:centos7
#FROM centos:latest
#FROM centos
MAINTAINER Vitaly Natarov <solo.metal@bigmir.net>

# Configure my repo to use my custom Nginx with modsec
#ADD http://static.theroux.ca/repository/failshell.repo /etc/yum.repos.d/
RUN mkdir -p /usr/local/src
RUN cd /usr/local/src
RUN yum -y install wget vim htop tar

# install repo for centos
# epel repo
RUN rpm -Uvh http://dl.fedoraproject.org/pub/epel/7/x86_64/e/epel-release-7-5.noarch.rpm
# remi repo
RUN rpm -Uvh http://rpms.famillecollet.com/enterprise/remi-release-7.rpm
RUN yum repolist


# install nginx
RUN yum -y install nginx
#RUN yum check all

#install mysql
#RUN yum -y install mysql mysql-server

# setup mysql
#RUN sed -i -e"s/^bind-address\s*=\s*127.0.0.1/bind-address = 0.0.0.0/" /etc/my.cnf 
#RUN setenforce 0
#RUN /usr/bin/mysql & \
#    sleep 10s &&\
#    echo "GRANT ALL ON *.* TO admin@'%' IDENTIFIED BY 'admin-pass' WITH GRANT OPTION; FLUSH PRIVILEGES" | mysql -u root --password=secret &&\
#    echo "create database test" | mysql -u root --password=secret

#install PHP + modules
#RUN yum -y install php php-cli php-mysql php-gd php-imap php-ldap php-odbc php-pear php-xml php-xmlrpc php-mbstring php-mcrypt 

# tell Nginx to stay foregrounded
ADD nginx.conf /etc/nginx/nginx.conf
RUN echo "daemon off;" >> /etc/nginx/nginx.conf
RUN mkdir -p /var/www
RUN curl https://git.centos.org/sources/httpd/c7/acf5cccf4afaecf3afeb18c50ae59fd5c6504910 \
    | tar -xz -C /var/www \
    --strip-components=1
RUN sed -i -e 's/Apache/nginx/g' -e '/apache_pb.gif/d' \
/var/www/index.html

#RUN echo "<?php phpinfo(); ?>" > /var/www/php_info.php

# expose HTTP
EXPOSE 80
EXPOSE 8080
EXPOSE 443

# expose mysql
EXPOSE 3306

# Run
# Start nginx when container starts
#CMD service nginx start
#ENTRYPOINT /usr/sbin/nginx

#ENTRYPOINT /usr/bin/mysql
CMD [ "/usr/sbin/nginx" ]
#CMD ["nginx", "-g", "daemon off;"]
#CMD /usr/sbin/nginx -c /etc/nginx/nginx.conf
#CMD /usr/sbin/mysql -c /etc/mysql/my.cnf


