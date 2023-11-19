# ORIGINAL PACKAGE:
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
pkgdesc="LSB version query program (Modified for AZOS GNU/Linux"
arch=('any')
url="https://refspecs.linuxfoundation.org/lsb.shtml"
license=('GPL')
depends=('sh')
makedepends=('git')
source=("git+https://github.com/RedFireSoftwareEntertainment/lsb-release-azos.git"
        'lsb-release'
        'lsb_release_description.patch'
        'lsb_release_make_man_page_reproducible.patch')
sha512sums=('SKIP'
            '00aa1161330db06b2efe7081caa0a4b8a30339d542f6e3159e961bf1ede72873504c8f731e0e192958349bc4f8b9372a0254ba9f617060b735b8cac02e9c3f68'
            '145ef64f90f5e6cc59075679e640cf7c1ad02617c12eff17f10b05c1cc219591fdba1b27be2b2c8480742aed24ce81d6a7badcbaca6772faea4ebc6a55695b62'
            'ab64a1d236d00a30a48e3af2c5bdfa0aad0183ebe0df4f2b0c6af58530c2a1fdac1b0a5cdd8a1800d5f8405f44562603cddf28eb318b5badaabd49a82e0b7e83')

pkgver() {
	cd src
	printf "%s.r%s.%s" "$(grep -Po 'SCRIPTVERSION="\K[^"]*' lsb_release)" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

prepare() {
	cd src
	patch -Np0 -i "$srcdir/lsb_release_description.patch"
	patch -Np1 -i "$srcdir/lsb_release_make_man_page_reproducible.patch"
}

build() {
	cd src
	make
}

package() {
	cd src
	install -Dm644 lsb_release.1.gz -t "$pkgdir/usr/share/man/man1"
	install -Dm755 lsb_release -t "$pkgdir/usr/bin"
	install -Dm644 "$srcdir/lsb-release" -t "$pkgdir/etc"
}
