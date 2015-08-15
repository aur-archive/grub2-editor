# Maintainer: hbdee <hbdee.arch@gmail.com>
# Contributor: Vindex17 <vindex17@outlook.it>
# Contributor: Konstantinos Smanis <konstantinos.smanis [at] gmail [dot] com>

pkgname=grub2-editor
_pkgname=kcm-grub2
pkgver=0.6.4
pkgrel=7
pkgdesc='A KDE Control Module for configuring the GRUB2 bootloader'
arch=('i686' 'x86_64')
url='http://sourceforge.net/projects/kcm-grub2/'
license=('GPL3')
depends=('kdebase-runtime' 'grub' 'imagemagick' 'hwinfo')
makedepends=('cmake' 'automoc4' 'gettext')
optdepends=('kdebase-workspace: systemsettings integration'
	    'memtest86+: memtest entries on grub')
source=("http://downloads.sourceforge.net/project/${_pkgname}/$pkgver/${_pkgname}-$pkgver.tar.gz")
install='grub2-editor.install'
sha512sums=('d996520762290b344737cba06a7b1db58ff016d6d91ab59514d6c675a3ad449ec81da0589a5f3b8ea50a9082fe5d32529a6112b5478f079f9ac08904d10eb0fe')

prepare() {
	cd "$srcdir/${_pkgname}-$pkgver"
	rm -rf build
	mkdir build
}

build() {
	cd "$srcdir/${_pkgname}-$pkgver/build"
	cmake -DCMAKE_INSTALL_PREFIX=$(kde4-config --prefix) \
	      -DCMAKE_BUILD_TYPE=Release \
	      -DGRUB_MEMTEST=/etc/grub.d/60_memtest86+ \
	      ..
	make
}

package() {
	cd "$srcdir/${_pkgname}-$pkgver/build"
	make DESTDIR="$pkgdir/" install
} 
