FROM xutl/ubuntu:bionic

LABEL maintainer="xutongle@gmail.com"

# persistent / runtime deps
ENV PHPIZE_DEPS autoconf dpkg-dev file g++ gcc libc-dev make pkg-config re2c

RUN set -x \
#	&& sed -i 's/archive.ubuntu.com/mirrors.aliyun.com/' /etc/apt/sources.list \
	&& apt-get update \
	&& apt-get install -y --no-install-recommends --no-install-suggests \
		$PHPIZE_DEPS \
		curl \
		libssl1.1 \
		libedit2 \
		libsqlite3-0 \
		libxml2 \
		libxslt1.1 \
		libtidy5 \
		libjpeg9 \
		libpng16-16 \
		libcurl4 \
		libbz2-1.0 \
		libfreetype6 \
		libgmp10 \
		libedit2 \
		libzip4 \
		zlib1g \
	&& rm -r /var/lib/apt/lists/*

RUN cd /usr/local/src \
	&& curl -fSL https://ftp.gnu.org/pub/gnu/libiconv/libiconv-1.15.tar.gz -o libiconv-1.15.tar.gz \
	&& tar zxf libiconv-1.15.tar.gz \
	&& rm -rf libiconv-1.15.tar.gz \
	&& cd libiconv-1.15/ \
	&& ./configure --prefix=/usr/local --libdir=/usr/local/lib64 --enable-static \
	&& make -j "$(nproc)" \
	&& make install \
	&& rm -rf /usr/local/src/libiconv-1.15


