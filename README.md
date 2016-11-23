![Microbadger badge](https://images.microbadger.com/badges/image/smartapps/bitbucket-pipelines-php-mysql:stretch.svg)

# bitbucket-pipelines-php-mysql

[Bitbucket Pipelines](https://bitbucket.org/product/features/pipelines) [Docker](https://www.docker.com/) image based on [Debian _Stretch_](https://www.debian.org/releases/stretch/) with [PHP](http://php.net/)/[MySQL](https://www.mysql.com) (and more !)

More help in Bitbucket's [Confluence](https://confluence.atlassian.com/bitbucket/bitbucket-pipelines-beta-792496469.html)

Docker image at [smartapps/bitbucket-pipelines-php-mysql](https://hub.docker.com/r/smartapps/bitbucket-pipelines-php-mysql/) (no `CMD` as it is overriden by *Pipelines*)

## Packages installed

 - `php7.0-apcu`, `php7.0-cli`, `php7.0-curl`, `php7.0-gd`, `php7.0-geoip`, `php-gettext`, `php7.0-imagick`, `php7.0-intl`, `php7.0-json`, `php7.0-mcrypt`, `php7.0-memcached`, `php7.0-mysql`, `php7.0-sqlite`, `php7.0-xdebug`, `php-xml`, `php-zip`, `memcached`, `imagemagick`, `openssh-client`, `curl`, `gettext`, `zip`, `git`
 - [Perl](https://www.perl.org/) 5.24
 - [Python](https://www.python.org/) 2.7 & 3.5
 - [MySQL](https://www.mysql.com/) 5.6 (user `root:root`)
 - [PHP](http://www.php.net/) 7.0
 - [Ruby](https://www.ruby-lang.org/) 2.3
 - [Node.js](https://nodejs.org/) 6.x LTS
 - Latest [Composer](https://getcomposer.org/), [Gulp](http://gulpjs.com/), [Webpack](https://webpack.github.io/), [Mocha](https://mochajs.org/), [Grunt](http://gruntjs.com/), [PHPUnit](https://phpunit.de/), [Codeception](https://codeception.com/)

## Sample `bitbucket-pipelines.yml`

```YAML
image: smartapps/bitbucket-pipelines-php-mysql:stretch
pipelines:
  default:
    - step:
        script:
          - service mysql start
          - mysql -h localhost --user=root --password=root -e "CREATE DATABASE test;"
          - composer config -g github-oauth.github.com XXXXXXXX
          - composer install --no-interaction --no-progress --prefer-dist
          - npm install --no-spin
          - gulp
```
