FROM centos:latest

ENV code_root /code
ENV httpd_conf ${code_root}/httpd.conf

# httpd
RUN yum install -y httpd

# php
RUN yum install -y http://rpms.famillecollet.com/enterprise/remi-release-7.rpm
RUN yum install -y --enablerepo=remi-php72 php php-cli php-gd php-mbstring php-mcrypt php-mysqlnd php-pdo php-xml
RUN sed -i -e "s|^;date.timezone =.*$|date.timezone = Asia/Tokyo|" /etc/php.ini

ADD . $code_root
RUN test -e $httpd_conf && echo "Include $httpd_conf" >> /etc/httpd/conf/httpd.conf

EXPOSE 80

CMD ["/usr/sbin/httpd", "-D", "FOREGROUND"]
