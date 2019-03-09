pkgname=wingpanel
pkgver=2.2.2~1~gfc1b8ea
pkgrel=1
pkgdesc='Stylish top panel that holds indicators and spawns an application launcher'
arch=('x86_64')
url='https://github.com/elementary/wingpanel'
license=('GPL3')
groups=('pantheon-unstable')
depends=('glib2' 'glibc' 'gtk3' 'libgee' 'libmutter2'
         'libgala.so' 'libgranite.so')
makedepends=('cmake' 'gala' 'git' 'granite' 'vala')
provides=('libwingpanel-2.0.so')
source=('git+https://github.com/elementary/wingpanel.git' 'autohide.patch')
sha256sums=('SKIP' 'SKIP')

pkgver() {
  cd wingpanel
  echo "$(git describe HEAD --tags | sed 's|-|~|g')"
}

prepare() {
  cd wingpanel
  patch -Np1 -i ${srcdir}/autohide.patch
  mkdir -p build
}

build() {
  arch-meson wingpanel build \
    -D b_pie=false
  ninja -C build
}

package() {
  DESTDIR="${pkgdir}" meson install -C build
}

# vim: ts=2 sw=2 et:
