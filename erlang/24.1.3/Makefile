.PHONY: all centos-7.9.2009 cenhos-8.3.2011 rhel-7.9 rhel-8.4 rocky-8.4 ubuntu-18.04 ubuntu-20.04

ERL_VERSION=24.1.3

all: centos-7.9.2009 centos-8.3.2011 rhel-7.9 rhel-8.4 rocky-8.4 ubuntu-18.04 ubuntu-20.04

centos-7.9.2009:
	cd centos/7.9.2009 && docker build --no-cache -t shiguredo/erlang:otp-${ERL_VERSION}-$@ .
	docker push shiguredo/erlang:otp-${ERL_VERSION}-$@

centos-8.3.2011:
	cd centos/8.3.2011 && docker build --no-cache -t shiguredo/erlang:otp-${ERL_VERSION}-$@ .
	docker push shiguredo/erlang:otp-${ERL_VERSION}-$@

rhel-7.9:
	cd rhel/7.9 && docker build --no-cache -t shiguredo/erlang:otp-${ERL_VERSION}-$@ .
	docker push shiguredo/erlang:otp-${ERL_VERSION}-$@

rhel-8.4:
	cd rhel/8.4 && docker build --no-cache -t shiguredo/erlang:otp-${ERL_VERSION}-$@ .
	docker push shiguredo/erlang:otp-${ERL_VERSION}-$@

rocky-8.4:
	cd rocky/8.4 && docker build --no-cache -t shiguredo/erlang:otp-${ERL_VERSION}-$@ .
	docker push shiguredo/erlang:otp-${ERL_VERSION}-$@

ubuntu-18.04:
	cd ubuntu/18.04 && docker build --no-cache -t shiguredo/erlang:otp-${ERL_VERSION}-$@ .
	docker push shiguredo/erlang:otp-${ERL_VERSION}-$@

ubuntu-20.04:
	cd ubuntu/20.04 && docker build --no-cache -t shiguredo/erlang:otp-${ERL_VERSION}-$@ .
	docker push shiguredo/erlang:otp-${ERL_VERSION}-$@
