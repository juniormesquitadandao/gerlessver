# Gerlessver

Managerless version with docker for Ruby on Rails.

## When is creating new project

```shell
cd project
  wget -nv https://raw.githubusercontent.com/juniormesquitadandao/gerlessver/master/ruby_on_rails/Dockerfile
  wget -nv https://raw.githubusercontent.com/juniormesquitadandao/gerlessver/master/ruby_on_rails/docker-compose.yml
  ARG_USER_UID=$(id -u) ARG_USER_GID=$(id -g) docker compose config
  ARG_USER_UID=$(id -u) ARG_USER_GID=$(id -g) docker compose build
  docker compose up -d
  docker compose exec app bash
    cat /etc/hosts | grep dockerhost
    echo > /dev/tcp/dockerhost/5432 && echo "Postgresql is running"
    echo > /dev/tcp/dockerhost/6379 && echo "Redis is running"

    git init
    gem install rails
    rails new --database postgresql --skip-bundle .
    bundle add redis
    npm init

    # Set host: dockerhost in file config/database.yml
    rails db:create
    RAILS_ENV=test rails db:create
    rails c
      Redis.new.keys
      exit
    rails s
    # Brower: http://localhost:3000
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
  wget -nv https://raw.githubusercontent.com/juniormesquitadandao/gerlessver/master/ruby_on_rails/Dockerfile
  wget -nv https://raw.githubusercontent.com/juniormesquitadandao/gerlessver/master/ruby_on_rails/docker-compose.yml
  ARG_USER_UID=$(id -u) ARG_USER_GID=$(id -g) docker compose config
  ARG_USER_UID=$(id -u) ARG_USER_GID=$(id -g) docker compose build
  docker compose up -d
  docker compose exec app bash
    cat /etc/hosts | grep dockerhost
    echo > /dev/tcp/dockerhost/5432 && echo "Postgresql is running"
    echo > /dev/tcp/dockerhost/6379 && echo "Redis is running"

    bundle
    npm install

    # Set host: dockerhost in file config/database.yml
    rails db:create
    RAILS_ENV=test rails db:create
    rails c
      Redis.new.keys
      exit
    rails s
    # Brower: http://localhost:3000
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
    echo > /dev/tcp/dockerhost/5432 && echo "Postgresql is running"
    echo > /dev/tcp/dockerhost/6379 && echo "Redis is running"

    bundle
    npm install
    rails db:create
    RAILS_ENV=test rails db:create
    rails c
      Redis.new.keys
      exit
    rails s
    # Brower: http://localhost:3000
    # Press: CTRL+C
    git status
    git add .
    git commit -m 'upgrade'
    git push
    exit
  docker compose down
```
