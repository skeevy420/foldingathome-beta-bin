# Contributor: paul2lv [at] gmail dot com
# Maintainer: 

pkgname=foldingathome-beta-bin
pkgver=7.4.16
pkgrel=3
pkgdesc="Folding@Home is a distributed computing project which studies protein folding, misfolding, aggregation, and related diseases."
arch=('x86_64')
url="http://folding.stanford.edu/"
license=('CUSTOM')
depends=('glibc')
optdepends=('opencl-nvidia: for folding with an nVidia GPU'
	'opencl-mesa: for folding with an AMD GPU'
	'opencl-amd: for folding with an AMD GPU using OpenCL from AMDGPU-PRO with the AMDGPU driver')
replaces=('foldingathome-v7' 'foldingathome')
conflicts=('foldingathome-v7' 'foldingathome')
source=('foldingathomebeta.service'
        'https://folding.stanford.edu/releases/beta/release/fahclient/debian-stable-64bit/v7.4/fahclient_7.4.16-64bit-release.tar.bz2')
sha256sums=('f1c2a774b235298ed9c467317708397d50f9b1edfb743899dd72a61a51b1f793'
            'dade69e217697dd886a241c4400b9aaef0e16e66f510c33ddcde22cd098fec30')


package() {
  cd ${srcdir}

  install -D -c -m755 fahclient_${pkgver}-64bit-release/FAHClient ${pkgdir}/opt/fah-beta/FAHClient
  install -D -c -m755 fahclient_${pkgver}-64bit-release/FAHCoreWrapper ${pkgdir}/opt/fah-beta/FAHCoreWrapper
  install -D -c -m755 fahclient_${pkgver}-64bit-release/sample-config.xml ${pkgdir}/opt/fah-beta/sample-config.xml

  chmod 755 ${pkgdir}/opt/fah-beta/FAHClient
  chmod 755 ${pkgdir}/opt/fah-beta/FAHCoreWrapper
  install -D -m644 fahclient_${pkgver}-64bit-release/copyright ${pkgdir}/usr/share/licenses/${pkgname}/copyright
  install -D -m644 fahclient_${pkgver}-64bit-release/README.md ${pkgdir}/opt/fah-beta/README.md
  install -D -m644 fahclient_${pkgver}-64bit-release/CHANGELOG.md ${pkgdir}/opt/fah-beta/CHANGELOG.md
  install -D -m644 ${srcdir}/foldingathomebeta.service ${pkgdir}/usr/lib/systemd/system/foldingathomebeta.service
}

post_install() {
  cat << 'EOM'
  --> Please cd to /opt/fah-beta/ and execute ./FAHClient --configure
  --> as root to configure your settings. If you are using systemd, 
  --> then run "systemctl enable foldingathomebeta.service" to enable
  --> the folding service. If you would like join the Arch Linux
  --> team, use team number 45032.  
EOM
}
