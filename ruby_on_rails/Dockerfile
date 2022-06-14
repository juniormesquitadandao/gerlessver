ARG ARG_RUBY_VERSION
FROM ruby:${ARG_RUBY_VERSION}-slim-buster

SHELL ["/bin/sh", "-c"]

RUN apt update && \
  apt upgrade -y && \
  apt install -y \
    sudo \
    locales-all \
    bash-completion \
    dh-autoreconf \
    cmake \
    git-core \
    curl \
    wget \
    zip \
    vim && \
  update-alternatives --config editor && \
  apt autoremove --purge && \
  apt autoclean

ARG ARG_LINUX_LOCALE
ENV LC_ALL=$ARG_LINUX_LOCALE LANG=$ARG_LINUX_LOCALE LANGUAGE=$ARG_LINUX_LOCALE

RUN getent passwd '1000' | cut -d: -f1 | { read username; [ -z "$username" ] && exit 0 || deluser --remove-home $username; } && \
  addgroup --gid '1000' user && \
  adduser --disabled-password --gecos '' --uid '1000' --gid '1000' user && \
  passwd -d root && \
  echo 'user ALL=(ALL:ALL) NOPASSWD:ALL' >> /etc/sudoers && \
  chown user:user -R /usr/local

USER user
WORKDIR /home/user

ARG ARG_NODE_VERSION
RUN wget -nv "https://nodejs.org/dist/v${ARG_NODE_VERSION}/node-v${ARG_NODE_VERSION}-linux-x64.tar.gz" && \
  tar -xf "node-v${ARG_NODE_VERSION}-linux-x64.tar.gz" --directory '/usr/local' --strip-components '1' && \
  rm -rf "node-v${ARG_NODE_VERSION}-linux-x64.tar.gz" && \
  npm install -g yarn

RUN sudo apt install -y libpq-dev

RUN locale && \
  ruby -v && \
  echo "node: `node -v`" && \
  echo "npm: `npm -v`" && \
  echo "yarn: `yarn -v`"
