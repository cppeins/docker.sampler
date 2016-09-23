# docker.sampler
========================


소개
----
1. haproxy
2. php7


사용
---
1. haproxy
   이미지 받기
    ```
    $ docker pull dayreiner/centos7-haproxy-1.6
    ```
   이미지 생성
    ```
    $ cd images.haproxy
    $ docker build -t haproxy:default .
    ```
   이미지 리스팅
    ```
    $ docker images
    ```
   이미지 실행
    ```
    $ docker run -d -p {External Port}:{Internal Port} haproxy:default
    ```
    ```
    $ docker run -i -t haproxy:default /bin/bash
    ```

2. php7


문제해결
----
   * docker error
      * [Docker: An error occurred trying to connect](http://stackoverflow.com/questions/35071536/docker-an-error-occurred-trying-to-connect)
      windows command prompt:
      ```
      $ docker-machine start default            // create new one
      $ docker-machine ls                       // show you your machine running
      $ docker-machine env --shell cmd default  // you'll see something like
         SET DOCKER_TLS_VERIFY=1
         SET DOCKER_HOST=tcp://192.168.99.100:2376
         SET DOCKER_CERT_PATH=C:\Users\Arseny\.docker\machine\machines\default
         SET DOCKER_MACHINE_NAME=default
         REM Run this command to configure your shell:
         REM     @FOR /f "tokens=*" %i IN ('docker-machine env --shell cmd default') DO @%i
      $ @FOR /f "tokens=*" %i IN ('docker-machine env --shell cmd default') DO @%i
      ```
   * haproxy install
      [A Recipe for a haproxy 1.6.4 stable version RPM on CentOS](https://github.com/ITV/rpm-haproxy)


참고자료
----
* docker
   * [Docker - Build, Ship, and Run Any App, Anywhere](https://www.docker.com/)
   * [도커(Docker) 튜토리얼 : 깐 김에 배포까지](http://blog.nacyot.com/articles/2014-01-27-easy-deploy-with-docker/)
   * [도커 무작정 따라하기: 도커가 처음인 사람도 60분이면 웹 서버를 올릴 수 있습니다!](http://www.slideshare.net/pyrasis/docker-fordummies-44424016)
   * [도커(Docker) 튜토리얼 : 깐 김에 배포까지](http://blog.nacyot.com/articles/2014-01-27-easy-deploy-with-docker/)
   * [Docker 기본 사용법](http://pyrasis.com/Docker/Docker-HOWTO)
* haproxy   
   * [dayreiner/centos7-haproxy-1.6](https://hub.docker.com/r/dayreiner/centos7-haproxy-1.6/)
   * [A Recipe for a haproxy 1.6.4 stable version RPM on CentOS](https://github.com/ITV/rpm-haproxy)
   * [The complete guide to HTTP/2 with HAProxy and Nginx](http://m12.io/blog/http-2-with-haproxy-and-nginx-guide)
