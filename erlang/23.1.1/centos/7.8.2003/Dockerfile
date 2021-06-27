FROM centos:7.8.2003

LABEL maintainer="v@shiguredo.jp"

ENV OTP_VERSION 23.1.1
ENV OPENSSL_VERSION 1.1.1h

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
                 --enable-dirty-schedulers \
                 --disable-sharing-preserving \
                 --disable-native-libs \
                 --disable-hipe \
                 --disable-sctp \
                 --disable-dynamic-ssl-lib \
                 --disable-vm-probes \
                 --with-ssl=/opt/openssl-${OPENSSL_VERSION} \
                 --without-javac \
                 --without-odbc \
  && make \
  && make install \
  && cd .. \
  && rm -rf otp

ENV PATH /opt/erlang-${OTP_VERSION}/bin:$PATH

WORKDIR /
