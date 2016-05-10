FROM centos:6.7

MAINTAINER NAKAI Ryosuke <nakai@shiguredo.jp>

ENV OCAML_VERSION 4.02.3
ENV OPAM_VERSION 1.2.2

RUN yum -y update; yum clean all
RUN yum -y install git tar gcc-c++ m4 bzip2 patch make unzip ncurses-devel; yum clean all

RUN curl -sSL "http://caml.inria.fr/pub/distrib/ocaml-4.01/ocaml-4.01.0.tar.gz" \
    | tar -v -C /usr/local/src -xz
RUN cd /usr/local/src/ocaml-${OCAML_VERSION} \
    && ./configure \
    && make world.opt \
    && make install

RUN curl -sSL "https://github.com/ocaml/opam/releases/download/${OPAM_VERSION}/opam-full-${OPAM_VERSION}.tar.gz" \
    | tar -v -C /usr/local/src -xz

RUN cd /usr/local/src/opam-full-${OPAM_VERSION} \
    && ./configure \
    && make lib-ext \
    && make \
    && make install

RUN opam init
RUN opam install core.111.13.00 -y
RUN opam install menhir.20151112 -y
RUN opam install omake.0.9.8.6-0.rc1 -y
RUN opam install ucorelib.0.0.2 -y

ENV PATH /root/.opam/system/bin:$PATH
