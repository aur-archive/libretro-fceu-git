# Maintainer:  prettyvanilla <prettyvanilla@posteo.at>
# Contributor: almostalive   <almostalive2003 at gmail dot com>

pkgname=libretro-fceu-git
pkgver=264.a77b86f
pkgrel=2
pkgdesc="libretro implementation of FCEUmm/FCEUX. (Nintendo Entertainment System)"
arch=('i686' 'x86_64' 'arm' 'armv6h')
url="https://github.com/libretro/fceu-next"
license=('GPL')
makedepends=('git')

_gitname=fceu-next
source=("git+https://github.com/libretro/${_gitname}.git"
        "https://raw.github.com/libretro/libretro-super/master/dist/info/fceumm_libretro.info")
md5sums=('SKIP'
         'SKIP')

pkgver() {
  cd "${_gitname}"
  echo $(git rev-list --count HEAD).$(git rev-parse --short HEAD)
}

build() {
  cd "${_gitname}/fceumm-code"
  make -f Makefile.libretro
}

package() {
  install -Dm644 "${_gitname}/fceumm-code/fceumm_libretro.so" "${pkgdir}/usr/lib/libretro/libretro-fceu.so"
  install -Dm644 "fceumm_libretro.info" "${pkgdir}/usr/lib/libretro/libretro-fceu.info"
}
