# Maintainer: Gustavo Costa <xfgusta@gmail.com>

pkgname=konsole-with-titlebar-opt
_pkgname=konsole
pkgver=20.12.3
pkgrel=1
arch=(x86_64)
url='https://kde.org/applications/system/konsole/'
pkgdesc="KDE's terminal emulator with titlebar option"
license=(GPL LGPL FDL)
groups=(kde-applications kde-utilities)
depends=(knotifyconfig kpty kparts kinit knewstuff)
makedepends=(extra-cmake-modules kdoctools)
conflicts=($_pkgname)
provides=($_pkgname)
optdepends=('keditbookmarks: to manage bookmarks')
source=("https://download.kde.org/stable/release-service/$pkgver/src/$_pkgname-$pkgver.tar.xz"
        'titlebar.patch')
sha256sums=('24cd42fdc4ae2e17526bfab9c5ad516bb25b22d654782e98aa52f6e39bdd138d'
            'SKIP')

prepare() {
    patch -p1 --input="${srcdir}/titlebar.patch"
}

build() {
  cmake -B build -S $_pkgname-$pkgver \
    -DBUILD_TESTING=OFF
  cmake --build build
}

package() {
  DESTDIR="$pkgdir" cmake --install build
} 
