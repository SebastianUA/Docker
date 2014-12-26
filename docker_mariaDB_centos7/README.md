# dockerfiles for MariaDB (mysql) on centos7



Please, see my Unix/Linux blog:
[Unix and Linux in examples](http://linux-notes.org)

It's russ version, but soon i'll have multi site on many languages

To build:

Copy the sources down -
```python
$ docker build -rm -t <username>/mysql:centos7 .
```
To run:
```python
$ docker run -d -p 3306:3306 <username>/mysql:centos7
``````
For test:
```python
$ mysql -uroot -pmysql -h your_server_IP -P your_listen_port_on_mysql
``````
Example:
```python
$ mysql -uroot -pmysql -h 192.168.103.198 -P 3307
``````

``````
Please, see my Unix/Linux blog:
[Unix and Linux in examples](http://linux-notes.org)

It's russ version, but soon i'll have multi site on many languages
