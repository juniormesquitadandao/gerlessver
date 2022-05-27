# GerlessVer

Managerless version with docker for Nuxt JS.

## When is creating new project

```shell
cd project
  wget -nv https://raw.githubusercontent.com/juniormesquitadandao/gerless_ver/master/nuxt_js/Dockerfile
  wget -nv https://raw.githubusercontent.com/juniormesquitadandao/gerless_ver/master/nuxt_js/docker-compose.yml
  docker compose config
  docker compose build
  docker compose up -d
  docker compose exec app bash
    npm init nuxt-app $(basename $PWD) -y
    mv $(basename $PWD)/* .
    mv $(basename $PWD)/.[^.]* .
    rm -rf $(basename $PWD)
    npm install
    npm run test
    npm run dev
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
  wget -nv https://raw.githubusercontent.com/juniormesquitadandao/gerless_ver/master/nuxt_js/Dockerfile
  wget -nv https://raw.githubusercontent.com/juniormesquitadandao/gerless_ver/master/nuxt_js/docker-compose.yml
  docker compose config
  docker compose build
  docker compose up -d
  docker compose exec app bash
    npm install
    npm run test
    npm run dev
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
  docker compose config
  docker compose build
  docker compose up -d
  docker compose exec app bash
    npm install
    npm run test
    npm run dev
    # Brower: http://localhost:3000
    # Press: CTRL+C
    git status
    git add .
    git commit -m 'upgrade'
    git push
    exit
  docker compose down
```
