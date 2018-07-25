# Maintainer: Pierre Marsais <pim@lse.epita.fr>
pkgname=dns-git
pkgrel=1
pkgver=r12.8340c23
pkgdesc="A dns server"
arch=('x86_64')
url=""
license=('GPL')
groups=()
depends=()
makedepends=('git')
provides=("${pkgname%-git}")
conflicts=("${pkgname%-git}")
replaces=()
backup=()
options=()
install=
source=('dns::git+ssh://gitolite@git.pimzero.com:222/users/pim/my_dns.git'
        'dns.service')
sha256sums=('SKIP'
            '28e5f9ccf44ce056cba393aca6bc485d8d9de48be33836ddd93fcefc495cd46c')

pkgver() {
	cd "$srcdir/${pkgname%-git}"
	printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
	cd "$srcdir/${pkgname%-git}"
	make
}

package() {
	install -Dm 644 dns.service "$pkgdir/usr/lib/systemd/system/dns.service"

	cd "$srcdir/${pkgname%-git}"
	install -Dm 755 dns "$pkgdir/usr/bin/dns"
	install -Dm 644 example.conf "$pkgdir/etc/dns.conf"
}
