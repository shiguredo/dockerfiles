.PHONY: all rhel-8.9-x86_64 rhel-9.3-x86_64 ubuntu-20.04-x86_64 ubuntu-22.04-x86_64 ubuntu-24.04-x86_64 
ERL_VERSION=26.2.2-openssl-3.2.1

all: x86_64 arm64v8

x86_64: rhel-8.9-x86_64 rhel-9.3-x86_64 ubuntu-20.04-x86_64 ubuntu-22.04-x86_64 ubuntu-24.04-x86_64

arm64v8: ubuntu-20.04-arm64v8 ubuntu-22.04-arm64v8 ubuntu-24.04-arm64v8

rhel-8.9-x86_64:
	cd rhel/8.9-x86_64 && docker buildx build --platform=linux/amd64 --memory=4g --no-cache -t shiguredo/shiguredo-erlang:otp-${ERL_VERSION}-$@ .
	docker push shiguredo/shiguredo-erlang:otp-${ERL_VERSION}-$@

rhel-9.3-x86_64:
	cd rhel/9.3-x86_64 && docker buildx build --platform=linux/amd64 --memory=4g --no-cache -t shiguredo/shiguredo-erlang:otp-${ERL_VERSION}-$@ .
	docker push shiguredo/shiguredo-erlang:otp-${ERL_VERSION}-$@

ubuntu-20.04-x86_64:
	cd ubuntu/20.04-x86_64 && docker buildx build --platform=linux/amd64 --memory=4g --no-cache -t shiguredo/shiguredo-erlang:otp-${ERL_VERSION}-$@ .
	docker push shiguredo/shiguredo-erlang:otp-${ERL_VERSION}-$@

ubuntu-20.04-arm64v8:
	cd ubuntu/20.04-arm64v8 && docker buildx build --platform=linux/arm64 --memory=4g --no-cache -t shiguredo/shiguredo-erlang:otp-${ERL_VERSION}-$@ .
	docker push shiguredo/shiguredo-erlang:otp-${ERL_VERSION}-$@

ubuntu-22.04-x86_64:
	cd ubuntu/22.04-x86_64 && docker buildx build --platform=linux/amd64 --memory=4g --no-cache -t shiguredo/shiguredo-erlang:otp-${ERL_VERSION}-$@ .
	docker push shiguredo/shiguredo-erlang:otp-${ERL_VERSION}-$@

ubuntu-22.04-arm64v8:
	cd ubuntu/22.04-arm64v8 && docker buildx build --platform=linux/arm64 --memory=4g --no-cache -t shiguredo/shiguredo-erlang:otp-${ERL_VERSION}-$@ .
	docker push shiguredo/shiguredo-erlang:otp-${ERL_VERSION}-$@

ubuntu-24.04-x86_64:
	cd ubuntu/24.04-x86_64 && docker buildx build --platform=linux/amd64 --memory=4g --no-cache -t shiguredo/shiguredo-erlang:otp-${ERL_VERSION}-$@ .
	docker push shiguredo/shiguredo-erlang:otp-${ERL_VERSION}-$@

ubuntu-24.04-arm64v8:
	cd ubuntu/24.04-arm64v8 && docker buildx build --platform=linux/arm64 --memory=4g --no-cache -t shiguredo/shiguredo-erlang:otp-${ERL_VERSION}-$@ .
	docker push shiguredo/shiguredo-erlang:otp-${ERL_VERSION}-$@

ubuntu-22.04-multi-arch:
	docker manifest create shiguredo/shiguredo-erlang:otp-${ERL_VERSION}-ubuntu-22.04 \
		shiguredo/shiguredo-erlang:otp-${ERL_VERSION}-ubuntu-22.04-x86_64 \
		shiguredo/shiguredo-erlang:otp-${ERL_VERSION}-ubuntu-22.04-arm64v8
	docker manifest push shiguredo/shiguredo-erlang:otp-${ERL_VERSION}-ubuntu-22.04
	
ubuntu-24.04-multi-arch:
	docker manifest create shiguredo/shiguredo-erlang:otp-${ERL_VERSION}-ubuntu-24.04 \
		shiguredo/shiguredo-erlang:otp-${ERL_VERSION}-ubuntu-24.04-x86_64 \
		shiguredo/shiguredo-erlang:otp-${ERL_VERSION}-ubuntu-24.04-arm64v8
	docker manifest push shiguredo/shiguredo-erlang:otp-${ERL_VERSION}-ubuntu-24.04
