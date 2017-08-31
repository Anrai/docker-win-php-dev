# MYSQL基础镜像
FROM hub.c.163.com/library/mysql:5.7.18
# 作者
MAINTAINER Anrai "anrai@huanglei.me"

ADD my.cnf /etc/mysql/conf.d/my.cnf

RUN usermod -u 1000 mysql && chown mysql.mysql /var/run/mysqld/

CMD ["mysqld"]

EXPOSE 3306