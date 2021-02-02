# Maintainer krr
pkgname=nintendo-switch-meta-openrc
pkgver=1
pkgrel=1
pkgdesc='OpenRC meta-package that provides some init scripts and  a custom script'
arch=('aarch64')
url=https://github.com/atlasflamer/ARMtix-NX
source=($pkgname'::git+https://github.com/atlasflamer/ARMtix-NX.git')
md5sums=('SKIP')
_bc=switchroot-pre-config-but-cooler
pkgver(){
	cd ${srcdir}/${pkgname} && 	printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}
package(){
	install -Dm666 $srcdir/$pkgname/custom-scripts/${_bc}\
		"$pkgdir/usr/bin/${_bc}"
	cd $srcdir/$pkgname/openRC-initscripts/
	install -Dm755 joycond "$pkgdir/etc/init.d/joycond"
   	install -Dm755 r2p "$pkgdir/etc/init.d/r2p"
	install -Dm755 ${_bc}\
	  	"$pkgdir/etc/init.d/${_bc}"
}
post_install(){
	groupadd -rf debug

	#aka systemD vaccum
	cd /etc/systemd/
	rm nv.sh nv-oem-* nvfb* nvmem* nvweston* nvzram* 
	cd system 
   	rm apt-* nv-oem* r2p.service switchroot-pre-config.service joycond.service nvfb.service\
	   	nvfb-early.service nv.service nvmemwarning.service ncweston.service nvzramconfig.service
}
