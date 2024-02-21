# Maintainer: Evan Greenup <_>

_name=clash-compiler
pkgname=hx-clash-ghc
pkgver=1.8.1
pkgrel=1
pkgdesc="Haskell to VHDL/Verilog/SystemVerilog compiler, CAES Language for Synchronous Hardware"
url="https://clash-lang.org/"
license=("BSD-2-Clause")
arch=('x86_64')
provides=('pandoc' 'pandoc-cli')
conflicts=('pandoc' 'pandoc-cli')
replaces=('pandoc' 'pandoc-cli')
depends=()
makedepends=('stack')
source=("${_name}-${pkgver}.tar.gz::https://github.com/clash-lang/${_name}/archive/refs/tags/v${pkgver}.tar.gz")
sha256sums=('2df4b708480486ade33e29aa4ea99be7bb23198596d96ececc2867c7e50e1ba7')

build() {
  cd "$srcdir/$_name-$pkgver"

  stack build clash-ghc:exe:clash
  stack build clash-ghc:exe:clashi
}

check() {
  cd "$srcdir/$_name-$pkgver"

  stack test clash-ghc:exe:clash
  stack test clash-ghc:exe:clashi
}

package() {
  cd "$srcdir/$_name-$pkgver"
  mkdir -m755 -p "${pkgdir}/usr/bin/"
  install -m755 "$(stack path --local-install-root)/bin/clash" "${pkgdir}/usr/bin/clash"
  install -m755 "$(stack path --local-install-root)/bin/clashi" "${pkgdir}/usr/bin/clashi"
  install -D -m644 LICENSE -t "$pkgdir"/usr/share/licenses/$pkgname/
}
