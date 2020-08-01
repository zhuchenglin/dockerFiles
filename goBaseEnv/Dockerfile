FROM centos

MAINTAINER zhuchenglin01

RUN yum -y install vim && yum -y install wget &&\
 mkdir -p /root/gopath &&\
 mkdir -p /root/gopath/src &&\
 mkdir -p /root/gopath/pkg &&\
 mkdir -p /root/gopath/bin &&\
 mkdir -p /usr/lib/golang &&\
 mkdir -p /usr/local &&\
 mkdir -p /root/gopath/src/server &&\
 wget https://dl.google.com/go/go1.10.linux-amd64.tar.gz &&\
 tar -C /usr/local -xzf go1.10.linux-amd64.tar.gz

ENV GOPATH /root/gopath
ENV GOROOT /usr/local/go
ENV PATH=$PATH:$GOPATH:$GOPATH/bin:/usr/local/go/bin

COPY src /root/gopath/src/server/

WORKDIR /root/gopath/src/server

RUN go run main.go
