# Maintainer:   Lucky <archlinux@builds.lucky.li>
# Contributor:  Thomas Haider <t.haider@deprecate.de>

pkgname=bley-git
_pkgname="${pkgname%-*}"
pkgver=2.0.0.r0.g368a216
pkgrel=1
pkgdesc="Intelligent greylisting daemon for Postfix and Exim"
url="http://bley.mx"
license=("BSD")
arch=("any")
depends=("python2" "python2-ipaddr" "python2-publicsuffix" "python2-pydns" "python2-pyspf" "python2-twisted")
optdepends=("postfix: mail server (Message Transfer Agent)"
            "exim: mail server (Message Transfer Agent)"
            "sqlite: required for SQLite support"
            "python2-psycopg2: required for PostgreSQL support"
            "mysql-python: required for MySQL support"
            "python2-matplotlib: required for bleygraph")
makedepends=("git" "python2-distribute")
provides=("${_pkgname}")
conflicts=("${_pkgname}")
install="${_pkgname}.install"
source=("git://github.com/evgeni/bley.git")
sha256sums=("SKIP")

pkgver() {
  cd "${srcdir}/${_pkgname}"
  git describe --long | sed -r "s#^${_pkgname}/##;s#([^-]*-g)#r\1#;s#-#.#g"
}

build() {
  cd "${srcdir}/${_pkgname}"
  python2 setup.py build
}

package() {
  cd "${srcdir}/${_pkgname}"
  python2 setup.py install --root="${pkgdir}" --optimize=1
}
