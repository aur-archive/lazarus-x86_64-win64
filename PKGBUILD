# Contributor: vantu5z <vantu5z@mail.ru>
pkgname=lazarus-x86_64-win64
pkgver=1.4.0
pkgrel=1
pkgdesc="Lazarus Component Library (x86_64-win64)"
url="http://www.lazarus.freepascal.org"
license=("GPL2, MPL, custom:LGPL")
arch=(any)
depends=(fpc-x86_64-win64-rtl)
makedepends=(lazarus)
[ $CARCH = "i686" ] && makedepends=(ppcrossx64)
options=(!emptydirs !makeflags !strip staticlibs)
#optdepends=("mingw-w64-qt4pas: LCL Qt4 backend linkage")
#"mingw-w64-gtk2: LCL Gtk+2 backend linkage")
source=("http://downloads.sourceforge.net/project/lazarus/Lazarus%20Zip%20_%20GZip/Lazarus%201.4/lazarus-$pkgver-0.tar.gz")
md5sums=('479c64ef40a327142f56e9378b7e8612')

build() {
  cd "$srcdir/lazarus"
  lazbuild --os=win64 --ws=win32 --cpu=x86_64 --lazarusdir=`pwd` lcl/lclbase.lpk
  lazbuild --os=win64 --ws=win32 --cpu=x86_64 lcl/interfaces/lcl.lpk
#   lazbuild --os=win64 --ws=qt --cpu=x86_64 lcl/lclbase.lpk
#   lazbuild --os=win64 --ws=qt --cpu=x86_64 lcl/interfaces/lcl.lpk
  
  # gtk2int.pas(56,3) Fatal: Can't find unit gdk2pixbuf used by Gtk2Int
  # -
  #lazbuild --os=win64 --ws=gtk2 --cpu=x86_64 lcl/lclbase.lpk
  #lazbuild --os=win64 --ws=gtk2 --cpu=x86_64 lcl/interfaces/lcl.lpk
}

package() {
  cd "$srcdir/lazarus"
  mkdir -p "$pkgdir/usr/lib/lazarus"
  find . -type f -path *x86_64-win64* -exec cp --parents '{}' "$pkgdir/usr/lib/lazarus/" \;
  find $pkgdir -name '*.o' -o -name '*.a' | xargs x86_64-w64-mingw32-strip -g
}

