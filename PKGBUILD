# Maintainer: kpcyrd <kpcyrd[at]archlinux[dot]org>

pkgname=libngtcp2
pkgver=1.1.0
pkgrel=1
pkgdesc='Implementation of IETF QUIC protocol'
url='https://github.com/ngtcp2/ngtcp2'
arch=('x86_64')
license=('MIT')
provides=('libngtcp2.so')
source=("${pkgname}-${pkgver}.tar.gz::https://github.com/ngtcp2/ngtcp2/archive/refs/tags/v${pkgver}.tar.gz")
sha256sums=('987d784643edea4f2859c405f7dfbc53871a9f7ae5fcddf5fb12ec5dfce1ef22')

prepare() {
  cd ngtcp2-${pkgver}
  autoreconf -i
}

build() {
  cd ngtcp2-${pkgver}
  # add --with-openssl after quic was released in openssl mainline
  ./configure \
    --prefix=/usr
  make
}

check() {
  cd ngtcp2-${pkgver}
  make check
}

package() {
  cd ngtcp2-${pkgver}/lib
  make DESTDIR="${pkgdir}" install
  install -Dm644 ../COPYING -t "${pkgdir}/usr/share/licenses/${pkgname}"
}

# vim: ts=2 sw=2 et:
