pkgname=grep
pkgver=3.12
pkgrel=2
pkgdesc="A string search utility"
arch=('x86_64')
url="https://www.gnu.org/software/grep/"
license=('GPL-3.0-or-later')
groups=('base' 'base-devel')
depends=(
    'bash'
    'glibc'
    'pcre2'
)
makedepends=(
    'gperf'
    'python'
    'texinfo'
)
source=(https://ftp.gnu.org/gnu/${pkgname}/${pkgname}-${pkgver}.tar.xz)
sha256sums=(2649b27c0e90e632eadcd757be06c6e9a4f48d941de51e7c0f83ff76408a07b9)

prepare() {
    cd ${pkgname}-${pkgver}

    sed -i "s/echo/#echo/" src/egrep.sh
}

build() {
    cd ${pkgname}-${pkgver}

    local configure_args=(
        ${configure_options}
    )

    ./configure "${configure_args[@]}"

    make
}

package() {
    cd ${pkgname}-${pkgver}

    make DESTDIR=${pkgdir} install
}
