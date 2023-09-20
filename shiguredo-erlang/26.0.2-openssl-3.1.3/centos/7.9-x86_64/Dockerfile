FROM centos:7.9.2009

LABEL maintainer="v@shiguredo.jp"

ENV OTP_VERSION 26.0.2
ENV OPENSSL_VERSION 3.1.3

RUN yum -y update \
  && yum clean all \
  && yum -y install \
         centos-release-scl \
  && yum clean all

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
         perl-IPC-Cmd \
         devtoolset-10 \
  && yum clean all

RUN bash -c "source scl_source enable devtoolset-10; \
  curl -sSL \"https://www.openssl.org/source/openssl-${OPENSSL_VERSION}.tar.gz\" \
    | tar -v -C /usr/local/src -xz \
  && cd /usr/local/src/openssl-${OPENSSL_VERSION} \
  && ./config --prefix=/opt/openssl-${OPENSSL_VERSION} no-shared no-module \
  && make -j \
  && make install_sw \
  && cd .. \
  && rm -rf openssl-${OPENSSL_VERSION} \
  "

RUN bash -c "source scl_source enable devtoolset-10; \
  git clone -b shiguredo https://github.com/shiguredo/otp /usr/local/src/otp_src_${OTP_VERSION} \
  && cd /usr/local/src/otp_src_${OTP_VERSION} \
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
  && rm -rf otp_src_${OTP_VERSION} \
  "


ENV PATH /opt/erlang-${OTP_VERSION}/bin:$PATH

WORKDIR /
