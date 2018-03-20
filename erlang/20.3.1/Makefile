.PHONY: all centos-6.9 centos-7.4.1708 ubuntu-14.04 ubuntu-16.04

ERL_VERSION=20.2.4

all: centos-6.9 centos-7.4.1708 ubuntu-14.04 ubuntu-16.04

centos-6.9:
	docker build --no-cache -t shiguredo/erlang:otp-${ERL_VERSION}-$@ -f centos/6.9/Dockerfile .
	docker push shiguredo/erlang:otp-${ERL_VERSION}-$@

centos-7.4.1708:
	docker build --no-cache -t shiguredo/erlang:otp-${ERL_VERSION}-$@ -f centos/7.4.1708/Dockerfile .
	docker push shiguredo/erlang:otp-${ERL_VERSION}-$@

ubuntu-14.04:
	docker build --no-cache -t shiguredo/erlang:otp-${ERL_VERSION}-$@ -f ubuntu/14.04/Dockerfile .
	docker push shiguredo/erlang:otp-${ERL_VERSION}-$@

ubuntu-16.04:
	docker build --no-cache -t shiguredo/erlang:otp-${ERL_VERSION}-$@ -f ubuntu/16.04/Dockerfile .
	docker push shiguredo/erlang:otp-${ERL_VERSION}-$@
