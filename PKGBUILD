# Maintainer: Knut Ahlers <knut at ahlers dot me>

pkgname=babel-eslint-plugin
pkgver=7.22.10
pkgrel=1
pkgdesc='@babel/eslint-parser allows you to lint ALL valid Babel code with the fantastic ESLint'
arch=('any')
url='https://github.com/babel/babel'
license=('MIT')
depends=('eslint')
makedepends=('npm')
source=("https://registry.npmjs.org/@babel/eslint-parser/-/eslint-parser-${pkgver}.tgz")
sha256sums=('f3624dcafe577897b255cb272844d349f9f79bccd7510a6d517422da62f6e6eb')
noextract=("eslint-parser-${pkgver}.tgz")

package() {
	install -dm 755 "$pkgdir/usr/lib"
	npm install -g --prefix "$pkgdir"/usr "$srcdir"/eslint-parser-${pkgver}.tgz

	# Fix permissions
	find "$pkgdir/usr" -type d -exec chmod 755 '{}' +

	# Remove files that conflict with `eslint`:
	rm -rf "$pkgdir/usr/lib/node_modules/eslint"
	rm -rf "$pkgdir/usr/bin"

	install -dm755 "${pkgdir}/usr/share/licenses/${pkgname}"
	ln -s ../../../lib/node_modules/@babel/eslint-parser/LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}
