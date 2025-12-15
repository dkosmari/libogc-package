_pkgname=libogc
_branch=devel
pkgname=${_pkgname}-dkosmari-git
pkgver=2.13.0.r15.gda3dd03f
pkgrel=1
pkgdesc='C library for GameCube and Wii targeting devkitPPC.'
arch=('any')
url='https://github.com/dkosmari/libogc'
license=('custom')
groups=('gamecube-dev' 'wii-dev')
depends=('devkitPPC>=r42' 'gamecube-tools' 'ppc-libmad')
options=(!buildflags !strip staticlibs)
conflicts=(${_pkgname})
provides=(${_pkgname})
source=("${_pkgname}::git+https://github.com/dkosmari/libogc.git#branch=${_branch}")

pkgver() {
    cd "${srcdir}/${_pkgname}"
    LIBOGC_VER=$(git describe --tags)
    LIBOGC_MAJOR=$(echo "$LIBOGC_VER" | sed "s/^v\([0-9]*\).*/\1/")
    LIBOGC_MINOR=$(echo "$LIBOGC_VER" | sed "s/^v[0-9]*\.\([0-9]*\).*/\1/")
    LIBOGC_PATCH=$(echo "$LIBOGC_VER" | sed "s/^v[0-9]*\.[0-9]*\.\([0-9]*\).*/\1/")
    LIBOGC_SUFFIX=$(echo "$LIBOGC_VER" | sed "s/^v[0-9]*\.[0-9]*\.[0-9]*-\(.*\)/\1/")
    printf "%d.%d.%d.r%s" "$LIBOGC_MAJOR" "$LIBOGC_MINOR" "$LIBOGC_PATCH" "${LIBOGC_SUFFIX/-/.}"
}

build() {
    cd "${srcdir}/${_pkgname}"
    make
}

package() {
    cd "${srcdir}/${_pkgname}"
    make install DESTDIR="${pkgdir}"
}

sha256sums=('SKIP')
