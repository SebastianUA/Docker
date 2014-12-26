FROM centos:centos7
MAINTAINER Vitaly Natarov <solo.metal@bigmir.net>

# Configure my repo to use my custom Nginx with modsec
RUN mkdir -p /usr/local/src && \
    cd /usr/local/src && \
    rpm -Uvh http://dev.mysql.com/get/mysql-community-release-el7-5.noarch.rpm && \
    yum -y install git mysql-community-server && \
    git clone https://github.com/SebastianUA/mysql-sys.git /tmp/mysql-sys

ADD mysql-init /usr/bin/mysql-init
RUN chmod +x /usr/bin/mysql-init && \
    /usr/bin/mysql-init

ADD mysql-start /usr/bin/mysql-start
RUN chmod +x /usr/bin/mysql-start
ADD my.cnf /etc/my.cnf

# expose mysql
EXPOSE 20 3306

# Run mysql in Docker conainer 
ENTRYPOINT ["/usr/bin/mysql-start"]
