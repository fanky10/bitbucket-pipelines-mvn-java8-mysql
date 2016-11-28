# bitbucket-pipelines-mvn-java8-mysql

[Bitbucket Pipelines](https://bitbucket.org/product/features/pipelines) [Docker](https://www.docker.com/) image based on [Debian _Jessie_](https://www.debian.org/releases/jessie/) with [JAVA](https://www.java.com/en/)/[MySQL](https://www.mysql.com) (and more !)

More help in Bitbucket's [Confluence](https://confluence.atlassian.com/bitbucket/bitbucket-pipelines-beta-792496469.html)

Docker image at [smartapps/bitbucket-pipelines-php-mysql](https://hub.docker.com/r/smartapps/bitbucket-pipelines-php-mysql/) (no `CMD` as it is overriden by *Pipelines*)

## Packages installed

 - `maven 3`, `java 8`,`openssh-client`, `curl`, `gettext`, `zip`, `git`
 - [MySQL](https://www.mysql.com/) 5.5 (user `root:root`)
 - [Java](https://www.java.com/) 8

## Sample `bitbucket-pipelines.yml`

```YAML
image: smartapps/bitbucket-pipelines-php-mysql
pipelines:
  default:
    - step:
        script:
          - service mysql start
          - mysql -h localhost --user=root --password=root -e "CREATE DATABASE test;"
          - mvn clean install test
```

## Debian _Stretch_

A Docker image based on [Debian _Stretch_](https://www.debian.org/releases/stretch/), PHP 7, MySQL 5.6, Node.js 6.x and Ruby 2.3 is available under `stretch` branch (and with Docker tag `stretch`).

## Changelog

### 0.1

 - Initial release
 - Maven 3, Java 8, MySQL
