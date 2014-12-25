<b> dockerfiles-centos-nginx </b>

CentOS 7 dockerfile for nginx

To build:

Copy the sources down -
```python
docker build -rm -t <username>/nginx:centos7 .
```
To run:
```python
docker run -d -p 80:80 <username>/nginx:centos7
``````

To test:
```python
curl http://localhost
``````
