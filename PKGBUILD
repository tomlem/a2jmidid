# $Id: PKGBUILD 123274 2015-01-12 10:33:51Z speps $
# Maintainer :
# Contributor:

pkgname=a2jmidid
pkgver=8
pkgrel=1
pkgdesc="A daemon for exposing legacy ALSA sequencer applications in JACK MIDI system."
arch=('x86_64')
url="http://home.gna.org/$pkgname/"
license=('GPL')
depends=('jack' 'dbus-python2')
source=("http://download.gna.org/$pkgname/$pkgname-$pkgver.tar.bz2"
        "$pkgname-dso-pthread.patch")
md5sums=('9cf4edbc3ad2ddeeaf6c8c1791ff3ddd'
         '4b15e485301aee48371844cb01689ad2')

prepare() {
  cd $pkgname-$pkgver

  # DSO link patch
  patch -p1 -i ../$pkgname-dso-pthread.patch

  # python2 shebang
  sed -i 's/python/&2/' a2j_control
}

build() {
  cd $pkgname-$pkgver
  python2 waf configure --prefix=/usr
  python2 waf
}

package() {
  cd $pkgname-$pkgver
  python2 waf install --destdir="$pkgdir/"
}
