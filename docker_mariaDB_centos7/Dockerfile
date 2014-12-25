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

#install mysql
RUN yum -y install mysql mysql-server




# expose mysql
EXPOSE 3306

# Run mysql in Docker conainer 
#ENTRYPOINT /usr/bin/mysql
CMD CMD ["/bin/bash", "/start.sh"]






