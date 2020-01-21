# Maintainer: Titux Metal <github@lgdweb.fr>
pkgname=archlinux-i3-config-titux
_pkgname=i3-config-archlinux
_destname1="/etc/skel/.config/"
_licensedir="/usr/share/licenses/${pkgname}/"
pkgver=r4.18e8331
pkgrel=1
pkgdesc="Personal configuration for i3 window manager. Based on arcolinux-i3wm: https://github.com/arcolinux/arcolinux-i3wm"
arch=('x86_64')
url="https://tituxmetal.github.io/archlinux-repo/x86_64"
license=('GPL3')
depends=('i3-gaps')
makedepends=('git')
provides=(${pkgname})
options=(!strip !emptydirs)
source=(${_pkgname}::"git+https://github.com/TituxMetal/${_pkgname}.git")
install='readme.install'
md5sums=('SKIP')

pkgver() {
  cd "$_pkgname"
  ( set -o pipefail
    git describe --long 2>/dev/null | sed 's/\([^-]*-g\)/r\1/;s/-/./g' ||
    printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
  )
}

package() {
	install -dm755 ${pkgdir}${_licensedir}${_pkgname}
	install -m644  ${srcdir}/${_pkgname}/LICENSE ${pkgdir}${_licensedir}

	install -dm755 ${pkgdir}${_destname1}
	cp -r  ${srcdir}/${_pkgname}${_destname1}* ${pkgdir}${_destname1}
}
