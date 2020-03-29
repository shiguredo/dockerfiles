.PHONY: all centos-7.7.1908 centos-8.1.1911 ubuntu-16.04 ubuntu-18.04 ubuntu-20.04

ERL_VERSION=23.0-rc2

all: centos-7.7.1908 centos-8.1.1911 ubuntu-16.04 ubuntu-18.04 ubuntu-20.04

centos-7.7.1908:
	cd centos/7.7.1908 && docker build --no-cache -t shiguredo/erlang:otp-${ERL_VERSION}-$@ .
	docker push shiguredo/erlang:otp-${ERL_VERSION}-$@

centos-8.1.1911:
	cd centos/8.1.1911 && docker build --no-cache -t shiguredo/erlang:otp-${ERL_VERSION}-$@ .
	docker push shiguredo/erlang:otp-${ERL_VERSION}-$@

ubuntu-16.04:
	cd ubuntu/16.04 && docker build --no-cache -t shiguredo/erlang:otp-${ERL_VERSION}-$@ .
	docker push shiguredo/erlang:otp-${ERL_VERSION}-$@

ubuntu-18.04:
	cd ubuntu/18.04 && docker build --no-cache -t shiguredo/erlang:otp-${ERL_VERSION}-$@ .
	docker push shiguredo/erlang:otp-${ERL_VERSION}-$@

ubuntu-20.04:
	cd ubuntu/20.04 && docker build --no-cache -t shiguredo/erlang:otp-${ERL_VERSION}-$@ .
	docker push shiguredo/erlang:otp-${ERL_VERSION}-$@

