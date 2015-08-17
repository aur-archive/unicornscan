# Contributor: Pranay Kanwar <pranay.kanwar@gmail.com>

pkgname=unicornscan
pkgver=0.4.7
pkgrel=3
url="http://www.unicornscan.org/"
depends=('libpcap' 'postgresql-libs' 'geoip' 'libdnet' 'libltdl')
makedepends=('flex' 'bison')
license=("GPL")
arch=("i686" "x86_64")
source=("http://www.unicornscan.org/releases/$pkgname-$pkgver-2.tar.bz2")
md5sums=('4c5f272eb38c333c0094c32317edf758')
pkgdesc="Unicornscan is a new information gathering and correlation engine."

build() {
  # prevent crashing geoip dependency
  export LDFLAGS="${LDFLAGS/--as-needed,/}"
  cd "$srcdir/$pkgname-$pkgver"
  ./configure CFLAGS="$CFLAGS -D_GNU_SOURCE" --prefix=/usr --sysconfdir=/etc --localstatedir=/var --with-pgsql --with-geoip
  make
  make DESTDIR="$pkgdir" install
  cd "$pkgdir/etc/unicornscan"
  ln -s /usr/share/GeoIP/GeoIP.dat GeoIP.dat
}
