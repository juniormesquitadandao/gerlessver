# Gerlessver

Managerless version with docker for Spring Boot.

## When is creating new project

```shell
cd project
  wget -nv https://raw.githubusercontent.com/juniormesquitadandao/gerlessver/master/spring_boot/Dockerfile
  wget -nv https://raw.githubusercontent.com/juniormesquitadandao/gerlessver/master/spring_boot/docker-compose.yml
  ARG_USER_UID=$(id -u) ARG_USER_GID=$(id -g) docker compose config
  ARG_USER_UID=$(id -u) ARG_USER_GID=$(id -g) docker compose build
  docker compose up -d
  docker compose exec app bash
    git init
    sdk install maven
    sdk install springboot
    spring init --dependencies=web
    unzip demo.zip
    rm demo.zip
    spring shell
      exit
    mvn spring-boot:run
    # Brower: http://localhost:8080
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
  wget -nv https://raw.githubusercontent.com/juniormesquitadandao/gerlessver/master/spring_boot/Dockerfile
  wget -nv https://raw.githubusercontent.com/juniormesquitadandao/gerlessver/master/spring_boot/docker-compose.yml
  ARG_USER_UID=$(id -u) ARG_USER_GID=$(id -g) docker compose config
  ARG_USER_UID=$(id -u) ARG_USER_GID=$(id -g) docker compose build
  docker compose up -d
  docker compose exec app bash
    mvn spring-boot:run
    # Brower: http://localhost:8080
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
  ARG_USER_UID=$(id -u) ARG_USER_GID=$(id -g) docker compose config
  ARG_USER_UID=$(id -u) ARG_USER_GID=$(id -g) docker compose build
  docker compose up -d
  docker compose exec app bash
    mvn spring-boot:run
    # Brower: http://localhost:8080
    # Press: CTRL+C
    git status
    git add .
    git commit -m 'upgrade'
    git push
    exit
  docker compose down
```

