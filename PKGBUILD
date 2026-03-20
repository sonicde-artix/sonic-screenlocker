# Maintainer: artist for Sonic-DE

pkgname=sonic-screenlocker
pkgver=6.6.3
_dirver=$(echo $pkgver | cut -d. -f1-3)
pkgrel=2
pkgdesc='Library and components for Sonic-DE secure lock screen architecture'
arch=(x86_64)
url='https://github.com/Sonic-DE/sonic-screenlocker'
license=(LGPL-2.0-or-later)
depends=(gcc-libs
         glibc
         kconfig
         kcoreaddons
         kcrash
         kdeclarative
         ki18n
         kidletime
         kio
         kirigami
         knotifications
         kpackage
         ksvg
         kwindowsystem
         kxmlgui
         sonic-screen-library
         libx11
         libxcb
         libxi
         pam
         libplasma
         qt6-base
         qt6-declarative
         sonic-frameworks-keybind
         xcb-util-keysyms)
makedepends=(extra-cmake-modules
             kcmutils
             kdoctools)
optdepends=('kcmutils: configuration module')
groups=(sonicde)
conflicts=(kscreenlocker)
provides=(kscreenlocker)
source=("$pkgname-$pkgver.tar.gz::${url}/archive/refs/tags/${_dirver}.tar.gz"
        kde.pam
        kde-fingerprint.pam 
        kde-smartcard.pam)

build() {
  cmake -B build  -S $pkgname-$pkgver \
    -DCMAKE_INSTALL_LIBEXECDIR=/usr/lib \
    -DBUILD_TESTING=OFF
  cmake --build build
}

package() {
  DESTDIR="$pkgdir" cmake --install build

  install -Dm644 "$srcdir"/kde.pam "$pkgdir"/usr/lib/pam.d/kde
  install -Dm644 "$srcdir"/kde-fingerprint.pam "$pkgdir"/usr/lib/pam.d/kde-fingerprint
  install -Dm644 "$srcdir"/kde-smartcard.pam "$pkgdir"/usr/lib/pam.d/kde-smartcard
}

sha256sums=('a118fd937516d4a31650eebc9c3799b09c89ca6f2e2bca28acdbf8c121ac7e88'
            'adba7bb7c27eb3a572e5e9d3cea0dbeebe59d3634472d1863d14fe892cb13b2b'
            '32734b4e1ec8b7f7e32b6cb2d68285c5c4f15f53736bba085096e76095181241'
            '5d9c31cbf66e8e455b9559c929f184efd598f714743d5a1e6ce20adb44dc4b2d')
