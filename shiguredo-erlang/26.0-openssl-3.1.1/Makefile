.PHONY: all centos-7.9-x86_64 rhel-8.8-x86_64 rhel-9.2-x86_64 ubuntu-20.04-x86_64 ubuntu-22.04-x86_64 amazonlinux-2023-x86_64
ERL_VERSION=26.0-openssl-3.1.0

all: x86_64 arm64v8

x86_64: centos-7.9-x86_64 rhel-8.8-x86_64 rhel-9.2-x86_64 ubuntu-20.04-x86_64 ubuntu-22.04-x86_64

arm64v8: ubuntu-20.04-arm64v8 ubuntu-22.04-arm64v8

centos-7.9-x86_64:
	cd centos/7.9-x86_64 && docker buildx build --platform=linux/amd64 --no-cache -t shiguredo/shiguredo-erlang:otp-${ERL_VERSION}-$@ .
	docker push shiguredo/erlang:otp-${ERL_VERSION}-$@

rhel-8.8-x86_64:
	cd rhel/8.8-x86_64 && docker buildx build --platform=linux/amd64  --no-cache -t shiguredo/shiguredo-erlang:otp-${ERL_VERSION}-$@ .
	docker push shiguredo/erlang:otp-${ERL_VERSION}-$@

rhel-9.2-x86_64:
	cd rhel/9.2-x86_64 && docker buildx build --platform=linux/amd64  --no-cache -t shiguredo/shiguredo-erlang:otp-${ERL_VERSION}-$@ .
	docker push shiguredo/erlang:otp-${ERL_VERSION}-$@

ubuntu-20.04-x86_64:
	cd ubuntu/20.04-x86_64 && docker buildx build --platform=linux/amd64  --no-cache -t shiguredo/shiguredo-erlang:otp-${ERL_VERSION}-$@ .
	docker push shiguredo/erlang:otp-${ERL_VERSION}-$@

ubuntu-22.04-x86_64:
	cd ubuntu/22.04-x86_64 && docker buildx build --platform=linux/amd64  --no-cache -t shiguredo/shiguredo-erlang:otp-${ERL_VERSION}-$@ .
	docker push shiguredo/erlang:otp-${ERL_VERSION}-$@

ubuntu-20.04-arm64v8:
	cd ubuntu/20.04-arm64v8 && docker buildx build --platform=linux/arm64  --no-cache -t shiguredo/shiguredo-erlang:otp-${ERL_VERSION}-$@ .
	docker push shiguredo/erlang:otp-${ERL_VERSION}-$@

ubuntu-22.04-arm64v8:
	cd ubuntu/22.04-arm64v8 && docker buildx build --platform=linux/arm64 --no-cache -t shiguredo/shiguredo-erlang:otp-${ERL_VERSION}-$@ .
	docker push shiguredo/erlang:otp-${ERL_VERSION}-$@

ubuntu-22.04-x86_64:
	cd ubuntu/22.04-x86_64 && docker buildx build --platform=linux/amd64  --no-cache -t shiguredo/shiguredo-erlang:otp-${ERL_VERSION}-$@ .
	docker push shiguredo/shiguredo-erlang:otp-${ERL_VERSION}-$@

ubuntu-22.04-arm64v8:
	cd ubuntu/22.04-arm64v8 && docker buildx build --platform=linux/arm64 --no-cache -t shiguredo/shiguredo-erlang:otp-${ERL_VERSION}-$@ .
	docker push shiguredo/shiguredo-erlang:otp-${ERL_VERSION}-$@

ubuntu-multi-arch:
	docker manifest create shiguredo/shiguredo-erlang:otp-${ERL_VERSION}-ubuntu-22.04 \
		shiguredo/shiguredo-erlang:otp-${ERL_VERSION}-ubuntu-22.04-x86_64 \
		shiguredo/shiguredo-erlang:otp-${ERL_VERSION}-ubuntu-22.04-arm64v8
	docker manifest push shiguredo/shiguredo-erlang:otp-${ERL_VERSION}-ubuntu-22.04
