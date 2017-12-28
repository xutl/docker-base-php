FROM xutl/centos:7

LABEL maintainer="xutongle@gmail.com"

# persistent / runtime deps
ENV PHPIZE_DEPS \
		autoconf \
		file \
		g++ \
		gcc \
		gcc-c++ \
		glibc-devel \
		make \
		pkg-config \
		re2c

RUN set -x \
	&& yum update -y \
	&& yum install -y \
		$PHPIZE_DEPS \
		curl \
		libjpeg \
		libpng \
		freetype \
		libxml2 \
		zlib \
		bzip2 \
		libidn \
		gettext \
		libxslt \
		libedit \
		libtidy \
		gd \
		mhash \
	&& yum clean all && rm -rf /var/cache/yum/*

RUN set -x \
	&& cd /usr/local/src \
	&& curl -fSL https://ftp.gnu.org/pub/gnu/libiconv/libiconv-1.15.tar.gz -o libiconv-1.15.tar.gz \
	&& tar zxf libiconv-1.15.tar.gz \
	&& rm -rf libiconv-1.15.tar.gz \
	&& cd libiconv-1.15/ \
	&& ./configure --prefix=/usr/local --libdir=/usr/local/lib64 --enable-static \
	&& make -j "$(nproc)" \
	&& make install \
	&& rm -rf /usr/local/src/libiconv-1.15

RUN set -x \
	&& cd /usr/local/src \
	&& curl -fSL http://7xk96f.com1.z0.glb.clouddn.com/software/icu/icu4c-58_2-src.tgz -o icu4c-58_2-src.tgz \
	&& tar zxf icu4c-58_2-src.tgz \
	&& rm -rf icu4c-58_2-src.tgz \
	&& cd icu/source/ \
	&& ./configure --prefix=/usr/local --libdir=/usr/local/lib64 --enable-static \
	&& make -j "$(nproc)" \
	&& make install \
	&& /sbin/ldconfig