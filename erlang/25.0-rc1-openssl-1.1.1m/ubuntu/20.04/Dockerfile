FROM ubuntu:20.04

LABEL maintainer="v@shiguredo.jp"

ENV OTP_VERSION 25.0-rc1
ENV OPENSSL_VERSION 1.1.1m

ADD sources.list /etc/apt/sources.list

RUN apt-get update \
  && apt-get install -y \
         autoconf \
         git \
         build-essential \
         curl \
         ncurses-dev \
  && apt-get clean \
  && rm -rf /var/cache/apt/archives/* /var/lib/apt/lists/*

RUN curl -sSL "https://www.openssl.org/source/openssl-${OPENSSL_VERSION}.tar.gz" \
    | tar -v -C /usr/local/src -xz \
  && cd /usr/local/src/openssl-${OPENSSL_VERSION} \
  && ./config --prefix=/opt/openssl-${OPENSSL_VERSION} \
  && make \
  && make install_sw \
  && cd .. \
  && rm -rf openssl-${OPENSSL_VERSION}

RUN cd /usr/local/src \
  && git clone -b OTP-${OTP_VERSION} https://github.com/erlang/otp.git \
  && cd /usr/local/src/otp \
  && ./configure --prefix=/opt/erlang-${OTP_VERSION} \
                 --enable-kernel-poll \
                 --enable-dirty-schedulers \
                 --enable-jit \
                 --disable-sharing-preserving \
                 --disable-sctp \
                 --disable-dynamic-ssl-lib \
                 --disable-vm-probes \
                 --with-ssl=/opt/openssl-${OPENSSL_VERSION} \
                 --without-javac \
                 --without-odbc \
  && make -j \
  && make install \
  && cd .. \
  && rm -rf otp

ENV PATH /opt/erlang-${OTP_VERSION}/bin:$PATH

WORKDIR /
