
pkgname=dustrac
pkgver=1.11.0
rel=1
pkgrel=1
pkgdesc="Dust Racing (Dustrac) is a tile-based, cross-platform 2D racing game written in Qt (C++) and OpenG."
arch=('i686' 'x86_64')
url="http://sourceforge.net/projects/dustrac/"
license=('GPL')
depends=('qt5-base' 'glu' 'openal' 'icu')
makedepends=('make' 'cmake')
source=("http://sourceforge.net/projects/dustrac/files/$pkgver/dustrac-$pkgver.tar.gz" "$pkgname.desktop")
md5sums=('bac37f501a6fbc17307ad6ce223ddb60' 'ccc24c540f2e7fd7880529ccda6cc408')
option=(strip)
install=${pkgname}.install

build() {
  cd $srcdir/$pkgname-$pkgver
  #./configure -DReleaseBuild=1 -DCMAKE_INSTALL_PREFIX=/usr
  qmake $pkgname.pro
  make
}

package() { 
  cd ${srcdir}/$pkgname-$pkgver
  #make CMAKE_INSTALL_PREFIX=${pkgdir} install
  #make DESTDIR="${pkgdir}" install
  mkdir ${pkgdir}/usr && mkdir ${pkgdir}/usr/bin
  cp src/editor/$pkgname-editor ${pkgdir}/usr/bin/ && cp src/game/$pkgname-game ${pkgdir}/usr/bin/
  #mv src/editor/$pkgname-{editor,game} ${pkgdir}/usr/bin/
  #mv {AUTHORS,CHANGELOG,COPYING,README} ${pkgdir}/usr/data/
  mkdir ${pkgdir}/usr/share && mkdir ${pkgdir}/usr/share/games && mkdir ${pkgdir}/usr/share/games/DustRacing
  cp -rp data ${pkgdir}/usr/share/games/DustRacing
  cp -ap ${srcdir}/$pkgname-$pkgver/data/meshes.conf ${pkgdir}/usr/share/games/DustRacing/data/
  cp -rp ${srcdir}/$pkgname-$pkgver/data/models ${pkgdir}/usr/share/games/DustRacing/data/
 
  # desktop file
    install -Dm644 $srcdir/$pkgname.desktop \
    "$pkgdir/usr/share/applications/$pkgname.desktop"
   
  # icon
 #   install -Dm644 $pkgname.png \
  #  "$pkgdir/usr/share/pixmaps/$pkgname.png"
}
