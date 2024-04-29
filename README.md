<p align="center">
    <a href="https://github.com/yiisoft" target="_blank">
        <img src="https://avatars0.githubusercontent.com/u/993323" height="100px">
    </a>
    <h1 align="center">Yii 2 Advanced Project Template Using Docker</h1>
    <br>
</p>

Yii 2 Advanced Project Template is a skeleton [Yii 2](https://www.yiiframework.com/) application best for
developing complex Web applications with multiple tiers.

The template includes three tiers: front end, back end, and console, each of which
is a separate Yii application.

The template is designed to work in a team development environment. It supports
deploying the application in different environments.

> Note: This template, enhanced by Eduardo Raider, is optimized to run with friendly URLs when run on an Apache server within Docker.

### Installing using Docker

Install the application dependencies

    docker-compose run --rm backend composer install

Initialize the application by running the `init` command within a container

    docker-compose run --rm backend php /app/init

Adjust the components['db'] configuration in `common/config/main-local.php` accordingly.

        'dsn' => 'mysql:host=mysql;dbname=yii2advanced',
        'username' => 'yii2advanced',
        'password' => 'secret',

> Docker networking creates a DNS entry for the host `mysql` available from your `backend` and `frontend` containers.

> If you want to use another database, such a Postgres, uncomment the corresponding section in `docker-compose.yml` and update your database connection.

>         'dsn' => 'pgsql:host=pgsql;dbname=yii2advanced',

For more information about Docker setup please visit the [guide](https://www.yiiframework.com/doc-2.0/guide-index.html).

Start the application

    docker-compose up -d

Run the migrations

    docker-compose run --rm backend yii migrate          

Access it in your browser by opening

- frontend: http://127.0.0.1:80
- backend: http://127.0.0.1:8080

Documentation is at [docs/guide/README.md](docs/guide/README.md).

[![Latest Stable Version](https://img.shields.io/packagist/v/yiisoft/yii2-app-advanced.svg)](https://packagist.org/packages/yiisoft/yii2-app-advanced)
[![Total Downloads](https://img.shields.io/packagist/dt/yiisoft/yii2-app-advanced.svg)](https://packagist.org/packages/yiisoft/yii2-app-advanced)
[![build](https://github.com/yiisoft/yii2-app-advanced/workflows/build/badge.svg)](https://github.com/yiisoft/yii2-app-advanced/actions?query=workflow%3Abuild)

DIRECTORY STRUCTURE
-------------------

```
common
    config/              contains shared configurations
    mail/                contains view files for e-mails
    models/              contains model classes used in both backend and frontend
    tests/               contains tests for common classes    
console
    config/              contains console configurations
    controllers/         contains console controllers (commands)
    migrations/          contains database migrations
    models/              contains console-specific model classes
    runtime/             contains files generated during runtime
backend
    assets/              contains application assets such as JavaScript and CSS
    config/              contains backend configurations
    controllers/         contains Web controller classes
    models/              contains backend-specific model classes
    runtime/             contains files generated during runtime
    tests/               contains tests for backend application    
    views/               contains view files for the Web application
    web/                 contains the entry script and Web resources
frontend
    assets/              contains application assets such as JavaScript and CSS
    config/              contains frontend configurations
    controllers/         contains Web controller classes
    models/              contains frontend-specific model classes
    runtime/             contains files generated during runtime
    tests/               contains tests for frontend application
    views/               contains view files for the Web application
    web/                 contains the entry script and Web resources
    widgets/             contains frontend widgets
vendor/                  contains dependent 3rd-party packages
environments/            contains environment-based overrides
```
