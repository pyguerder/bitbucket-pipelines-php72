# Bitbucket Pipelines PHP 7.1 image

[![](https://images.microbadger.com/badges/version/edbizarro/bitbucket-pipelines-php7.svg)](https://microbadger.com/images/edbizarro/bitbucket-pipelines-php7 "Get your own version badge on microbadger.com") [![](https://images.microbadger.com/badges/image/edbizarro/bitbucket-pipelines-php7.svg)](https://microbadger.com/images/edbizarro/bitbucket-pipelines-php7 "Get your own image badge on microbadger.com")

[![forthebadge](http://forthebadge.com/images/badges/fuck-it-ship-it.svg)](http://forthebadge.com)

## Based on Ubuntu 16.04

### Packages installed

- `php7.1-zip`, `php7.1-xml`, `php7.1-mbstring`, `php7.1-curl`, `php7.1-json`, `php7.1-imap`, `php7.1-mysql` and `php7.1-tokenizer`
- [Composer](https://getcomposer.org/)
- Mysql 5.7

### Sample `bitbucket-pipelines.yml`

```YAML
image: oktupol/bitbucket-pipelines-php71
pipelines:
  default:
    - step:
        script:
          - service mysql start
          - mysql -h localhost -u root -proot -e "CREATE DATABASE test;"
          - composer install --no-interaction --no-progress --prefer-dist
          - ./vendor/phpunit/phpunit/phpunit -v --coverage-text --colors=never --stderr
```
