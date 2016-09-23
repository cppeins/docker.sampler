FROM centos:7
MAINTAINER cppis <cppis@daum.net>

RUN yum update -y && \
    yum install -y epel-release && \
    yum install -y wget &&\
    wget http://rpms.famillecollet.com/enterprise/remi-release-7.rpm &&\
    rpm -Uvh remi-release-7.rpm

RUN yum install -y rpmdevtools pcre-devel
RUN yum install -y
#EXPOSE 80 443 9000
