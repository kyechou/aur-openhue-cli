# Maintainer: Kuan-Yen Chou <kuanyenchou@gmail.com>

pkgname=openhue-cli
pkgver=0.22.1
pkgrel=1
pkgdesc='CLI for interacting with Philips Hue smart lighting systems'
depends=()
optdepends=()
makedepends=('go')
arch=('x86_64')
url='https://www.openhue.io/cli/openhue-cli'
license=('Apache-2.0')
provides=('openhue')
source=("https://github.com/openhue/openhue-cli/archive/refs/tags/$pkgver.tar.gz")
sha256sums=('fb565545dde82ea1a4e5e227259a7a14d66e228f317497c13908d807c6635a84')

build() {
    export CGO_CPPFLAGS="${CPPFLAGS}"
    export CGO_CFLAGS="${CFLAGS}"
    export CGO_CXXFLAGS="${CXXFLAGS}"
    export CGO_LDFLAGS="${LDFLAGS}"
    export GOFLAGS="-buildmode=pie -trimpath -ldflags=-linkmode=external -mod=readonly -modcacherw"

    cd "$srcdir/$pkgname-$pkgver"
    mkdir -p build
    go build -o build ./...
}

check() {
    cd "$srcdir/$pkgname-$pkgver"
    go test ./...
}

package() {
    cd "$srcdir/$pkgname-$pkgver"
    install -Dm 755 "build/$pkgname" "$pkgdir/usr/bin/openhue"
}

# vim: set sw=4 ts=4 et:
