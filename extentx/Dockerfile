FROM ubuntu:14.04
MAINTAINER liuyuan <liuyuan@xiaoshoyi.com>

RUN echo 'deb http://mirrors.163.com/ubuntu/ trusty main restricted universe multiverse' > /etc/apt/sources.list && \
    echo 'deb http://mirrors.163.com/ubuntu/ trusty-updates main restricted universe multiverse' >> /etc/apt/sources.list

RUN sudo apt-get -qqy update && \
    sudo apt-get -y install g++ && \ 
    sudo apt-get -y install make && \
    sudo apt-get -y install python

COPY dep/node-v6.11.0.tar.gz /tmp/

RUN cd /tmp/ && \
    tar zxvf node-v6.11.0.tar.gz && \
    cd node-v6.11.0 && \
    ./configure && \
    make && \
    make install

RUN sudo npm install -g cnpm --registry=https://registry.npm.taobao.org && \
    sudo cnpm install sails -g

RUN mkdir -p /opt/extentx

COPY proj/extentx /opt/extentx

RUN cd /opt/extentx/ && \
    sudo cnpm install

WORKDIR /opt/extentx

EXPOSE 1337

CMD ["sails", "lift"]
