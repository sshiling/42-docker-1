FROM debian:latest

RUN apt update
RUN apt install git -y
RUN apt install golang -y 
RUN apt install sqlite3 -y

ENV USER=root GOPATH=/

WORKDIR src/github.com/gogits
RUN git clone --depth=1 -b develop https://github.com/gogits/gogs 
RUN go get -u -tags sqlite github.com/gogits/gogs

WORKDIR gogs
RUN go build -tags sqlite
EXPOSE 3000
ENTRYPOINT ./gogs web
