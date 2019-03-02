.PHONY: all centos-7.6.1810 ubuntu-16.04 ubuntu-18.04

ERL_VERSION=22.0-rc1

all: centos-7.6.1810 ubuntu-16.04 ubuntu-18.04

centos-7.6.1810:
	cd centos/7.6.1810 && docker build --no-cache -t shiguredo/erlang:otp-${ERL_VERSION}-$@ .
	docker push shiguredo/erlang:otp-${ERL_VERSION}-$@

ubuntu-16.04:
	cd ubuntu/16.04 && docker build --no-cache -t shiguredo/erlang:otp-${ERL_VERSION}-$@ .
	docker push shiguredo/erlang:otp-${ERL_VERSION}-$@

ubuntu-18.04:
	cd ubuntu/18.04 && docker build --no-cache -t shiguredo/erlang:otp-${ERL_VERSION}-$@ .
	docker push shiguredo/erlang:otp-${ERL_VERSION}-$@
