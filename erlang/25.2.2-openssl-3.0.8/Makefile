.PHONY: all centos-7.9.2009 rhel-7.9 rhel-8.7 rhel-9.1.0 ubuntu-18.04 ubuntu-20.04 ubuntu-22.04

ERL_VERSION=25.2.2-openssl-3.0.8

all: centos-7.9.2009 rhel-8.7 rhel-9.1.0 ubuntu-18.04 ubuntu-20.04 ubuntu-22.04

centos-7.9.2009:
	cd centos/7.9.2009 && docker build --no-cache -t shiguredo/erlang:otp-${ERL_VERSION}-$@ .
	docker push shiguredo/erlang:otp-${ERL_VERSION}-$@

rhel-7.9:
	cd rhel/7.9 && docker build --no-cache -t shiguredo/erlang:otp-${ERL_VERSION}-$@ .
	docker push shiguredo/erlang:otp-${ERL_VERSION}-$@

rhel-8.7:
	cd rhel/8.7 && docker build --no-cache -t shiguredo/erlang:otp-${ERL_VERSION}-$@ .
	docker push shiguredo/erlang:otp-${ERL_VERSION}-$@

rhel-9.1.0:
	cd rhel/9.1.0 && docker build --no-cache -t shiguredo/erlang:otp-${ERL_VERSION}-$@ .
	docker push shiguredo/erlang:otp-${ERL_VERSION}-$@

ubuntu-18.04:
	cd ubuntu/18.04 && docker build --no-cache -t shiguredo/erlang:otp-${ERL_VERSION}-$@ .
	docker push shiguredo/erlang:otp-${ERL_VERSION}-$@

ubuntu-20.04:
	cd ubuntu/20.04 && docker build --no-cache -t shiguredo/erlang:otp-${ERL_VERSION}-$@ .
	docker push shiguredo/erlang:otp-${ERL_VERSION}-$@

ubuntu-22.04:
	cd ubuntu/22.04 && docker build --no-cache -t shiguredo/erlang:otp-${ERL_VERSION}-$@ .
	docker push shiguredo/erlang:otp-${ERL_VERSION}-$@
