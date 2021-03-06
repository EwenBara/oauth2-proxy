# Maintainer: Ewen BARA <ewen.bara@gmail.com>

pkgname=oauth2-proxy
pkgver=7.0.1
pkgrel=1
pkgdesc="A reverse proxy and static file server that provides authentication using Providers (Google, GitHub, and others) to validate accounts by email, domain or group."
arch=('x86_64')
url="https://oauth2-proxy.github.io/oauth2-proxy/"
license=('MIT')
makedepends=('go')
source=("${pkgname}-${pkgver}.tar.gz::https://github.com/oauth2-proxy/oauth2-proxy/archive/v${pkgver}.tar.gz")
sha512sums=('4784b5fff4a382829586246da8865366339d832224038ce085130db0ba54a72bbffa5bbc25867d7230709979389259489330739c87f5a6439d39d5cae63afb60')

export CGO_CPPFLAGS="${CPPFLAGS}"
export CGO_CFLAGS="${CFLAGS}"
export CGO_CXXFLAGS="${CXXFLAGS}"
export CGO_LDFLAGS="${LDFLAGS}"
export GOFLAGS="-buildmode=pie -trimpath -ldflags=-linkmode=external -mod=readonly -modcacherw"

export GOOS='linux'
export GOARCH='amd64'
export XC_OSARCH='linux/amd64'

prepare() {
  cd "${pkgname}-${pkgver}"
  mkdir -p build
}

build() {
  cd "${pkgname}-${pkgver}"
  go build -o build './...'
}

package() {
  cd "$pkgname-$pkgver"
  install -Dm755 build/$pkgname "$pkgdir"/usr/bin/$pkgname
}

# vim:set ts=2 sw=2 et:
