
url="https://gitlab.com/caveman250/Headlines"
pkgdesc="A GTK4/libAdwaita Reddit client written in C++"
license="GPL-3.0"
pkgname=headlines-git
pkgrel=0
pkgver="_git"
options="!check"
arch="all"
provides="headlines"
source=""
builddir="${srcdir}/${pkgname}"

makedepends="git gtkmm4-dev cmake gcc libmicrohttpd-dev curl-dev openssl-dev jsoncpp-dev libxml2-dev ffmpeg-dev gstreamer-dev gst-plugins-bad-dev gst-plugins-base-dev boost-dev websocket++ libadwaita-dev xdg-utils libsecret-dev"

depends="youtube-dl boost gst-libav libadwaita gtkmm4 libmicrohttpd curl openssl jsoncpp libxml2 ffmpeg gstreamer gst-plugins-bad gst-plugins-good gst-plugins-base boost"

prepare() {
    	cd "${srcdir}"
	git clone --depth=1 "${url}" "${pkgname}"
	cd "${builddir}"
	default_prepare
}

build() {
    	cd "${builddir}"
	cmake \
	  	-B build \
		-DCMAKE_BUILD_TYPE=Release \
		-DDIST_BUILD=ON \
		-DCMAKE_INSTALL_PREFIX=/usr \
		-Wno-dev
	make -C build
}

package() {
	make -C build install DESTDIR="$pkgdir/"
}
