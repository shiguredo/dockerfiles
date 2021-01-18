.PHONY: all ubuntu-20.04

ERL_VERSION=master-jit-$(shell date "+%Y%m%d")

all: ubuntu-20.04

ubuntu-20.04:
	cd ubuntu/20.04 && docker build --no-cache -t shiguredo/erlang:otp-${ERL_VERSION}-$@ .
	docker push shiguredo/erlang:otp-${ERL_VERSION}-$@
