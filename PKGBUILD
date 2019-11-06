# Maintainer: Jan Houben <jan@nexttrex.de>
# Contributor: Jesus Alvarez <jeezusjr at gmail dot com>
#
# This PKGBUILD was generated by the archzfs build scripts located at
#
# http://github.com/archzfs/archzfs
#
pkgname="zfs-dkms"
pkgdesc="Kernel modules for the Zettabyte File System."

pkgver=0.8.2
pkgrel=1
makedepends=()
arch=("x86_64")
url="https://zfsonlinux.org/"
source=("https://github.com/zfsonlinux/zfs/releases/download/zfs-${pkgver}/zfs-${pkgver}.tar.gz")
sha256sums=("47608e257c8ecebb918014ef1da6172c3a45d990885891af18e80f5cc28beab8")
license=("CDDL")
depends=("zfs-utils=${pkgver}" "lsb-release" "dkms")
provides=("zfs" "zfs-headers" "spl" "spl-headers")
groups=("archzfs-dkms")
conflicts=("zfs" "zfs-headers" "spl" "spl-headers")
replaces=("spl-dkms")

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
