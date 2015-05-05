FROM ubuntu:14.04

MAINTAINER NAKAI Ryosuke <nakai@shiguredo.jp>

ENV OCAML_VERSION 4.01.0
ENV OPAM_VERSION 1.2.1

ADD sources.list /etc/apt/sources.list

RUN apt-get update
RUN apt-get upgrade -y
RUN apt-get install build-essential git unzip bzip2 tar curl m4 -y
RUN apt-get clean && rm -rf /var/cache/apt/archives/* /var/lib/apt/lists/*

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
