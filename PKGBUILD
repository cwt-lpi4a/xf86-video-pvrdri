# Maintainer: Chaiwat Suttipongsakul <cwt@bashell.com>
pkgname="xf86-video-pvrdri"
pkgver=r45.99aec00
pkgrel=1
pkgdesc="DDX for KMS devices accelerated by PowerVR GPUs (Mesa DRI drivers)"
arch=('riscv64')
url="https://github.com/Icenowy/aosc-os-pvr/"
license=('MIT')
depends=('xorg-server' 'mesa' 'libdrm' 'libepoxy')
makedepends=('xorg-server-devel' 'git')
source=("git+https://github.com/Icenowy/aosc-os-pvr.git")
md5sums=('SKIP')

pkgver() {
  cd "$srcdir/aosc-os-pvr"
  printf 'r%s.%s' "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
  cd "$srcdir/aosc-os-pvr/common/$pkgname/autobuild/src"
  mkdir build
  cd build
  meson setup ..
  ninja $NINJAFLAGS -C .
}

package() {
  cd "$srcdir/aosc-os-pvr/common/$pkgname/autobuild/src"
  DESTDIR="${pkgdir}" ninja $NINJAFLAGS -C build install
}
