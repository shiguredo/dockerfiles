FROM centos:6.9

LABEL maintainer="v@shiguredo.jp"

ENV OTP_VERSION 20.3.3
ENV OPENSSL_VERSION 1.1.0h

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
  && git clone https://github.com/erlang/otp.git \
  && cd /usr/local/src/otp \
  && git checkout OTP-${OTP_VERSION} \
  && ./otp_build autoconf \
  && ./configure --prefix=/opt/erlang-${OTP_VERSION} \
                 --enable-kernel-poll \
                 --enable-hipe \
                 --enable-dirty-schedulers \
                 --enable-smp-support \
                 --enable-m64-build \
                 --enable-lock-counter \
                 --enable-sharing-preserving \
                 --enable-native-libs \
                 --with-ssl=/opt/openssl-${OPENSSL_VERSION} \
                 --without-javac \
                 --without-odbc \
                 --disable-sctp \
                 --disable-dynamic-ssl-lib \
                 --disable-vm-probes \
  && make \
  && make install \
  && cd .. \
  && rm -rf otp

ENV PATH /opt/erlang-${OTP_VERSION}/bin:$PATH

WORKDIR /
