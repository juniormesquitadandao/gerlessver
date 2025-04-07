# Gerlessver

![Architecture](https://raw.githubusercontent.com/juniormesquitadandao/gerlessver/master/architecture.png)

Managerless version with docker.

## Configure host

### Mac
- Install Docker Desktop: https://docs.docker.com/desktop/install/mac-install
- Install Rosetta: https://support.apple.com/en-us/102527

### Linux
- Uninstall docker engine: https://docs.docker.com/engine/install/ubuntu/#uninstall-docker-engine
- Install docker engine (without run hello world): https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository
- Config docker as a non-root user ((with run hello world)): https://docs.docker.com/engine/install/linux-postinstall/#manage-docker-as-a-non-root-user
- Config docker to start on boot: https://docs.docker.com/engine/install/linux-postinstall/#configure-docker-to-start-on-boot

### All
- Install git: https://git-scm.com/book/en/v2/Getting-Started-Installing-Git
- Config git global: https://git-scm.com/book/en/v2/Customizing-Git-Git-Configuration
- Config ssh: https://git-scm.com/book/en/v2/Git-on-the-Server-Generating-Your-SSH-Public-Key
- Install any code editor ou IDE: https://www.sublimetext.com/docs/linux_repositories.html#apt
- Run: docker version
- Run: docker compose version
- Run: git version
- Run: git config --global --add safe.directory "*"
- Run: uname -m
- Run: DOCKER_DEFAULT_PLATFORM=linux/amd64 docker run --rm -t i386/ubuntu uname -m
- Run: DOCKER_DEFAULT_PLATFORM=linux/arm64 docker run --rm -t arm64v8/ubuntu uname -m

### Git Muilt Accounts
Update: ~/.ssh/config
```sh
Host 01.github.com
  HostName github.com
  User git
  IdentityFile ~/.ssh/github_01_rsa

Host 02.github.com
  HostName github.com
  User git
  IdentityFile ~/.ssh/github_02_rsa

Host 01.bitbucket.org
  HostName bitbucket.org
  User git
  IdentityFile ~/.ssh/bitbucket_01_rsa

Host 02.bitbucket.org
  HostName bitbucket.org
  User git
  IdentityFile ~/.ssh/bitbucket_02_rsa

Host 01.gitlab.com
  HostName gitlab.com
  User git
  IdentityFile ~/.ssh/gitlab_01_rsa

Host 02.gitlab.com
  HostName gitlab.com
  User git
  IdentityFile ~/.ssh/gitlab_02_rsa
```

Clone:
```sh
git clone git@01.github.com:name/project.git
git clone git@02.github.com:name/project.git
git clone git@01.bitbucket.org:name/project.git
git clone git@02.bitbucket.org:name/project.git
git clone git@01.gitlab.com:name/project.git
git clone git@02.gitlab.com:name/project.git
```

## Backend frameworks

- Ruby on Rails: https://github.com/juniormesquitadandao/gerlessver/tree/master/ruby_on_rails
- Nest JS: https://github.com/juniormesquitadandao/gerlessver/tree/master/nest_js
- Spring Boot: https://github.com/juniormesquitadandao/gerlessver/tree/master/spring_boot
- Laravel: https://github.com/juniormesquitadandao/gerlessver/tree/master/laravel
- Flask: https://github.com/juniormesquitadandao/gerlessver/tree/master/flask
- Phoenix: https://github.com/juniormesquitadandao/gerlessver/tree/master/phoenix
- ASP.NET: https://github.com/juniormesquitadandao/gerlessver/tree/master/aspnet

## Frontend frameworks

- Nuxt JS: https://github.com/juniormesquitadandao/gerlessver/tree/master/nuxt_js
- Next JS: https://github.com/juniormesquitadandao/gerlessver/tree/master/next_js
