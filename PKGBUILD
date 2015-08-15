# Contributor:  Ionut Biru <ibiru@archlinux.org>
# Contributor: Alexander Rødseth <rodseth@gmail.com>
# Contributor: Hugo Doria <hugo@archlinux.org>
# Contributor: Sergej Chodarev <sergejx@centrum.sk>
# Contributor: zhuqin <zhuqin83@gmail.com>
# Maintainer: Yosef Or Boczko <yoseforb@gnome.org>

_pkgname=gedit-plugins
pkgname=$_pkgname-git
pkgver=3.17.0.6.g6b11b79
_realver=3.17.0
pkgrel=1
pkgdesc="Plugins for gedit"
arch=(x86_64 i686)
license=(GPL)
url="https://wiki.gnome.org/Apps/Gedit/ShippedPlugins"
depends=("gtksourceview3" "gedit" python-dbus "glib2" "gtk3")
makedepends=(intltool gnome-doc-utils vte3 libgit2-glib git)
optdepends=('gucharmap: for charmap plugin'
            'vte3: for embedded terminal'
            'libgit2-glib: for git plugin')
options=('!libtool' '!emptydirs')
install=gedit-plugins.install
replaces=('gedit-plugins')
provides=("gedit-plugins=${_realver}")
conflicts=('gedit-plugins')
source=('git://git.gnome.org/gedit-plugins')
sha256sums=('SKIP')

pkgver() {
  cd "$srcdir/$_pkgname"
  git describe --always | sed 's|-|.|g'
}

prepare() {
  cd "$srcdir/$_pkgname"
}

build() {
  cd "$srcdir/$_pkgname"
  ./autogen.sh --prefix=/usr --sysconfdir=/etc --with-plugins=all \
      --disable-schemas-compile
  make
}

package() {
  cd "$srcdir/$_pkgname"
  make DESTDIR=$pkgdir install
}

# vim:set ts=2 sw=2 et:
