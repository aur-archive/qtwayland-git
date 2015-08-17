# Maintainer: Pier Luigi Fiorini <pierluigi.fiorini@gmail.com>

pkgname=qtwayland-git
pkgver=0.0.0
pkgrel=1
pkgdesc="A cross-platform application and UI framework (QtWayland)"
arch=('i686' 'x86_64')
url="http://qt-project.org/"
license=('GPL3' 'LGPL')
depends=('qtbase-git' 'qtdeclarative-git' 'libxcomposite' 'wayland')
makedepends=('git' 'gdb')
options=('!libtool' 'debug')
source=(git://gitorious.org/qt/qtwayland.git#branch=stable)
md5sums=('SKIP')

pkgver() {
  cd qtwayland
  git describe --always | sed 's|-|.|g'
}

prepare() {
  cd qtwayland
}

build() {
  cd qtwayland
  /opt/qt-git/bin/qmake CONFIG+=wayland-compositor
  make
}

package() {
  cd qtwayland
  make INSTALL_ROOT="${pkgdir}" install

  # Workaround to install generated private headers
  cp ./include/QtCompositor/5.3.0/QtCompositor/private/{qwayland-server-*,*protocol*}.h \
      ${pkgdir}/opt/qt-git/include/QtCompositor/5.3.0/QtCompositor/private/
}
