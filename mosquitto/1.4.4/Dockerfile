FROM ubuntu:14.04

RUN apt-get update
RUN apt-get upgrade -y
# Install libwebsockets
RUN apt-get install -y wget cmake build-essential rpm libssl-dev
RUN wget http://git.warmcat.com/cgi-bin/cgit/libwebsockets/snapshot/libwebsockets-1.4-chrome43-firefox-36.tar.gz
RUN tar -xzvf libwebsockets-1.4-chrome43-firefox-36.tar.gz
WORKDIR libwebsockets-1.4-chrome43-firefox-36
RUN mkdir build
WORKDIR build
RUN cmake ..
RUN make
RUN make install

# Install Mosquitto
RUN apt-get install -y libc-ares-dev uuid-dev xsltproc docbook-xsl
RUN apt-get clean && rm -rf /var/cache/apt/archives/* /var/lib/apt/lists/*
WORKDIR /
RUN wget http://mosquitto.org/files/source/mosquitto-1.4.4.tar.gz
RUN tar -zxvf mosquitto-1.4.4.tar.gz
WORKDIR mosquitto-1.4.4
RUN sed -i -e s/WITH_WEBSOCKETS:=no/WITH_WEBSOCKETS:=yes/ config.mk
RUN make
RUN make install
RUN useradd -r -m -d /var/lib/mosquitto -s /usr/sbin/nologin -g nogroup mosquitto
CMD ["/usr/local/sbin/mosquitto", "-c", "/mosquitto/mosquitto.conf"]
