FROM centos:7.3.1611

MAINTAINER NAKAI Ryosuke <nakai@shiguredo.jp>

ENV OTP_VERSION 20.0.2
ENV OPENSSL_VERSION 1.1.0f

RUN yum -y update \
  && yum clean all \
  && yum -y install \
         git \
         gcc \
         autoconf \
         glibc-devel \
         make \
         ncurses-devel \
         perl \
         tar \
  && yum clean all

RUN curl -sSL "https://www.openssl.org/source/openssl-${OPENSSL_VERSION}.tar.gz" \
    | tar -v -C /usr/local/src -xz \
  && cd /usr/local/src/openssl-${OPENSSL_VERSION} \
  && ./config --prefix=/opt/openssl-${OPENSSL_VERSION} \
  && make \
  && make install \
  && cd .. \
  && rm -rf openssl-${OPENSSL_VERSION}

RUN cd /usr/local/src \
  && git clone -b OTP-${OTP_VERSION} https://github.com/erlang/otp.git \
  && cd /usr/local/src/otp \
  && ./otp_build autoconf \
  && ./configure --prefix=/opt/erlang-${OTP_VERSION} \
                 --enable-kernel-poll \
                 --enable-hipe \
                 --enable-dirty-schedulers \
                 --enable-smp-support \
                 --enable-m64-build \
                 --enable-sharing-preserving \
                 --without-wx \
                 --without-javac \
                 --disable-vm-probes \
                 --disable-megaco-flex-scanner-lineno \
                 --disable-megaco-reentrant-flex-scanner \
  && make \
  && make install \
  && cd .. \
  && rm -rf otp

ENV PATH /opt/erlang-${OTP_VERSION}/bin:$PATH

WORKDIR /
