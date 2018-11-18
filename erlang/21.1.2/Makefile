.PHONY: all centos-6.9 centos-7.5.1804 ubuntu-14.04 ubuntu-16.04 ubuntu-18.04

ERL_VERSION=21.1.2

all: centos-6.9 centos-7.5.1804 ubuntu-14.04 ubuntu-16.04 ubuntu-18.04

centos-6.9:
	docker build --no-cache -t shiguredo/erlang:otp-${ERL_VERSION}-$@ -f centos/6.9/Dockerfile .
	docker push shiguredo/erlang:otp-${ERL_VERSION}-$@

centos-7.5.1804:
	docker build --no-cache -t shiguredo/erlang:otp-${ERL_VERSION}-$@ -f centos/7.5.1804/Dockerfile .
	docker push shiguredo/erlang:otp-${ERL_VERSION}-$@

ubuntu-14.04:
	docker build --no-cache -t shiguredo/erlang:otp-${ERL_VERSION}-$@ -f ubuntu/14.04/Dockerfile .
	docker push shiguredo/erlang:otp-${ERL_VERSION}-$@

ubuntu-16.04:
	docker build --no-cache -t shiguredo/erlang:otp-${ERL_VERSION}-$@ -f ubuntu/16.04/Dockerfile .
	docker push shiguredo/erlang:otp-${ERL_VERSION}-$@

ubuntu-18.04:
	docker build --no-cache -t shiguredo/erlang:otp-${ERL_VERSION}-$@ -f ubuntu/18.04/Dockerfile .
	docker push shiguredo/erlang:otp-${ERL_VERSION}-$@

