# Maintainer: Pierre Marsais <pim@lse.epita.fr>
pkgname=man-intrinsics-git
pkgrel=1
pkgver=r50.4e25ed1
pkgdesc="man pages from Intel Intrinsics Guide"
arch=('x86_64')
url=""
license=('GPL')
groups=()
depends=()
makedepends=('git' 'wget' 'python2')
provides=("${pkgname%-git}")
conflicts=("${pkgname%-git}")
replaces=()
options=()
install=
source=('git+https://github.com/WojciechMula/man-intrinsics.git')
sha256sums=('SKIP')

pkgver() {
	cd "$srcdir/${pkgname%-git}"
	printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
	cd "$srcdir/${pkgname%-git}"
	make download
}

package() {
	cd "$srcdir/${pkgname%-git}"
	mkdir -p "$pkgdir/usr/share/man/man7"
	python2 ./main.py -g data-latest.xml -u instructions.xml -o "$pkgdir/usr/share/man/man7"
}
