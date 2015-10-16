FROM ubuntu:14.04

# As reference: https://gist.github.com/hilios/6dfb40bf6b716ac97619

# Install libwebsockets
RUN apt-get update && apt-get install -y \
         build-essential \
         cmake \
         libssl-dev \
         rpm \
         wget \
  && apt-get clean \
  && rm -rf /var/cache/apt/archives/* /var/lib/apt/lists/*

RUN wget http://git.warmcat.com/cgi-bin/cgit/libwebsockets/snapshot/libwebsockets-1.4-chrome43-firefox-36.tar.gz \
  && tar -xzvf libwebsockets-1.4-chrome43-firefox-36.tar.gz \
  && cd libwebsockets-1.4-chrome43-firefox-36 \
  && mkdir build \
  && cd build \
  && cmake .. \
  && make \
  && make install \
  && cd ../.. \
  && rm -rf libwebsockets-1.4-chrome43-firefox-36.tar.gz libwebsockets-1.4-chrome43-firefox-36


# Install Mosquitto
RUN apt-get update && apt-get install -y \
         docbook-xsl \
         libc-ares-dev \
         uuid-dev \
         xsltproc \
  && apt-get clean \
  && rm -rf /var/cache/apt/archives/* /var/lib/apt/lists/*

RUN cd / \
  && wget http://mosquitto.org/files/source/mosquitto-1.4.4.tar.gz \
  && tar -zxvf mosquitto-1.4.4.tar.gz \
  && cd mosquitto-1.4.4 \
  && sed -i -e s/WITH_WEBSOCKETS:=no/WITH_WEBSOCKETS:=yes/ config.mk \
  && make \
  && make install \
  && cd .. \
  && rm -rf mosquitto-1.4.4.tar.gz mosquitto-1.4.4


RUN useradd -r -m -d /var/lib/mosquitto -s /usr/sbin/nologin -g nogroup mosquitto
CMD ["/usr/local/sbin/mosquitto", "-c", "/mosquitto/mosquitto.conf"]
