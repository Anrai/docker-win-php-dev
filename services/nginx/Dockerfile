# NGINX基础镜像
FROM hub.c.163.com/library/nginx:1.13.0
# 作者
MAINTAINER Anrai "anrai@huanglei.me"

ADD nginx.conf /etc/nginx/
ADD sites/*.conf /etc/nginx/conf.d/

RUN mkdir /home/www
RUN chown -R www-data.www-data /home/www

RUN  cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime

CMD ["nginx"]

EXPOSE 80 443