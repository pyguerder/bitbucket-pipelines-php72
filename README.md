# Bitbucket Pipelines PHP 7.1 image

[![](https://images.microbadger.com/badges/version/pyguerder/bitbucket-pipelines-php71.svg)](https://microbadger.com/images/pyguerder/bitbucket-pipelines-php71 "Get your own version badge on microbadger.com") [![](https://images.microbadger.com/badges/image/pyguerder/bitbucket-pipelines-php71.svg)](https://microbadger.com/images/pyguerder/bitbucket-pipelines-php71 "Get your own image badge on microbadger.com")

## Based on Ubuntu 16.04

### Packages installed

- `php7.1-zip`, `php7.1-xml`, `php7.1-mbstring`, `php7.1-curl`, `php7.1-json`, `php7.1-imap`, `php7.1-mysql` and `php7.1-tokenizer`
- [Composer](https://getcomposer.org/)
- Mysql 5.7

### Sample `bitbucket-pipelines.yml`

```YAML
image: pyguerder/bitbucket-pipelines-php71
pipelines:
  default:
    - step:
        script:
          - service mysql start
          - mysql -h localhost -u root -proot -e "CREATE DATABASE test;"
          - composer install --no-interaction --no-progress --prefer-dist
          - ./vendor/phpunit/phpunit/phpunit -v --coverage-text --colors=never --stderr
```
