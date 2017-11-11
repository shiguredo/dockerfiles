.PHONY: all centos6.9 centos-7.4.1708 ubuntu14.04 ubuntu16.04

ERL_VERSION=20.1.5

all: centos6.9 centos-7.4.1708 ubuntu14.04 ubuntu16.04

centos6.9:
	docker build --no-cache -t shiguredo/erlang:erlang-${ERL_VERSION}-$@ -f centos/6.9/Dockerfile .
	docker push shiguredo/erlang:erlang-${ERL_VERSION}-$@

centos-7.4.1708:
	docker build --no-cache -t shiguredo/erlang:erlang-${ERL_VERSION}-$@ -f centos/7.4.1708/Dockerfile .
	docker push shiguredo/erlang:erlang-${ERL_VERSION}-$@

ubuntu14.04:
	docker build --no-cache -t shiguredo/erlang:erlang-${ERL_VERSION}-$@ -f ubuntu/14.04/Dockerfile .
	docker push shiguredo/erlang:erlang-${ERL_VERSION}-$@

ubuntu16.04:
	docker build --no-cache -t shiguredo/erlang:erlang-${ERL_VERSION}-$@ -f ubuntu/16.04/Dockerfile .
	docker push shiguredo/erlang:erlang-${ERL_VERSION}-$@
