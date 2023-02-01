# Gerlessver

Managerless version with docker for Flask.

## When is creating new project

```shell
cd project
  wget -nv https://raw.githubusercontent.com/juniormesquitadandao/gerlessver/master/flask/Dockerfile
  wget -nv https://raw.githubusercontent.com/juniormesquitadandao/gerlessver/master/flask/docker-compose.yml
  ARG_USER_UID=$(id -u) ARG_USER_GID=$(id -g) docker compose config
  ARG_USER_UID=$(id -u) ARG_USER_GID=$(id -g) docker compose build
  docker compose up -d
  docker compose exec app bash
    cat /etc/hosts | grep dockerhost

    git init
    pip install flask
    wget -nv https://raw.githubusercontent.com/Sysnove/flask-hello-world/master/hello.py --output-document app.py
    npm init
    flask run
    # Brower: http://localhost:5000
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
  wget -nv https://raw.githubusercontent.com/juniormesquitadandao/gerlessver/master/flask/Dockerfile
  wget -nv https://raw.githubusercontent.com/juniormesquitadandao/gerlessver/master/flask/docker-compose.yml
  ARG_USER_UID=$(id -u) ARG_USER_GID=$(id -g) docker compose config
  ARG_USER_UID=$(id -u) ARG_USER_GID=$(id -g) docker compose build
  docker compose up -d
  docker compose exec app bash
    cat /etc/hosts | grep dockerhost

    pip install -r requirements.txt
    npm install
    flask run
    # Brower: http://localhost:5000
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

    pip install -r requirements.txt
    npm install
    flask run
    # Brower: http://localhost:5000
    # Press: CTRL+C
    git status
    git add .
    git commit -m 'upgrade'
    git push
    exit
  docker compose down
```
