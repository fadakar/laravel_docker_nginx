# run laravel in docker

### with nginx php mysql

## to run following the commands:

```console
    docker-compose up -d
```

```console
    docker-compose exec php bash
    cp .env.example .env
    composer install
    php artisan key:generate
```
