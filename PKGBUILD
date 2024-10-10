# Maintainer: Knut Ahlers <knut at ahlers dot me>

pkgname=babel-eslint-plugin
pkgver=7.25.8
pkgrel=1
pkgdesc='@babel/eslint-parser allows you to lint ALL valid Babel code with the fantastic ESLint'
arch=('any')
url='https://github.com/babel/babel'
license=('MIT')
depends=('eslint')
makedepends=('npm')
source=("https://registry.npmjs.org/@babel/eslint-parser/-/eslint-parser-${pkgver}.tgz")
sha256sums=('b3e54660e938dfc76b8fd284b05080f07a140151466c7b4293dfb807dbe6de9f')
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
