# Gerlessver

Managerless version with docker for Laravel.

## When is creating new project

```shell
cd project
  wget -nv https://raw.githubusercontent.com/juniormesquitadandao/gerlessver/master/laravel/Dockerfile
  wget -nv https://raw.githubusercontent.com/juniormesquitadandao/gerlessver/master/laravel/docker-compose.yml
  ARG_USER_UID=$(id -u) ARG_USER_GID=$(id -g) docker compose config
  ARG_USER_UID=$(id -u) ARG_USER_GID=$(id -g) docker compose build
  docker compose up -d
  docker compose exec app bash
    cat /etc/hosts | grep dockerhost

    git init
    composer global require laravel/installer
    laravel new $(basename $PWD)
    mv $(basename $PWD)/* .
    mv $(basename $PWD)/.[^.]* .
    rm -rf $(basename $PWD)
    composer install
    npm init
    php artisan test
    php artisan serve
    # Brower: http://localhost:8000
    # Press: CTRL+C
    git status
    git add .
    git commit -m 'create'
    git push
    exit
  docker compose down
```

## When is updating current project

```shell
git clone ...
cd project
  wget -nv https://raw.githubusercontent.com/juniormesquitadandao/gerlessver/master/laravel/Dockerfile
  wget -nv https://raw.githubusercontent.com/juniormesquitadandao/gerlessver/master/laravel/docker-compose.yml
  ARG_USER_UID=$(id -u) ARG_USER_GID=$(id -g) docker compose config
  ARG_USER_UID=$(id -u) ARG_USER_GID=$(id -g) docker compose build
  docker compose up -d
  docker compose exec app bash
    cat /etc/hosts | grep dockerhost

    composer install
    npm install
    php artisan test
    php artisan serve
    # Brower: http://localhost:8000
    # Press: CTRL+C
    git status
    git add .
    git commit -m 'update'
    git push
    exit
  docker compose down
```

## When is upgrading versions

```shell
cd project
  # Change "app.build.args" in current docker-compose.yml
  # Change versions in current project
  docker volume rm project_app_local
  docker volume rm project_postgresql_data
  ARG_USER_UID=$(id -u) ARG_USER_GID=$(id -g) docker compose config
  ARG_USER_UID=$(id -u) ARG_USER_GID=$(id -g) docker compose build
  docker compose up -d
  docker compose exec app bash
    cat /etc/hosts | grep dockerhost

    composer install
    npm install
    php artisan test
    php artisan serve
    # Brower: http://localhost:8000
    # Press: CTRL+C
    git status
    git add .
    git commit -m 'upgrade'
    git push
    exit
  docker compose down
```
