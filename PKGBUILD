# Contributor: Andrea Scarpino <andrea@archlinux.org>

pkgname=kdelibs-frameworks-git
pkgver=v4.11.95.r6016.g00b0db2
pkgrel=1
pkgdesc='The KDE Library (KDE Frameworks)'
arch=('i686' 'x86_64')
url='https://projects.kde.org/projects/kde/kdelibs'
license=('LGPL')
depends=('attica-kf5-git' 'phonon-qt5' 'libdbusmenu-qt5' 'qt5-svg'
         'qt5-x11extras' 'enchant' 'jasper' 'openexr' 'libutempter'
         'polkit-qt' 'docbook-xsl' 'qt5-webkit>=5.2.0rc1' 'shared-mime-info'
         'giflib' 'libxss' 'upower' 'udisks2')
makedepends=('extra-cmake-modules-git' 'git')
source=('git://anongit.kde.org/kdelibs#branch=frameworks')
md5sums=('SKIP')

pkgver() {
  cd kdelibs
  git describe --long | sed -E 's/([^-]*-g)/r\1/;s/-/./g'
}

prepare() {
  mkdir -p build
}

build() {
  export LD_LIBRARY_PATH=/opt/kf5/lib
  export PKG_CONFIG_PATH=/opt/kf5/lib

  cd build
  cmake ../kdelibs \
    -DCMAKE_BUILD_TYPE=Release \
		-DCMAKE_INSTALL_PREFIX=/opt/kf5 \
    -DSUPERBUILD=ON \
    -DLIB_INSTALL_DIR=lib \
    -DHUPNP_ENABLE=OFF
  make
}

package() {
  cd build
  make DESTDIR="${pkgdir}" install
}
