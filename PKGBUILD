# Maintainer: Nate Nygren <nate.nygren at gmail dot com>
pkgname=sgminer-git
pkgver=4.1.153.r59.gaa471a2
pkgrel=1
pkgdesc="A multi-threaded multi-pool GPU miner for scrypt-based coins."
arch=('i686' 'x86_64')
url="https://github.com/veox/sgminer"
license=('GPL3')
depends=('curl' 'libcl' 'jansson')
conflicts=('sgminer')
makedepends=('opencl-headers' 'pkg-config' 'libtool' 'git')
optdepends=('ncurses: For ncurses formatted screen output'
            'opencl-nvidia: OpenCL implementation for NVIDIA'
            'opencl-catalyst: OpenCL implementation for AMD')
provides=('sgminer')
source=('git+https://github.com/veox/sgminer.git')
md5sums=('SKIP')

pkgver() {
  cd "$srcdir/sgminer"
  # Use the tag of the last commit
  git describe --long | sed -E 's/([^-]*-g)/r\1/;s/-/./g'
}



build() {
    cd "$srcdir/sgminer"
    ./autogen.sh
    CFLAGS="-O2 -Wall -march=native"
    ./configure
    make
}

package() {
    cd "$srcdir/sgminer"
    make DESTDIR="$pkgdir" install
    
}
