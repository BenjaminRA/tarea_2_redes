# FROM alpine

# RUN apk add --no-cache bash git perl uncrustify yarn cmake build-base make curl curl-dev automake autoconf libtool

# WORKDIR /client

# COPY . .

# RUN git submodule update --init \
#   && mkdir build \
#   && cd build \
#   && cmake .. \
#   && make \
#   && make install

FROM ubuntu

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update && apt-get -y install build-essential automake autoconf libtool pkg-config intltool libcurl4-openssl-dev libglib2.0-dev libevent-dev libminiupnpc-dev libgtk-3-dev libappindicator3-dev

WORKDIR /client

COPY . .

RUN apt-get -y install libssl-dev

RUN ./configure -q && make -s

RUN make install