# Maintainer: Davide Iosca <dvdios[at]aol[dot]com>
pkgname=iclingo
pkgver=3.0.4
pkgrel=2
pkgdesc="An incremental ASP system implemented on top of Clingo."
arch=('x86_64' 'i686')
url="http://potassco.sourceforge.net/"
license=('GPL3')
depends=('boost-libs>=1.37.1-1' 'lua51' 'gcc-libs')
makedepends=('boost>=1.37.1-1' 'cmake>=2.6')
optdepends=(
  'luasql-mysql: for Mysql support'
  'mysql: for Mysql support'
  'sqlite3: for Mysql support')
source=("http://downloads.sourceforge.net/project/potassco/${pkgname}/${pkgver}/${pkgname}-${pkgver}-source.tar.gz"
  "gringo-3.0.4.patch")
md5sums=('12b78f4b1630cd34f2d07bb14952ab16'
  'a51a0718957022f0bf45e6a8863f5cf7')

build() {
  cd "${srcdir}/${pkgname}-${pkgver}-source"
  patch -N -p1 -l -i ../gringo-3.0.4.patch
  cmake_options="-DWITH_LUA=system -DCMAKE_CXX_FLAGS=-fpermissive \
      -DLUA_INCLUDE_DIR=/usr/include/lua5.1 -DLUA_LIBRARY=/usr/lib/liblua5.1.so \
      -DLUA_LIBRARIES='/usr/lib/liblua5.1.so;/usr/lib/libm.so;/usr/lib/libdl.so'" make -e
}

package() {
  cd "${srcdir}/${pkgname}-${pkgver}-source/build/release/bin"
  install -D ${pkgname} ${pkgdir}/usr/bin/${pkgname}
}
