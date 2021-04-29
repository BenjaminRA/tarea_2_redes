FROM ubuntu

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update && apt-get -y install build-essential automake autoconf libtool pkg-config intltool libcurl4-openssl-dev libglib2.0-dev libevent-dev libminiupnpc-dev libgtk-3-dev libappindicator3-dev

WORKDIR /client

COPY . .

RUN apt-get -y install libssl-dev

RUN chmod +x ./configure && ./configure -q && make -s

RUN make install

WORKDIR /transmission

ENV TRANSMISSION_HOME="/transmission/config"

CMD [ "transmission-daemon", "-f"]