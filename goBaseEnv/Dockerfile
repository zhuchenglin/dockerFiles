FROM centos

MAINTAINER zhuchenglin01

RUN yum -y install vim && yum -y install wget &&\
 yum -y install openssh-server && mkdir /var/run/sshd && ssh-keygen -t rsa -f /etc/ssh/ssh_host_rsa_key &&\
 ssh-keygen -t dsa -f /etc/ssh/ssh_host_dsa_key &&\
 /bin/echo 'root:123456'|chpasswd && /bin/sed -i 's/.session.required.pam_loginuid.so./session optional pam_loginuid.so/g' /etc/pam.d/sshd &&\
 /bin/echo -e "LANG="en_US.UTF-8"" > /etc/default/local &&\
 mkdir -p /root/gopath &&\
 mkdir -p /root/gopath/src &&\
 mkdir -p /root/gopath/pkg &&\
 mkdir -p /root/gopath/bin &&\
 mkdir -p /usr/lib/golang &&\
 mkdir -p /usr/local &&\
 mkdir -p /root/gopath/src/server &&\
 wget https://dl.google.com/go/go1.12.7.linux-amd64.tar.gz &&\
 tar -C /usr/local -xzf go1.12.7.linux-amd64.tar.gz

ENV GOPATH /root/gopath
ENV GOROOT /usr/local/go
ENV PATH=$PATH:$GOPATH:$GOPATH/bin:/usr/local/go/bin

COPY src /root/gopath/src/server/

WORKDIR /root/gopath/src/server

EXPOSE 22

CMD /usr/sbin/sshd -D && go run main.go