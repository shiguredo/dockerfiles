.PHONY: all centos-7.7.1908 centos-8.0.1905 ubuntu-16.04 ubuntu-18.04

ERL_VERSION=22.1.7

all: centos-7.7.1908 centos-8.0.1905 ubuntu-16.04 ubuntu-18.04

centos-7.7.1908:
	cd centos/7.7.1908 && docker build --no-cache -t shiguredo/erlang:otp-${ERL_VERSION}-$@ .
	docker push shiguredo/erlang:otp-${ERL_VERSION}-$@

centos-8.0.1905:
	cd centos/8.0.1905 && docker build --no-cache -t shiguredo/erlang:otp-${ERL_VERSION}-$@ .
	docker push shiguredo/erlang:otp-${ERL_VERSION}-$@

ubuntu-16.04:
	cd ubuntu/16.04 && docker build --no-cache -t shiguredo/erlang:otp-${ERL_VERSION}-$@ .
	docker push shiguredo/erlang:otp-${ERL_VERSION}-$@

ubuntu-18.04:
	cd ubuntu/18.04 && docker build --no-cache -t shiguredo/erlang:otp-${ERL_VERSION}-$@ .
	docker push shiguredo/erlang:otp-${ERL_VERSION}-$@
