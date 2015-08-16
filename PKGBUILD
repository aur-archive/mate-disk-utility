# Maintainer : Martin Wimpress <code@flexion.org>

pkgname=mate-disk-utility
pkgver=1.6.1
pkgrel=2
pkgdesc="Disk management application for MATE."
url="https://github.com/NiceandGently/mate-disk-utility"
arch=('i686' 'x86_64' 'armv6h' 'armv7h')
license=('GPL')
depends=('avahi' 'dbus' 'gtk2' 'gobject-introspection' 'libatasmart' 'libnotify' 'libunique'
         'mate-file-manager' 'mate-keyring' 'udisks')
makedepends=('mate-common' 'mate-doc-utils' 'perl-xml-parser')
options=('!emptydirs')
source=("https://github.com/NiceandGently/${pkgname}/archive/v${pkgver}.tar.gz")
md5sums=('6354d83bb4c99fbbe27796fd939f43fe')
install=${pkgname}.install

build() {
    cd "${srcdir}/${pkgname}-${pkgver}"
    ./autogen.sh \
        --prefix=/usr \
        --sysconfdir=/etc \
        --libexecdir=/usr/lib/${pkgname} \
        --enable-mate-keyring \
        --disable-static \
        --disable-scrollkeeper
    make
}

package() {
    cd "${srcdir}/${pkgname}-${pkgver}"
    make DESTDIR="${pkgdir}" install
    rm -f "${pkgdir}/usr/lib/"*.a
}
