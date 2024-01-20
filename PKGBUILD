# ORIGINAL PACKAGE
# Maintainer: Jonas Witschel <diabonas@archlinux.org>
# Contributor: Sven-Hendrik Haase <sh@lutzhaase.com>
# Contributor: Malte Rabenseifner <malte@zearan.de>
# Contributor: John Gerritse <reaphsharc@gmail.com>
#
# MODIFIED BY RED FIRE SOFTWARE ENTERTAINMENT FOR AZOS GNU/LINUX

pkgname=lsb-release
pkgver=2.0.r53.a86f885
_commit=a86f885597a91cd41837d706bf6a08d4c239a54b
pkgrel=1
pkgdesc="LSB version query program (Modified for AZOS GNU/Linux)"
arch=('any')
url="https://refspecs.linuxfoundation.org/lsb.shtml"
license=('GPL')
depends=('sh')
makedepends=('git')
source=("git+https://github.com/LinuxStandardBase/lsb-samples.git#commit=$_commit"
        'lsb-release'
        'lsb_release_description.patch'
        'lsb_release_make_man_page_reproducible.patch')
sha512sums=('SKIP'
            'SKIP'
            'SKIP'
            'SKIP')

pkgver() {
	cd lsb-samples/lsb_release/src
	printf "%s.r%s.%s" "$(grep -Po 'SCRIPTVERSION="\K[^"]*' lsb_release)" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

prepare() {
	cd lsb-samples/lsb_release/src
	patch -Np0 -i "$srcdir/lsb_release_description.patch"
	patch -Np1 -i "$srcdir/lsb_release_make_man_page_reproducible.patch"
}

build() {
	cd lsb-samples/lsb_release/src
	make
}

package() {
	cd lsb-samples/lsb_release/src
	install -Dm644 lsb_release.1.gz -t "$pkgdir/usr/share/man/man1"
	install -Dm755 lsb_release -t "$pkgdir/usr/bin"
	install -Dm644 "$srcdir/lsb-release" -t "$pkgdir/etc"
}
