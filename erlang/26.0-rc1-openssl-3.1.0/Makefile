.PHONY: all centos-7.9-x86_64 rhel-7.9-x86_64 rhel-8.7-x86_64 rhel-9.1-x86_64 ubuntu-20.04-x86_64 ubuntu-22.04-x86_64

ERL_VERSION=26.0-rc1-openssl-3.1.0

all: x86_64 arm64

x86_64: centos-7.9-x86_64 rhel-8.7-x86_64 rhel-9.1.0-x86_64 ubuntu-20.04-x86_64 ubuntu-22.04-x86_64

arm64: ubuntu-20.04-arm64 ubuntu-22.04-arm64

centos-7.9-x86_64:
	cd centos/7.9-x86_64 && docker build --no-cache -t shiguredo/erlang:otp-${ERL_VERSION}-$@ .
	docker push shiguredo/erlang:otp-${ERL_VERSION}-$@

rhel-7.9-x86_64:
	cd rhel/7.9-x86_64 && docker build --no-cache -t shiguredo/erlang:otp-${ERL_VERSION}-$@ .
	docker push shiguredo/erlang:otp-${ERL_VERSION}-$@

rhel-8.7-x86_64:
	cd rhel/8.7-x86_64 && docker build --no-cache -t shiguredo/erlang:otp-${ERL_VERSION}-$@ .
	docker push shiguredo/erlang:otp-${ERL_VERSION}-$@

rhel-9.1-x86_64:
	cd rhel/9.1-x86_64 && docker build --no-cache -t shiguredo/erlang:otp-${ERL_VERSION}-$@ .
	docker push shiguredo/erlang:otp-${ERL_VERSION}-$@

ubuntu-20.04-x86_64:
	cd ubuntu/20.04-x86_64 && docker build --no-cache -t shiguredo/erlang:otp-${ERL_VERSION}-$@ .
	docker push shiguredo/erlang:otp-${ERL_VERSION}-$@

ubuntu-22.04-x86_64:
	cd ubuntu/22.04-x86_64 && docker build --no-cache -t shiguredo/erlang:otp-${ERL_VERSION}-$@ .
	docker push shiguredo/erlang:otp-${ERL_VERSION}-$@

ubuntu-20.04-arm64:
	cd ubuntu/20.04-arm64 && docker build --no-cache -t shiguredo/erlang:otp-${ERL_VERSION}-$@ .
	docker push shiguredo/erlang:${ERL_VERSION}-$@

ubuntu-22.04-arm64:
	cd ubuntu/22.04-arm64 && docker build --no-cache -t shiguredo/erlang:otp-${ERL_VERSION}-$@ .
	docker push shiguredo/erlang:${ERL_VERSION}-$@

ubuntu-multi-arch:
	docker manifest create shiguredo/erlang:${ERL_VERSION}-$@-ubuntu-22.04 \
		shiguredo/erlang:${ERL_VERSION}-$@-ubuntu-22.04-x86_64 \
		shiguredo/erlang:${ERL_VERSION}-$@-ubuntu-22.04-arm64v8
	docker manifest push shiguredo/erlang:${ERL_VERSION}-$@-ubuntu-22.04