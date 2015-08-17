# Maintainer: Rozan Martin <rozan.martin@gmail.com>
pkgname=tboplayer-git
pkgver=1
pkgrel=20121230
pkgdesc="A GUI interface to control omxplayer for the Raspberry Pi"
arch=('arm' 'armv6h')
url="https://github.com/KenT2/tboplayer"
license=('custom')
depends=(omxplayer-git python2 python2-pexpect)
makedepends=(git)
_gitroot="https://github.com/KenT2/tboplayer.git"
_gitname="tboplayer"

build() {
  cd "$srcdir"
  msg "Connecting to GIT server...."
    if [ -d $_gitname ] ; then
    ( cd $_gitname && git pull ) || warning "Git pull 
failed!"
  else
    git clone --depth=1 $_gitroot 
  fi
  msg "GIT checkout done or server timeout"
  cd $_gitname
  sed -i -e "s|#![ ]*/usr/bin/env python$|#!/usr/bin/env python2|" tboplayer.py
}

package() {
  cd "$srcdir/$_gitname"
  install -D -m755 tboplayer.py "$pkgdir/usr/bin/tboplayer"
}
