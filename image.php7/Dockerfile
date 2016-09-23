FROM centos:7
MAINTAINER cppis <cppis@daum.net>

RUN yum update -y && \
    yum install -y epel-release && \
    yum install -y wget &&\
    wget http://rpms.famillecollet.com/enterprise/remi-release-7.rpm &&\
    rpm -Uvh remi-release-7.rpm

RUN yum install -y nginx git
RUN yum --enablerepo=remi install -y \
        php70 php70-php php70-php-cli php70-php-common \
        php70-php-devel php70-php-pear php70-php-xdebug \
        php70-php-pdo php70-php-opcache php70-php-fpm \
        php70-php-mbstring php70-php-xml php70-php-pecl-apcu \
        php70-php-mysqlnd

RUN wget https://phar.phpunit.de/phpunit.phar && \
    chmod +x phpunit.phar && \
    mv phpunit.phar /usr/local/bin/phpunit

RUN ln -sf /usr/bin/php70 /usr/bin/php && \
    php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" && \
    php -r "if (hash_file('SHA384', 'composer-setup.php') === 'e115a8dc7871f15d853148a7fbac7da27d6c0030b848d9b3dc09e2a0388afed865e6a3d6b3c0fad45c48e2b5fc1196ae') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;" && \
    php composer-setup.php && \
    php -r "unlink('composer-setup.php');" && \
    mv composer.phar /usr/local/bin/composer

#ADD ./conf/cp-server.conf /etc/nginx/conf.d/cp-server.conf

RUN echo "xdebug.remote_enable=1" >> /etc/opt/remi/php70/php.d/15-xdebug.ini && \
    echo "xdebug.remote_autostart=1" >> /etc/opt/remi/php70/php.d/15-xdebug.ini && \
    echo "xdebug.remote_connect_back=1" >> /etc/opt/remi/php70/php.d/15-xdebug.ini && \
    echo "xdebug.profiler_enable=0" >> /etc/opt/remi/php70/php.d/15-xdebug.ini

RUN yum install -y python-pip && \
    pip install supervisor

#ADD ./conf/supervisord.conf /etc/supervisord.conf

#ADD ./sh/exec-php.sh /usr/bin/exec-php.sh

#RUN chmod +755 /usr/bin/exec-php.sh

#ENV PHP_IDE_CONFIG "serverName=ControlPointServer"


CMD ["/usr/bin/supervisord"]

EXPOSE 80 443 9000
