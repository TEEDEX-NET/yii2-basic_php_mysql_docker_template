## Yii 2 Basic project template 
[![codecov](https://codecov.io/gh/TEEDEX-NET/yii2-basic_php_mysql_docker_template/branch/master/graph/badge.svg?token=7ZNVHFGSBD)](https://codecov.io/gh/TEEDEX-NET/yii2-basic_php_mysql_docker_template)
[![Latest Release](https://img.shields.io/github/v/release/TEEDEX-NET/yii2-basic_php_mysql_docker_template)](https://github.com/TEEDEX-NET/yii2-basic_php_mysql_docker_template/releases/latest)
[![Latest build](https://img.shields.io/github/workflow/status/TEEDEX-NET/yii2-basic_php_mysql_docker_template/PHP%20workflow%20for%20Pushes)](https://github.com/TEEDEX-NET/yii2-basic_php_mysql_docker_template/actions/workflows/on_push.yml)

# Features
- Yii 2
- PHP 8
- MySQL 8
- PHP Code Sniffer
- Codeception
- Docker

# Local run
Note: First you should configure .env file in root directory (use .env.example as an example)

Then run command in root directory:
```
docker-compose -f dev/docker/docker-compose.yml --env-file=.env up
```

# Linter
Linters based on Yii 2 standards.

To lint code you should execute next command from root directory (inside container):
```
./vendor/bin/phpcs .
```

# Tests
Project's tests based on Yii 2 tests. 

To run tests you should execute next command from root directory (inside container): 
```
./vendor/bin/codecept run
```

# Docker
There are 3 containers:

## PHPMyAdmin 5.1.0
To manage MySQL database you can use phpmyadmin web-interface, available by next uri: `localhost:$PMA_PORT`, where $PMA_PORT is a variable from environment file

## MySQL 8.0.25
Application database service. There is no database exists, you should create your own.

# Application
Contains application source files and PHP 8.0.6 to serve it. 
