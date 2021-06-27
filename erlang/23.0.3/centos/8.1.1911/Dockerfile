FROM centos:8.1.1911

LABEL maintainer="v@shiguredo.jp"

ENV OTP_VERSION 23.0.3
ENV OPENSSL_VERSION 1.1.1g

RUN dnf -y update \
  && dnf clean all \
  && dnf -y install \
         git \
         gcc \
         autoconf \
         glibc-devel \
         make \
         ncurses-devel \
         perl \
         tar \
  && dnf clean all

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
                 --enable-smp-support \
                 --disable-sharing-preserving \
                 --enable-native-libs \
                 --with-ssl=/opt/openssl-${OPENSSL_VERSION} \
                 --without-javac \
                 --without-odbc \
                 --disable-hipe \
                 --disable-sctp \
                 --disable-dynamic-ssl-lib \
                 --disable-vm-probes \
  && make \
  && make install \
  && cd .. \
  && rm -rf otp

ENV PATH /opt/erlang-${OTP_VERSION}/bin:$PATH

WORKDIR /
