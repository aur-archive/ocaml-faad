# Maintainer: Charles E. Hawkins <charlesthehawk at yahoo dot com>
# Contributor: Thomas S Hatch <thatch45 at gmail dot com>
pkgname=ocaml-faad
pkgver=0.3.2
pkgrel=1
arch=('i686' 'x86_64')
license=('GPL')
pkgdesc="OCaml libs for faad."
url="http://savonet.sourceforge.net/"
depends=()
makedepends=('ocaml' 'ocaml-findlib' 'faad2')
options=('!strip' '!makeflags')
source=("http://downloads.sourceforge.net/savonet/${pkgname}-${pkgver}.tar.gz")
md5sums=('a6f15887ecb9ed0d3b3c930776d54c0a')

build() {
  cd "${srcdir}/${pkgname}-${pkgver}"
  ./configure --prefix=/usr
  make all
}

package() {
  cd "${srcdir}/${pkgname}-${pkgver}"
  mkdir -p ${pkgdir}/usr/share/doc/${pkgname}/example
  cp -a example/* ${pkgdir}/usr/share/doc/${pkgname}/example
  mkdir -p ${pkgdir}$(ocamlfind printconf destdir)
  make \
    OCAMLFIND_DESTDIR=${pkgdir}$(ocamlfind printconf destdir) \
    OCAMLFIND_LDCONF=ignore \
    install
}
