# Maintainer: Zachary Silver <zmansilver@gmail.com>

pkgname=silver-st
pkgver=0.8.1
pkgrel=1
pkgdesc='A customized clone of the simple virtual terminal emulator for X.'
arch=('i686' 'x86_64')
license=('MIT')
depends=('libxft' 'libxext' 'xorg-fonts-misc')
makedepends=('ncurses')
url="http://st.suckless.org"
source=(https://github.com/ZmanSilver/silver-st/blob/master/silver-st.tar.gz
        config.h)
sha256sums=('7ddc89e2cd65ff294f3bc2af3c63a6c68cbc850b7ff09ba6aa15c0632bf0280a'
            'e700886ac3265a609f76b8118b7f43e585be34319ac990e79a66ae5b46dd13ff')

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
