# Maintainer: Alex <shantanna(at)hotmail(dot)com>

_pkgbase=goodix-gf3208
pkgname=goodix-gf3208-dkms
pkgver=0.1
pkgrel=0
pkgdesc="Kernel module for Goodix GF3208 Fingerprint Sensor (DKMS)"
arch=('i686' 'x86_64')
license=('GPL2')
depends=('dkms' 'subversion' 'linux-headers')
conflicts=("${_pkgbase}")
#install=${pkgname}.install
source=("${_pkgbase}-${pkgver}::svn+https://github.com/yangyangnau/android_kernel_xiaomi_msm8937/tree/cm-13.0/drivers/fingerprint/goodix"
        'gf-external.patch')
md5sums=('SKIP'
         'SKIP')

prepare() {
  cd ${_pkgbase}-${pkgver}
  patch -N -p1 -i "${srcdir}"/gf-external.patch
}

package() {
  # Install
  msg2 "Starting make..."
  cd ${_pkgbase}-${pkgver}

	install -dm 755 ${pkgdir}/usr/src/
  # Copy sources (including Makefile)
  cp -r "${srcdir}/${_pkgbase}-${pkgver}" "${pkgdir}/usr/src/${_pkgbase}-${pkgver}"

  # Set name and version
  sed -e "s/@_PKGBASE@/${_pkgbase}/" \
      -e "s/@PKGVER@/${pkgver}/" \
      -i "${pkgdir}"/usr/src/${_pkgbase}-${pkgver}/dkms.conf

}
