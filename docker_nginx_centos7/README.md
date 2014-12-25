<b> dockerfiles-centos-nginx </b>

CentOS 7 dockerfile for nginx

To build:

Copy the sources down -
<i>
docker build -rm -t <username>/nginx:centos7 .
</i>
To run:
<i>
docker run -d -p 80:80 <username>/nginx:centos7
</i>
To test:
<i>
curl http://localhost
</i>
