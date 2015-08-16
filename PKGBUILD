# Maintainer: Karol 'Kenji Takahashi' Wozniak <wozniakk@gmail.com>

pkgname=mpristester-git
pkgver=20130302
pkgrel=1
pkgdesc="A developer tool for testing the MPRIS interface of media players"
arch=('i686' 'x86_64')
url="https://github.com/randomguy3/mpristester"
license=('GPL')
depends=('qt4')
makedepends=('git')
provides=('mpristester')
source=()
md5sums=()

_gitroot=https://github.com/randomguy3/mpristester.git
_gitname=mpristester

build() {
    cd "$srcdir"
    msg "Connecting to GIT server...."

    if [[ -d "$_gitname" ]]; then
        cd "$_gitname" && git pull origin
        msg "The local files are updated."
    else
        git clone "$_gitroot" "$_gitname"
    fi

    msg "GIT checkout done or server timeout"
    msg "Starting build..."

    cd "$srcdir/$_gitname"
    qmake-qt4 mpristester.pro
    make
}

package() {   
    install -d -m755 ${pkgdir}/usr/bin
    install -D -m755 ${srcdir}/${_gitname}/mpristester ${pkgdir}/usr/bin/
}

# vim:set ts=4 sw=4 et:

