# Maintainer: Jan Houben <jan@nexttrex.de>
# Contributor: Jesus Alvarez <jeezusjr at gmail dot com>
#
# This PKGBUILD was generated by the archzfs build scripts located at
#
# http://github.com/archzfs/archzfs
#
pkgname="zfs-dkms"
pkgdesc="Kernel modules for the Zettabyte File System."

pkgver=0.8.4
pkgrel=1
makedepends=()
arch=("x86_64")
url="https://zfsonlinux.org/"
source=("https://github.com/zfsonlinux/zfs/releases/download/zfs-${pkgver}/zfs-${pkgver}.tar.gz"
        "linux-5.8-compat-__vmalloc.patch"
)
sha256sums=("2b988f5777976f09d08083f6bebf6e67219c4c4c183c1f33033fb7e5e5eacafb"
            "264728b1e4f7f7509fde76b6049c93033aa813ae6324f37609ff95db8c9e8959"
)
license=("CDDL")
depends=("zfs-utils=${pkgver}" "lsb-release" "dkms")
provides=("zfs" "zfs-headers" "spl" "spl-headers")
groups=("archzfs-dkms")
conflicts=("zfs" "zfs-headers" "spl" "spl-headers")
replaces=("spl-dkms")
prepare() {
    cd "${srcdir}/zfs-${pkgver}"
    patch -Np1 -i ${srcdir}/linux-5.8-compat-__vmalloc.patch
}

build() {
    cd "${srcdir}/zfs-${pkgver}"
    ./autogen.sh
}

package() {
    dkmsdir="${pkgdir}/usr/src/zfs-${pkgver}"
    install -d "${dkmsdir}"
    cp -a ${srcdir}/zfs-${pkgver}/. ${dkmsdir}
    cd "${dkmsdir}"
    find . -name ".git*" -print0 | xargs -0 rm -fr --
    scripts/dkms.mkconf -v ${pkgver} -f dkms.conf -n zfs
    chmod g-w,o-w -R .
}
