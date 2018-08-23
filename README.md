# Docker-php-apache
> How to Setup a PHP environment using docker apache and php

## Getting Started
As part of the docker build process once apache and php is installed:
1. we will create a phpinfo page (index.php), which we will use to verify the PHP environment settings.
2. update php.ini to set sys_temp_dir to “/tmp/whateverfolderyouspecify”
3. update php.ini to enable and set php error_log file

## Prerequisites
Linux: Install docker:
1. yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
2. yum install docker-ce
3. clone the repository

## Installation / Build the app
1. docker build -t phpinfo .

  Explanation of the Dockerfile:
  
  1. FROM php:7.2-apache (Pull docker image from docker hub using image name/tag php:7.2-apache).
  2. COPY php.ini /usr/local/etc/php/ (Copy updated php.ini file to /usr/local/etc/php/).
  3. COPY index.php /var/www/html/ (Copy index.php to apache docroot so phpinfo() function is displayed.

## Run the container
1. docker run -d -p 80:80 phpinfo
2. For additional webservers run the same command as above but change the host port to 8080, 81, etc.
    1. docker run -d -p 8080:80 phpinfo
    2. docker run -d -p 81:80 phpinfo

## Verifying the container and website is up:
1. curl http://localhost on the host where you ran the container
2. Open a browser to http://ec2-52-71-64-160.compute-1.amazonaws.com/ (this is temporary and will be removed shortly).
