pkgname=mkdtboimg-git
pkgver=r448.f6b572a
pkgrel=1
pkgdesc='mkdtboimg tool'
arch=(any)
url='https://android.googlesource.com/platform/system/tools/mkbootimg'
license=(Apache)
depends=(python2)
provides=(mkdtboimg mkdtimg mkdtimg-git)
source=(git+https://android.googlesource.com/platform/system/libufdt)
sha1sums=('SKIP')

pkgver() {
  cd libufdt
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
  sed -i 's|/usr/bin/env python$|/usr/bin/env python2|g' "$srcdir"/libufdt/utils/src/mkdtboimg.py
}

package() {
  install -m755 -d "$pkgdir"/usr/bin
  install -Dm 755 libufdt/utils/src/mkdtboimg.py "$pkgdir"/usr/bin/mkdtboimg
  ln -sf "$pkgdir"/usr/bin/mkdtboimg "$pkgdir"/usr/bin/mkdtimg
}
