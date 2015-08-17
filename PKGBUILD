# Maintainer: Anthony Cornehl <accornehl@gmail.com>
# https://github.com/twinshadow/openstack-aur

_realpkgname="novaclient"
pkgname="python2-${_realpkgname}-git"
pkgdesc="OpenStack Nova API Python bindings"
pkgver=0.0.0
pkgrel=1
conflicts=("python2-${_realpkgname}", "${_realpkgname}")
provides=("python2-${_realpkgname}")
arch=("any")
license=("custom")
url="https://github.com/openstack/python-${_realpkgname}"
depends=(
    "python2"
    "python2-babel"
    "python2-iso8601"
    "python2-prettytable"
    "python2-requests"
    "python2-simplejson"
    "python2-six"
)
makedepends=(
    "python2-setuptools"
    "git"
)
source=("$pkgname"::"git+https://github.com/openstack/python-${_realpkgname}")
md5sums=("SKIP")

pkgver() {
  cd "$pkgname"
  local ver="$(git describe --long)"
  printf "%s" "${ver//-/.}"
}

build() {
  cd "$pkgname"
  python2 setup.py build
}

package() {
  cd "$pkgname"
  python2 setup.py install --root="$pkgdir" --optimize=1
  install -Dm644 LICENSE "$pkgdir/usr/share/licenses/${_realpkgname}/LICENSE"
}
