FROM centos:centos7
MAINTAINER Vitaly Natarov <solo.metal@bigmir.net>

# Configure my repo to use my custom Nginx with modsec
RUN mkdir -p /usr/local/src
RUN cd /usr/local/src
#RUN yum -y install wget vim htop tar

# install repo for centos
# epel repo
#RUN rpm -Uvh http://dl.fedoraproject.org/pub/epel/7/x86_64/e/epel-release-7-5.noarch.rpm
# remi repo
#RUN rpm -Uvh http://rpms.famillecollet.com/enterprise/remi-release-7.rpm
#RUN yum repolist


#install MariaDB (mysql)
#RUN yum -y update; yum clean all
RUN rpm -Uvh http://dev.mysql.com/get/mysql-community-release-el7-5.noarch.rpm
RUN yum -y install git mysql-community-server

# setup MariaDB (mysql)
RUN git clone https://github.com/SebastianUA/mysql-sys.git /tmp/mysql-sys
ADD mysql-init /usr/bin/mysql-init
RUN chmod +x /usr/bin/mysql-init
RUN /usr/bin/mysql-init

ADD mysql-start /usr/bin/mysql-start
RUN chmod +x /usr/bin/mysql-start
ADD my.cnf /etc/my.cnf

# delete repos
RUN rm -rf /usr/local/src/epel-release-7-5.noarch.rpm
RUN rm -rf /usr/local/src/remi-release-7.rpm

# expose mysql
EXPOSE 20 3306

# Run mysql in Docker conainer 
ENTRYPOINT ["/usr/bin/mysql-start"]

