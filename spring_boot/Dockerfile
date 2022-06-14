ARG ARG_OPEN_JDK_VERSION
FROM openjdk:${ARG_OPEN_JDK_VERSION}-slim-buster

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

RUN curl -s 'https://get.sdkman.io' | bash

RUN locale && \
  java --version

