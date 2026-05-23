# Maintainer: artist for Artix Linux

pkgname=sonic-screenlocker
pkgver=6.6.5
pkgrel=1
_commit="db1878f38118a504d8c052d79c07e4bb5ba11b47"
pkgdesc='Library and components for Artix Linux secure lock screen architecture'
arch=(x86_64)
url='https://github.com/Sonic-DE/sonic-screenlocker'
license=(LGPL-2.0-or-later)
depends=(glibc
         kconfig
         sonic-frameworks-core-addons
         kcrash
         kdeclarative
         ki18n
         kidletime
         sonic-frameworks-io
         sonic-frameworks-quick-ui
         knotifications
         kpackage
         ksvg
         kxmlgui
         libgcc
         libx11
         libxcb
         libxi
         pam
         qt6-base
         qt6-declarative
         sonic-frameworks-keybind
         sonic-frameworks-windowsystem
         sonic-interface-libraries
         sonic-screen-library
         xcb-util-keysyms)
makedepends=(extra-cmake-modules
             kcmutils
             kdoctools)
optdepends=('kcmutils: configuration module')
groups=(sonicde)
conflicts=(kscreenlocker)
provides=(kscreenlocker)
makedepends+=(git)
source=("$pkgname-$pkgver::git+$url.git#commit=$_commit"
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

sha256sums=('d3fccc0f1a271296dd4afcb8787f9519000cbbb1c1b196bba5364cca06066545'
            'adba7bb7c27eb3a572e5e9d3cea0dbeebe59d3634472d1863d14fe892cb13b2b'
            '32734b4e1ec8b7f7e32b6cb2d68285c5c4f15f53736bba085096e76095181241'
            '5d9c31cbf66e8e455b9559c929f184efd598f714743d5a1e6ce20adb44dc4b2d')

