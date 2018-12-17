.PHONY: all centos-7.6.1810 ubuntu-16.04 ubuntu-18.04

ERL_VERSION=21.2

all: centos-7.6.1810 ubuntu-16.04 ubuntu-18.04

centos-7.6.1810:
	docker build --no-cache -t shiguredo/erlang:otp-${ERL_VERSION}-$@ -f centos/7.6.1810/Dockerfile .
	docker push shiguredo/erlang:otp-${ERL_VERSION}-$@

ubuntu-16.04:
	docker build --no-cache -t shiguredo/erlang:otp-${ERL_VERSION}-$@ -f ubuntu/16.04/Dockerfile .
	docker push shiguredo/erlang:otp-${ERL_VERSION}-$@

ubuntu-18.04:
	docker build --no-cache -t shiguredo/erlang:otp-${ERL_VERSION}-$@ -f ubuntu/18.04/Dockerfile .
	docker push shiguredo/erlang:otp-${ERL_VERSION}-$@
