ARG ARG_NODE_VERSION
FROM --platform=linux/amd64 node:${ARG_NODE_VERSION}-buster-slim

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

ARG ARG_USER_UID ARG_USER_GID
RUN getent passwd $ARG_USER_UID | cut -d: -f1 | { read username; [ -z "$username" ] && exit 0 || deluser --remove-home $username; } && \
  getent group $ARG_USER_GID | cut -d: -f1 | { read groupname; [ -z "$groupname" ] && exit 0 || delgroup --remove-home $groupname; } && \
  addgroup --gid $ARG_USER_GID user && \
  adduser --disabled-password --gecos '' --uid  $ARG_USER_UID --gid $ARG_USER_GID user && \
  passwd -d root && \
  echo 'user ALL=(ALL:ALL) NOPASSWD:ALL' >> /etc/sudoers && \
  chown user:user -R /usr/local
USER user
WORKDIR /home/user

RUN sudo apt install -y python3

RUN locale && \
  echo "node: `node -v`"
