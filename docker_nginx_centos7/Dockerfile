FROM centos:centos7
MAINTAINER Vitaly Natarov <solo.metal@bigmir.net>

# Configure my repo to use my custom Nginx with modsec
RUN mkdir -p /usr/local/src && \
    cd /usr/local/src && \
    yum -y install wget vim htop tar

# install repo for centos
# epel repo
RUN rpm -Uvh http://dl.fedoraproject.org/pub/epel/7/x86_64/e/epel-release-7-5.noarch.rpm && \
    rpm -Uvh http://rpms.famillecollet.com/enterprise/remi-release-7.rpm && \
    yum repolist && \
    yum -y install nginx
    
# tell Nginx to stay foregrounded
ADD nginx.conf /etc/nginx/nginx.conf
RUN echo "daemon off;" >> /etc/nginx/nginx.conf && \
    mkdir -p /var/www && \
    curl https://git.centos.org/sources/httpd/c7/acf5cccf4afaecf3afeb18c50ae59fd5c6504910 \
     | tar -xz -C /var/www \
     --strip-components=1 && \
   sed -i -e 's/Apache/nginx/g' -e '/apache_pb.gif/d' \
     /var/www/index.html

# expose HTTP
EXPOSE 80 8080 443
# Run
CMD [ "/usr/sbin/nginx" ]

