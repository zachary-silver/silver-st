# Maintainer: Zachary Silver <zmansilver@gmail.com>

pkgname=silver-st
pkgver=0.8.1
pkgrel=2
pkgdesc='A customized clone of a simple virtual terminal emulator for X.'
arch=('i686' 'x86_64')
license=('MIT')
depends=('libxft' 'libxext' 'xorg-fonts-misc' 'ttf-dejavu')
makedepends=('ncurses')
provides=($pkgname)
conflicts=($pkgname 'st')
url="www.github.com/ZmanSilver/silver-st"
source=(https://www.dropbox.com/s/1byx58zts3swycf/silver-st.tar.gz
	config.h)
sha256sums=('089e90add3056486633f89d029a2109592e49812839e43fb7af2dadb62000194'
            '20575c9acb647193c4ad12dfb6e6992bac0fda4f4c0ec068984c19c0e0be57eb')

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
