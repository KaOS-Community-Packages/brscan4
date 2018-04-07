license=('GPL' 'custom:Brother')
arch=('x86_64')
pkgname=brscan4
pkgver=0.4.4_4
pkgrel=1
pkgdesc="SANE drivers from Brother for brscan4 compatible models"
depends=('sane' 'sed' 'libusb-compat')
makedepends=('sane')
url="http://support.brother.com/g/s/id/linux/en"
install=brscan4.install

pkg="${pkgname}-${pkgver/_/-}.x86_64.rpm"
pkg_md5sum="9319e08317382f76f5e8ad294de8c569"

backup=("/opt/brother/scanner/brscan4/brsanenetdevice4.cfg")
source=("http://download.brother.com/welcome/dlf006648/$pkg" "http://www.brother.com/agreement/English_sane/agree.html" "brscan4.rules")
md5sums=($pkg_md5sum 'ccffb9a6f6d436b21be25b0241068981' 'a865404f01de89430be88638bcb77f60')

package() {
  cp -r $srcdir/etc $pkgdir
  cp -r $srcdir/opt $pkgdir
  cp -r $srcdir/usr $pkgdir
  install -d -m755 $pkgdir/etc/udev/rules.d
  install -D -m644 $srcdir/brscan4.rules $pkgdir/etc/udev/rules.d
  install -D -m644 $srcdir/agree.html $pkgdir/usr/share/licenses/$pkgname/LICENSE.html
  mv $pkgdir/usr/lib64 $pkgdir/usr/lib
  cd $pkgdir/usr/lib/sane
  ln -sf libsane-brother4.so.1.0.7 libsane-brother4.so.1
  ln -sf libsane-brother4.so.1 libsane-brother4.so
}
