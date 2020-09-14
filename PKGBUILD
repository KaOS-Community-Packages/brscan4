pkgname=brscan4
pkgver=0.4.9_1
pkgrel=1
pkgdesc="SANE drivers from Brother for brscan4 compatible models"
url="http://support.brother.com/g/s/id/linux/en"
license=('GPL' 'custom:Brother')
depends=('sane' 'sed' 'libusb-compat')
arch=('x86_64')
install=brscan4.install

pkg="${pkgname}-${pkgver/_/-}.x86_64.rpm"
pkg_md5sum="02329240d6f8943f8c9e8dd663878a1d"

backup=(opt/brother/scanner/brscan4/brsanenetdevice4.cfg)
source=("http://download.brother.com/welcome/dlf006648/$pkg" "agree.html" "brscan4.rules")

md5sums=($pkg_md5sum 'ccffb9a6f6d436b21be25b0241068981' 'a865404f01de89430be88638bcb77f60')

package() {
  cp -r $srcdir/etc $pkgdir
  cp -r $srcdir/opt $pkgdir
  cp -r $srcdir/usr $pkgdir
  mv $pkgdir/usr/lib64 $pkgdir/usr/lib
  install -d -m755 $pkgdir/usr/lib/udev/rules.d/
  install -D -m644 $srcdir/brscan4.rules $pkgdir/usr/lib/udev/rules.d/
  install -D -m644 $srcdir/agree.html $pkgdir/usr/share/licenses/$pkgname/LICENSE.html
  cd $pkgdir/usr/lib/sane
  ln -sf libsane-brother4.so.1.0.7 libsane-brother4.so.1
  ln -sf libsane-brother4.so.1 libsane-brother4.so
}

