# Maintainer: Nissar Chababy <contact at funilrys dot com>
# Contributor: Luis Martinez <luis dot martinez at disroot dot org>

pkgname=python-box
pkgver=6.1.0
pkgrel=1
pkgdesc="Advanced Python dictionaries with dot notation access"
arch=('x86_64')
url="https://github.com/cdgriffith/Box"
license=('MIT')
depends=('python')
optdepends=(
	'python-msgpack'
	'python-ruamel-yaml: YAML support'
	'python-toml: TOML support'
	'python-yaml: YAML support')
makedepends=('cython' 'python-build' 'python-installer' 'python-setuptools' 'python-wheel')
source=("$pkgname-$pkgver.tar.gz::https://files.pythonhosted.org/packages/source/${pkgname::1}/${pkgname}/${pkgname}-${pkgver}.tar.gz")
sha256sums=('6e7c243b356cb36e2c0f0e5ed7850969fede6aa812a7f501de7768996c7744d7')

build() {
	cd "$pkgname-$pkgver"
	python -m build --wheel --no-isolation
}

package() {
	cd "$pkgname-$pkgver"
	PYTHONHASHSEED=0 python -m installer --destdir="$pkgdir/" dist/*.whl
	local _site="$(python -c 'import site; print(site.getsitepackages()[0])')"
	install -d "$pkgdir/usr/share/licenses/$pkgname/"
	ln -s \
		"$_site/${pkgname/-/_}-$pkgver.dist-info/LICENSE" \
		"$pkgdir/usr/share/licenses/$pkgname/"
}
