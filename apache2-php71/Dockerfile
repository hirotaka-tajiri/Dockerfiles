# Apache2-php71
#
# VERSION               0.0.1

FROM centos

LABEL name="Apache2 with php-7.1 Image" \
    license="GPLv2" \
    build-date="20170216"

RUN yum -y upgrade
RUN yum -y install bzip2 xz bind-utils lsof wget epel-release
RUN rpm -ivh http://rpms.famillecollet.com/enterprise/remi-release-7.rpm
RUN yum -y install --enablerepo=remi-php71 php php-devel php-cli php-common php-json php-mysql php-mysqlnd php-opcache php-mbstring

VOLUME /var/www/html /var/log/httpd

COPY files/httpd.conf /etc/httpd/conf
COPY files/httpd-default.conf /etc/httpd/conf.d
COPY files/httpd-languages.conf /etc/httpd/conf.d
COPY files/httpd-mpm.conf /etc/httpd/conf.d
COPY files/php.ini /etc
COPY files/10-opcache.ini /etc/php.d

ENV PATH $PATH:/usr/local/bin:/usr/sbin
CMD ["/usr/sbin/httpd", "-DFOREGROUND"]
