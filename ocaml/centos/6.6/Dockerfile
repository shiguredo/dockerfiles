FROM centos:6.6

MAINTAINER NAKAI Ryosuke <nakai@shiguredo.jp>

ENV OCAML_VERSION 4.01.0
ENV OPAM_VERSION 1.2.1

RUN yum -y update; yum clean all
RUN yum -y install git tar gcc-c++ m4 bzip2 patch make unzip; yum clean all

RUN curl -sSL "http://caml.inria.fr/pub/distrib/ocaml-4.01/ocaml-4.01.0.tar.gz" \
    | tar -v -C /usr/local/src -xz
RUN cd /usr/local/src/ocaml-4.01.0 \
    && ./configure \
    && make world.opt \
    && make install

RUN curl -sSL "https://github.com/ocaml/opam/releases/download/1.2.1/opam-full-1.2.1.tar.gz" \
    | tar -v -C /usr/local/src -xz

RUN cd /usr/local/src/opam-full-1.2.1 \
    && ./configure \
    && make lib-ext \
    && make \
    && make install

RUN opam init
RUN opam install core -y
RUN opam install menhir -y
RUN opam install omake -y
RUN opam install ucorelib -y

ENV PATH /root/.opam/system/bin:$PATH

