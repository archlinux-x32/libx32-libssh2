# Maintainer: Florian Pritz <flo@xssn.at>
# $Id: PKGBUILD 136290 2015-07-02 17:31:50Z bluewind $
# Contributor: Angel Velasquez <angvp@archlinux.org> 
# Contributor: Sergej Pupykin <pupykin.s+arch@gmail.com>
# Contributor: Andrea Scarpino <andrea@archlinux.org>
# Contributor: ice-man <icemanf@gmail.com>

_pkgbasename=libssh2
pkgname=lib32-$_pkgbasename
pkgver=1.6.0
pkgrel=1
pkgdesc="A library implementing the SSH2 protocol as defined by Internet Drafts (32-bit)"
url="http://www.libssh2.org/"
arch=('i686' 'x86_64')
license=('BSD')
depends=('lib32-openssl' $_pkgbasename)
provides=('libssh2.so')
makedepends=('zlib' "gcc-multilib")
options=('!libtool')
source=("http://www.libssh2.org/download/${_pkgbasename}-${pkgver}.tar.gz")
md5sums=('00aabd6e714a5f42a4fb82ace20db1dd')

build() {
  export CC="gcc -m32"
  export CXX="g++ -m32"
  export PKG_CONFIG_PATH="/usr/lib32/pkgconfig"

  cd ${srcdir}/${_pkgbasename}-${pkgver}
  ./configure --prefix=/usr --libdir=/usr/lib32
  make
}

package() {
  cd ${srcdir}/${_pkgbasename}-${pkgver}
  make DESTDIR=${pkgdir} install

  rm -rf "${pkgdir}"/usr/{include,share,bin,sbin}
  mkdir -p "$pkgdir/usr/share/licenses"
  ln -s $_pkgbasename "$pkgdir/usr/share/licenses/$pkgname"
}
