# Maintainer: Andrea Scarpino <andrea@archlinux.org>

pkgname=kwallet-git
_pkgname=kwallet
pkgver=v5.102.0.r16.g130491f
pkgrel=1
pkgdesc='KWallet Framework'
arch=(i686 x86_64)
url='https://invent.kde.org/frameworks/kwallet'
license=(LGPL)
depends=(knotifications-git kiconthemes-git kservice-git gpgme)
makedepends=(extra-cmake-modules-git git python boost kdoctools-git
qca-qt6)
conflicts=(${_pkgname})
provides=(${_pkgname})
source=("git+${url}.git")
md5sums=('SKIP')

pkgver() {
  cd "$_pkgname"
  it describe --long --abbrev=7 | sed 's/^foo-//;s/\([^-]*-g\)/r\1/;s/-/./g'
}

build() {
  cmake -B build -S ${_pkgname} \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DKDE_INSTALL_LIBDIR=lib \
    -DKDE_INSTALL_USE_QT_SYS_PATHS=ON \
    -DBUILD_TESTING=OFF
  cmake --build build
}

package() {
  DESTDIR="$pkgdir" cmake --install build
}
