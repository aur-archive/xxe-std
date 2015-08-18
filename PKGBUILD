# Maintainer: Andrzej Giniewicz <gginiu@gmail.com>
# Based on xxe package by: Otto Sabart <seberm@gmail.com>

pkgname=xxe-std
pkgver=3.5.2
pkgrel=3
pkgdesc="XMLmind XML Editor allows to edit large, complex, modular, XML documents. This package contains latest Standard Edition"
arch=('i686' 'x86_64')
url="http://www.xmlmind.com/xmleditor"
provides=('xxe')
conflicts=('xxe')
license=('custom')
depends=('java-runtime=6')
makedepends=('imagemagick' 'unzip' 'java-environment=6')
install=xxe.install
source=(http://www.xmlmind.com/archive/xmleditor/$pkgver/xxe-std-${pkgver//./_}.zip xxe.sh xxe.desktop)

md5sums=('199d5efaf723f3c295e7e81b97909765'
         'ccd373358e00dfcf8055067bc614ec39'
         '5665a6b917f6a79e94e09995e7ae63d1')

build() {
	cd "${srcdir}"
	mkdir "${pkgdir}"/opt
	mv xxe-std-${pkgver//./_} "${pkgdir}"/opt/xxe
	rm "${pkgdir}"/opt/xxe/bin/*.bat
	rm "${pkgdir}"/opt/xxe/bin/*.exe

	# switch to Java 6
	#sed 's/java/java6/' -i "${pkgdir}"/opt/xxe/bin/{xxe,rngvalid,csscheck,dtdvalid,xsdvalid,schvalid,deploywebstart,convertdoc,translatexxe}

	# license
	install -D -m644 "${pkgdir}"/opt/xxe/bin/legal/xxe-std.LICENSE "${pkgdir}"/usr/share/licenses/${pkgname}/LICENSE

	# logo and menu file
	mkdir -p "${pkgdir}"/usr/share/{applications,pixmaps}
	convert "${pkgdir}"/opt/xxe/bin/icon/xxe.tiff "${pkgdir}"/usr/share/pixmaps/xxe.png
	install    -m644 "${srcdir}"/xxe.desktop "${pkgdir}"/usr/share/applications/
	install -D -m755 "${srcdir}"/xxe.sh "${pkgdir}"/etc/profile.d/xxe.sh
}

