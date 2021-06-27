FROM ubuntu:16.04

MAINTAINER NAKAI Ryosuke <v@shiguredo.jp>

ENV OTP_VERSION 19.3

ADD sources.list /etc/apt/sources.list

RUN apt update \
  && apt install -y \
         build-essential \
         curl \
         libssl-dev \
         ncurses-dev \
  && apt clean \
  && rm -rf /var/cache/apt/archives/* /var/lib/apt/lists/*

RUN curl -sSL "http://erlang.shiguredo.jp/otp_src_${OTP_VERSION}.tar.gz" \
    | tar -v -C /usr/local/src -xz \
  && cd /usr/local/src/otp_src_${OTP_VERSION} \
  && ./configure --prefix=/opt/erlang-${OTP_VERSION} \
                 --enable-kernel-poll \
                 --enable-hipe \
                 --enable-dirty-schedulers \
                 --enable-smp-support \
                 --enable-m64-build \
                 --enable-sharing-preserving \
                 --without-javac \
                 --disable-vm-probes \
                 --disable-megaco-flex-scanner-lineno \
                 --disable-megaco-reentrant-flex-scanner \
  && make \
  && make install \
  && cd .. \
  && rm -rf otp_src_${OTP_VERSION}

ENV PATH /opt/erlang-${OTP_VERSION}/bin:$PATH

WORKDIR /
