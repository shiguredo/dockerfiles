FROM ubuntu:14.04

MAINTAINER NAKAI Ryosuke <nakai@shiguredo.jp>

ENV OCAML_VERSION 4.03.0
ENV OPAM_VERSION 1.2.2

ADD sources.list /etc/apt/sources.list

RUN apt-get update
RUN apt-get upgrade -y
RUN apt-get install build-essential git unzip bzip2 tar curl m4 -y
RUN apt-get clean && rm -rf /var/cache/apt/archives/* /var/lib/apt/lists/*

RUN curl -sSL "http://caml.inria.fr/pub/distrib/ocaml-4.03/ocaml-4.03.0.tar.gz" \
    | tar -v -C /usr/local/src -xz
RUN cd /usr/local/src/ocaml-4.03.0 \
    && ./configure \
    && make world.opt \
    && make install

RUN curl -sSL "https://github.com/ocaml/opam/releases/download/${OPAM_VERSION}/opam-full-${OPAM_VERSION}.tar.gz" \
    | tar -v -C /usr/local/src -xz

RUN cd /usr/local/src/opam-full-1.2.2 \
    && ./configure \
    && make lib-ext \
    && make \
    && make install

RUN opam init
RUN opam install core.113.33.02+4.03 -y
RUN opam install menhir.20160504 -y
RUN opam install omake.0.9.8.6-0.rc1 -y
RUN opam install ucorelib.0.0.2 -y

ENV PATH /root/.opam/system/bin:$PATH
