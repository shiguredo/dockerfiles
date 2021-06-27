FROM arm64v8/ubuntu:20.04

LABEL maintainer="v@shiguredo.jp"

ENV OTP_VERSION 23.2.6

RUN apt-get update \
  && apt-get install -y \
         autoconf \
         git \
         build-essential \
         openssl \
         libssl-dev \
         curl \
         ncurses-dev \
  && apt-get clean \
  && rm -rf /var/cache/apt/archives/* /var/lib/apt/lists/*

RUN cd /usr/local/src \
  && git clone -b OTP-${OTP_VERSION} https://github.com/erlang/otp.git \
  && cd /usr/local/src/otp \
  && ./otp_build autoconf \
  && ./configure --prefix=/opt/erlang-${OTP_VERSION} \
                 --enable-kernel-poll \
                 --enable-dirty-schedulers \
                 --disable-sharing-preserving \
                 --disable-native-libs \
                 --disable-hipe \
                 --disable-sctp \
                 --disable-vm-probes \
                 --without-javac \
                 --without-odbc \
  && make -j \
  && make install \
  && cd .. \
  && rm -rf otp

ENV PATH /opt/erlang-${OTP_VERSION}/bin:$PATH

WORKDIR /
