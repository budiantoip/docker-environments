FROM ubuntu:18.04

RUN apt-get update && apt-get install -y software-properties-common
#reference : https://launchpad.net/~libreoffice/+archive/ubuntu/ppa
RUN add-apt-repository ppa:libreoffice/libreoffice-6-4
RUN apt-get update && apt-get install -y vim nano libreoffice libreoffice-writer

RUN mkdir -p /pdf

CMD exec /bin/bash -c "trap : TERM INT; sleep infinity & wait"