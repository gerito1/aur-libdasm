# Contributor: Sebastien Duquette <ekse.0x@gmail.com>
pkgname=libdasm
pkgver=1.6r15
pkgrel=1
pkgdesc="a disassembly library"
arch=('i686' 'x86_64')
url="https://github.com/alexeevdv/libdasm.git"
license=('custom:Public Domain') # a modifier
depends=()
source=("$pkgname::git+https://github.com/alexeevdv/libdasm.git")
md5sums=('SKIP')
build() {
  cd "$srcdir/$pkgname"

  git apply --stat ../../pydasm.patch

  mkdir build
  cd ./build
  cmake ..
  make || return 1
}

package() {
  cd "$srcdir/$pkgname"

  install -D -m644 libdasm.h  $pkgdir/usr/include/libdasm.h
  install -D -m755 build/libdasm.so $pkgdir/usr/lib/libdasm.so
  install -d -m755 examples/ $pkgdir/usr/include/libdasm/examples
  rsync -a ./examples $pkgdir/usr/include/libdasm/examples
  install -Dm644 LICENSE "$pkgdir"/usr/share/licenses/$pkgname/LICENSE
  python2 ./pydasm/setup.py install --root="$pkgdir" --optimize=1

  cd $pkgdir/usr/lib/
  ln -s libdasm.so libdasm.so.1.0
 
}
# vim:set ts=2 sw=2 et:
