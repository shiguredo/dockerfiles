FROM centos:7.2.1511

MAINTAINER NAKAI Ryosuke <nakai@shiguredo.jp>

ENV OTP_VERSION 18.2.1

RUN yum -y update \
  && yum clean all \
  && yum -y install \
         git \
         gcc \
         autoconf \
         glibc-devel \
         make \
         ncurses-devel \
         openssl-devel \
         perl \
         tar \
  && yum clean all

RUN cd /usr/local/src \
  && git clone -b shiguredo-otp-${OTP_VERSION} https://github.com/shiguredo/otp.git \
  && cd /usr/local/src/otp \
  && ./otp_build autoconf \
  && ./configure --prefix=/opt/shiguredo-otp-${OTP_VERSION} \
                 --enable-kernel-poll \
                 --enable-hipe \
                 --enable-dirty-schedulers \
                 --enable-smp-support \
                 --enable-m64-build \
                 --without-javac \
                 --disable-vm-probes \
                 --disable-megaco-flex-scanner-lineno \
                 --disable-megaco-reentrant-flex-scanner \
  && make \
  && make install \
  && cd .. \
  && rm -rf otp

ENV PATH /opt/shiguredo-otp-${OTP_VERSION}/bin:$PATH

WORKDIR /
