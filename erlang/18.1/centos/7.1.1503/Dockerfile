FROM centos:7.1.1503

MAINTAINER Seizan Shimazaki <shimazaki@shiguredo.jp>

ENV OTP_VERSION 18.1

RUN yum -y update; yum clean all
RUN yum -y install tar perl gcc glibc-devel make ncurses-devel openssl-devel; yum clean all

RUN curl -sSL "http://www.erlang.org/download/otp_src_${OTP_VERSION}.tar.gz" \
    | tar -v -C /usr/local/src -xz

RUN cd /usr/local/src/otp_src_${OTP_VERSION} \
    && ./configure --prefix=/opt/erlang-${OTP_VERSION} \
                   --enable-kernel-poll \
                   --enable-hipe \
                   --enable-dirty-schedulers \
                   --enable-smp-support \
                   --enable-m64-build \
                   --without-javac \
                   --disable-vm-probes \
                   --disable-megaco-flex-scanner-lineno \
                   --disable-megaco-reentrant-flex-scanner \
    && make; make install

ENV PATH /opt/erlang-${OTP_VERSION}/bin:$PATH
