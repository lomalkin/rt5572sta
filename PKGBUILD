# Mantainer: Marty Plummer <ntzrmtthihu777@gmail.com>
pkgname=('rt5572sta')
pkgver=('2.601')
pkgrel=1
pkgdesc='kernel module and firmware for DLink DWA-160 B2 wifi dongle'
arch=('any')
url=''
license=('GPL')
depends=('dkms' 'wpa_supplicant')
makedepends=('linux-headers')
conflicts=()
provides=()
options=('!strip')
install=$pkgname.install
source=(
	${pkgname}-${pkgver}.tar.bz2
	rt2870.zip
	${pkgname}-3.x-kernel.patch
	dkms.conf
)
md5sums=('14d79bedf6567a9c5205fd118d3ad763'
         'c5a93b466532a5617da6b203cabab62b'
         '6bae5f1c3e12583e1a7211616ca528cb'
         'e521adc1462b41c64308c39c250d6a04')

build() {
	cd ${srcdir}/
	mv DPO_RT5572_LinuxSTA_2.6.1.3_20121022 ${pkgname}-${pkgver}
	mv RT2870_Firmware_V22 rt2870
	cd ${pkgname}-${pkgver}
	patch -p2 < ../${pkgname}-3.x-kernel.patch
}

package() {
    mkdir -p ${pkgdir}/usr/src/
    cp -RL ${srcdir}/${pkgname}-${pkgver}/ ${pkgdir}/usr/src/
    cp -RL ${srcdir}/dkms.conf ${pkgdir}/usr/src/${pkgname}-${pkgver}
    mkdir -p ${pkgdir}/lib/firmware
    cp -RL ${srcdir}/rt2870/rt2870.bin ${pkgdir}/lib/firmware
}
