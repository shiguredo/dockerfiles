FROM centos:6.9

MAINTAINER NAKAI Ryosuke <v@shiguredo.jp>

ENV OTP_VERSION 20.0

RUN yum -y update \
  && yum clean all \
  && yum -y install \
         gcc \
         glibc-devel \
         make \
         ncurses-devel \
         openssl-devel \
         perl \
         tar \
  && yum clean all

RUN curl -sSL "http://erlang.shiguredo.jp/otp_src_${OTP_VERSION}.tar.gz" \
    | tar -v -C /usr/local/src -xz

RUN cd /usr/local/src/otp_src_${OTP_VERSION} \
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
