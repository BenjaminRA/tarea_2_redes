FROM ubuntu

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update

RUN apt-get -y install build-essential automake autoconf libtool pkg-config intltool libcurl4-openssl-dev libglib2.0-dev libevent-dev libminiupnpc-dev libgtk-3-dev libappindicator3-dev libssl-dev 

WORKDIR /client

COPY . .

RUN tar xf transmission-3.00.tar.xz

WORKDIR /client/transmission-3.00

RUN chmod +x ./configure && ./configure -q && make -s

RUN make install

WORKDIR /transmission

ENV TRANSMISSION_HOME="/transmission/config"

RUN apt-get -y install tcpdump

CMD [ "transmission-daemon", "-f"]