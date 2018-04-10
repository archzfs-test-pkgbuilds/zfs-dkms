# Maintainer: Jesus Alvarez <jeezusjr at gmail dot com>
#
# This PKGBUILD was generated by the archzfs build scripts located at
#
# http://github.com/archzfs/archzfs
#
#
pkgname="zfs-dkms"
pkgdesc="Kernel modules for the Zettabyte File System."

pkgver=0.7.8
pkgrel=1
makedepends=("git")
arch=("x86_64")
url="http://zfsonlinux.org/"
source=("https://github.com/zfsonlinux/zfs/releases/download/zfs-0.7.8/zfs-0.7.8.tar.gz")
sha256sums=("70ba0edd72914d4bfc9a9426cf26725e955a9509acbddb6902efb9eebb35f150")
license=("CDDL")
depends=("spl-dkms" "zfs-utils-common=0.7.8")
provides=("zfs")
groups=("archzfs-dkms")
conflicts=('zfs-dkms-git' 'zfs-archiso-linux' 'zfs-archiso-linux-git' 'zfs-linux-hardened' 'zfs-linux-hardened-git' 'zfs-linux-lts' 'zfs-linux-lts-git' 'zfs-linux' 'zfs-linux-git' 'zfs-linux-vfio' 'zfs-linux-vfio-git' 'zfs-linux-zen' 'zfs-linux-zen-git'  'zfs-archiso-linux-headers' 'zfs-archiso-linux-git-headers' 'zfs-linux-hardened-headers' 'zfs-linux-hardened-git-headers' 'zfs-linux-lts-headers' 'zfs-linux-lts-git-headers' 'zfs-linux-headers' 'zfs-linux-git-headers' 'zfs-linux-vfio-headers' 'zfs-linux-vfio-git-headers' 'zfs-linux-zen-headers' 'zfs-linux-zen-git-headers' )

build() {
    cd "${srcdir}/zfs-0.7.8"
    ./autogen.sh
}

package() {
    dkmsdir="${pkgdir}/usr/src/zfs-0.7.8"
    install -d "${dkmsdir}"
    cp -a ${srcdir}/zfs-0.7.8/. ${dkmsdir}
    cd "${dkmsdir}"
    find . -name ".git*" -print0 | xargs -0 rm -fr --
    scripts/dkms.mkconf -v 0.7.8 -f dkms.conf -n zfs
    chmod g-w,o-w -R .
}
