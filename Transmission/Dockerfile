FROM alpine

RUN apk add --no-cache bash git perl uncrustify yarn cmake build-base make curl curl-dev automake autoconf libtool

WORKDIR /client

COPY . .

RUN git submodule update --init \
  && mkdir build \
  && cd build \
  && cmake .. \
  && make \
  && make install