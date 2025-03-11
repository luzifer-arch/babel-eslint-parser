# Maintainer: Knut Ahlers <knut at ahlers dot me>

pkgname=babel-eslint-plugin
pkgver=7.26.10
pkgrel=1
pkgdesc='@babel/eslint-parser allows you to lint ALL valid Babel code with the fantastic ESLint'
arch=('any')
url='https://github.com/babel/babel'
license=('MIT')
depends=('eslint')
makedepends=('npm')
source=("https://registry.npmjs.org/@babel/eslint-parser/-/eslint-parser-${pkgver}.tgz")
sha256sums=('9989ba2d5c7aee4168520fba10e1c78e9ab00ed3775cbc7610448d9e1d41d5f9')
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
