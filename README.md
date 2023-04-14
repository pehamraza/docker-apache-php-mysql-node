# Docker setup for Apache, PHP, MySQL & Node dev environment

#### Published on Docker Hub at https://hub.docker.com/repository/docker/peham/apache2-mysql8-php-nod
## How to use

### 1. Build docker image from dockerfile

 ```
docker build -t peham/apache2-mysql8-php-node:1.0 .
 ```

### 2. Use the image in docker-compose.yml to build the dev environment

 ```
 web:
image: peham/apache2-mysql8-php-node:1.0
volumes:
    - '/Users/peham/Projects/RS/PR:/app'
    - './.docker-config/php.ini:/etc/php/php.ini'

# Uncomment the following line to override the SSL dir
#   - './.docker-config/ssl:/etc/ssl/docker'

# Uncomment the following line to enable xdebug
#   - './.docker-config/php-xdebug-phpstorm.ini:/etc/php/xdebug-settings.ini'
    
    environment:
        PHP_VERSION: '7.2'
        COMPOSER_ALLOW_XDEBUG: '1'
        PHP_IDE_CONFIG: 'serverName=docker-php-apache'
        TERM: '$TERM'
    ports:
        - '80:80'
        - '443:443'
 ```

## Environment Variables:
 You can change the environment variables to change the PHP version to install.
 See variables,
 
- PHP_VERSION
- COMPOSER_ALLOW_XDEBUG
- PHP_IDE_CONFIG
- TERM

## Other configurations

- You can also modify ``php.ini`` to be included in your dev environment
- You can modify ``vhost.conf`` to your Virtual Host configuration