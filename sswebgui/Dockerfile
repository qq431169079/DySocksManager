FROM ubuntu:16.04
LABEL com.damonyuan.ss-webgui.version="1.0.0" \
      vendor="Damon Yuan"
MAINTAINER Damon Yuan <yzmhit@gmail.com>

RUN apt-get update && \
    apt-get install tzdata net-tools curl git sudo software-properties-common python-pip iputils-ping -y && \
    pip install git+https://github.com/shadowsocks/shadowsocks.git@master && \
    add-apt-repository ppa:max-c-lv/shadowsocks-libev -y && \
    curl -sL https://deb.nodesource.com/setup_6.x | bash - && \
    apt-get install -y nodejs shadowsocks-libev && \
    npm i -g shadowsocks-manager && \
    echo "Asia/Shanghai" > /etc/timezone && \
    rm /etc/localtime && \
    dpkg-reconfigure -f noninteractive tzdata

COPY entrypoint.sh /entrypoint.sh

WORKDIR /root/.ssmgr/

COPY webgui.yml /root/.ssmgr/webgui.yml

WORKDIR /

EXPOSE 6003

ENTRYPOINT ["/entrypoint.sh"]