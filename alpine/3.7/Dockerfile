FROM xutl/alpine:3.7

LABEL maintainer="xutongle@gmail.com"

# persistent / runtime deps
ENV PHPIZE_DEPS autoconf dpkg-dev file g++ gcc libc-dev make re2c

RUN apk add --no-cache --virtual .persistent-deps \
		curl \
		tar \
		libressl

# ensure www-data user exists
RUN set -x \
	&& apk add --no-cache --virtual .persistent-deps \
		curl \
		tar \
		libressl \
	&& addgroup -g 82 -S www-data \
	&& adduser -u 82 -D -S -G www-data www-data
# 82 is the standard uid/gid for "www-data" in Alpine
