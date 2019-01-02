# Maintainer: Zachary Silver <zmansilver@gmail.com>

pkgname=silver-st
pkgver=0.8.1
pkgrel=1
pkgdesc='A customized clone of the simple virtual terminal emulator for X.'
arch=('i686' 'x86_64')
license=('MIT')
depends=('libxft' 'libxext' 'xorg-fonts-misc')
makedepends=('ncurses')
url="www.github.com/ZmanSilver/silver-st"
source=(https://www.dropbox.com/s/av0d5cv3bvh770m/silver-st.tar.gz
	config.h)
sha256sums=('202011ee5c57057a8a7fab68a41644094d1415c1fc1d2c682ab9e85455a47269'
            '6b4d5b6b67848809479120096491d17f812c8ca8af95b5ada877195a42011e73')

prepare() {
  cd $srcdir/$pkgname
  # skip terminfo which conflicts with ncurses
  sed -i '/tic /d' Makefile
  cp $srcdir/config.h config.h
}

build() {
  cd $srcdir/$pkgname
  make X11INC=/usr/include/X11 X11LIB=/usr/lib/X11
}

package() {
  cd $srcdir/$pkgname
  make PREFIX=/usr DESTDIR="$pkgdir" TERMINFO="$pkgdir/usr/share/terminfo" install
  install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
  install -Dm644 README "$pkgdir/usr/share/doc/$pkgname/README"
}
