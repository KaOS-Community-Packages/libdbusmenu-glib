pkgname=libdbusmenu-glib
pkgver=16.04.0
pkgrel=1
pkgdesc="A library for passing menus over DBus"
arch=('x86_64')
url="https://launchpad.net/libdbusmenu"
license=('GPL3')
depends=('glib2')
makedepends=('gobject-introspection' 'gtk3' 'intltool')
source=("http://launchpad.net/dbusmenu/${pkgver%.?}/${pkgver}/+download/libdbusmenu-${pkgver}.tar.gz")
sha256sums=('b9cc4a2acd74509435892823607d966d424bd9ad5d0b00938f27240a1bfa878a')

prepare() {
  cd libdbusmenu-${pkgver}
  # don't treat warnings as errors
  sed -i 's/-Werror//' libdbusmenu-*/Makefile.{am,in}
}

build() {
  cd libdbusmenu-${pkgver}
  export HAVE_VALGRIND_TRUE='#'
  export HAVE_VALGRIND_FALSE=''
  ./configure \
    --prefix='/usr' \
    --sysconfdir='/etc' \
    --localstatedir='/var' \
    --disable-{dumper,static,tests,vala,doc}
  make
}

package() {
  cd libdbusmenu-${pkgver}
  make -C libdbusmenu-glib DESTDIR="${pkgdir}" install
}

