FROM arm64v8/ubuntu:18.04

LABEL maintainer="v@shiguredo.jp"

ENV OTP_VERSION 23.0.3

RUN apt-get update \
  && apt-get install -y \
         autoconf \
         git \
         build-essential \
         curl \
         openssl \
         libssl-dev \
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
                 --enable-smp-support \
                 --disable-sharing-preserving \
                 --enable-native-libs \
                 --without-javac \
                 --without-odbc \
                 --disable-hipe \
                 --disable-sctp \
                 --disable-vm-probes \
  && make -j \
  && make install \
  && cd .. \
  && rm -rf otp_src_${OTP_VERSION}

ENV PATH /opt/erlang-${OTP_VERSION}/bin:$PATH

WORKDIR /
