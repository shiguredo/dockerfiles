FROM ubuntu:14.04

MAINTAINER Seizan Shimazaki <shimazaki@shiguredo.jp>

ENV OTP_VERSION 18.1

ADD sources.list /etc/apt/sources.list

RUN apt-get update
RUN apt-get upgrade -y
RUN apt-get install curl libssl-dev ncurses-dev build-essential -y
RUN apt-get clean && rm -rf /var/cache/apt/archives/* /var/lib/apt/lists/*

RUN curl -sSL "http://www.erlang.org/download/otp_src_${OTP_VERSION}.tar.gz" \
    | tar -v -C /usr/local/src -xz

WORKDIR /usr/local/src/otp_src_${OTP_VERSION}

RUN ./configure --prefix=/opt/erlang-${OTP_VERSION} \
                --enable-kernel-poll \
                --enable-hipe \
                --enable-dirty-schedulers \
                --enable-smp-support \
                --enable-m64-build \
                --without-javac \
                --disable-vm-probes \
                --disable-megaco-flex-scanner-lineno \
                --disable-megaco-reentrant-flex-scanner
RUN make
RUN make install

ENV PATH /opt/erlang-${OTP_VERSION}/bin:$PATH

WORKDIR /
