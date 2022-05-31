# GerlessVer

Managerless version with docker for Phoenix.

## When is creating new project

```shell
cd project
  wget -nv https://raw.githubusercontent.com/juniormesquitadandao/gerless_ver/master/phoenix/Dockerfile
  wget -nv https://raw.githubusercontent.com/juniormesquitadandao/gerless_ver/master/phoenix/docker-compose.yml
  docker compose config
  docker compose build
  docker compose up -d
  docker compose exec app bash
    git init
    mix archive.install --force hex phx_new
    mix phx.new --database=postgres --no-install .
    ls config/* | while read file; do sed -i 's/username: "postgres"/username: System.get_env("DATABASE_USERNAME")/g' $file; done
    ls config/* | while read file; do sed -i 's/password: "postgres"/password: System.get_env("DATABASE_PASSWORD")/g' $file; done
    ls config/* | while read file; do sed -i 's/hostname: "localhost",/hostname: System.get_env("DATABASE_HOST"),\n  port: System.get_env("DATABASE_PORT"),/g' $file; done
    sed -i 's/ip: {127, 0, 0, 1}, port: 4000/ip: System.get_env("IP") |> String.split(".") |> Enum.map(\&String.to_integer\/1) |> List.to_tuple, port: System.get_env("PORT")/g' config/dev.exs
    mix deps.get
    mix deps.compile
    mix ecto.create
    npm init
    mix test
    iex -S mix
    mix phx.server
    # Brower: http://localhost:4000
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
  wget -nv https://raw.githubusercontent.com/juniormesquitadandao/gerless_ver/master/phoenix/Dockerfile
  wget -nv https://raw.githubusercontent.com/juniormesquitadandao/gerless_ver/master/phoenix/docker-compose.yml
  docker compose config
  docker compose build
  docker compose up -d
  docker compose exec app bash
    mix deps.get
    mix deps.compile
    mix ecto.create
    npm install
    mix test
    iex -S mix
    mix phx.server
    # Brower: http://localhost:4000
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
  docker compose config
  docker compose build
  docker compose up -d
  docker compose exec app bash
    mix deps.get
    mix deps.compile
    mix ecto.create
    npm install
    mix test
    iex -S mix
    mix phx.server
    # Brower: http://localhost:4000
    # Press: CTRL+C
    git status
    git add .
    git commit -m 'upgrade'
    git push
    exit
  docker compose down
```
