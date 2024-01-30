# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: kpcyrd <kpcyrd[at]archlinux[dot]org>
# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>

pkgname=libngtcp2
pkgver=1.2.0
pkgrel=1
pkgdesc='Implementation of IETF QUIC protocol'
url='https://github.com/ngtcp2/ngtcp2'
arch=(
  'x86_64'
  'arm'
  'aarch64'
)
license=('MIT')
provides=('libngtcp2.so')
source=("${pkgname}-${pkgver}.tar.gz::https://github.com/ngtcp2/ngtcp2/archive/refs/tags/v${pkgver}.tar.gz")
sha256sums=('15f3dd4cc4db2435bcd0b5253ccce4cbab26d18cc6ef4f00b5cb4af21ed06a0b')

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
  cd \
    ngtcp2-${pkgver}/lib
  make \
    DESTDIR="${pkgdir}" \
    install
  install \
    -Dm644 \
    ../COPYING \
    -t \
      "${pkgdir}/usr/share/licenses/${pkgname}"
}

# vim:set sw=2 sts=-1 et:
