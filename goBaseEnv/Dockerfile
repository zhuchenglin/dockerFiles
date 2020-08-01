FROM centos

MAINTAINER zhuchenglin01

#RUN yum install -y gcc
#RUN yum install -y wget
#RUN yum install -y go 1.10.1

VOLUME /tmp
VOLUME /usr
VOLUME /root

#RUN wget https://dl.google.com/go/go1.10.linux-amd64.tar.gz
#COPY ./docker/images/goInstall/* /tmp
ADD ./images/* /usr/local
#RUN gzip -d /tmp/go1.10.linux-amd64.tar.gz
#RUN tar zxvf /tmp/go1.10.linux-amd64.tar.gz -C /usr/local

# config GOPATH
RUN yum -y install vim &&\
 mkdir -p /root/gopath &&\
 mkdir -p /root/gopath/src &&\
 mkdir -p /root/gopath/pkg &&\
 mkdir -p /root/gopath/bin &&\
 mkdir -p /usr/lib/golang &&\
 mkdir -p /root/gopath/src/server


ENV GOPATH /root/gopath
ENV GOROOT /usr/local/go
ENV PATH=$PATH:$GOPATH:$GOPATH/bin:/usr/local/go/bin

# copy source files

COPY src /root/gopath/src/server/


# build the server
WORKDIR /root/gopath/src/server
#RUN go build -o server.bin main.go
RUN go run main.go
# startup the server
#CMD /root/gopath/src/server/server.bin