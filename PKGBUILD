# Maintainer: Knut Ahlers <knut at ahlers dot me>

pkgname=babel-eslint-plugin
pkgver=7.25.0
pkgrel=1
pkgdesc='@babel/eslint-parser allows you to lint ALL valid Babel code with the fantastic ESLint'
arch=('any')
url='https://github.com/babel/babel'
license=('MIT')
depends=('eslint')
makedepends=('npm')
source=("https://registry.npmjs.org/@babel/eslint-parser/-/eslint-parser-${pkgver}.tgz")
sha256sums=('5649c8d8ca16ef226eb19c7b8b0370c4dcf72b23b1734fe76c1d078c85de08a4')
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
