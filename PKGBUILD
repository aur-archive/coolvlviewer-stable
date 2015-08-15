# Maintainer: GordonGR <gordongr@freemail.gr>

pkgname=coolvlviewer-stable
pkgver=1.26.4.23
pkgrel=1
pkgdesc="The Cool VL Viewer (formerly known as 'Cool SL Viewer') is a third-party viewer for Second Life (C) (secondlife) and OpenSim (opensimulator) grids. In the name, 'VL' stands for virtual life (native 32bit, binary)"
url="http://sldev.free.fr"
license=('custom')
depends=('apr-util' 'gtk2' 'libpng' 'libgl' 'libjpeg6' 'libidn' 'sdl' 'mesa')
optdepends=('nvidia-utils: GL support for NVIDIA drivers' 'libpulse: for PulseAudio support' 'alsa-lib: for ALSA support' 'gstreamer0.10: For video support, may need good, bad and ugly plugins' 'freealut: For OpenAL support')
[ "$CARCH" = "x86_64" ] && depends=('lib32-gtk2' 'lib32-libpng' 'lib32-libidn' 'lib32-sdl' 'lib32-mesa')
[ "$CARCH" = "x86_64" ] && optdepends=('lib32-nvidia-utils: GL support for NVIDIA drivers' 'lib32-libpulse: for PulseAudio support' 'lib32-alsa-lib: for ALSA support' 'lib32-freealut: For OpenAL support')
arch=('i686' 'x86_64')
conflicts=('coolvlviewer-experimental')
install=coolvlviewer.install
source=("http://sldev.free.fr/binaries/CoolVLViewer-${pkgver}-Linux-x86-Setup"
        "coolvlviewer.desktop"
        "coolvlviewer.launcher")
        
md5sums=('6aad03c80a512932fbf675bbd2aa9da7'
         'd09508e9641ea75f5fd5f5195802f4e2'
         'fd78de1f6c1333a5120ece89873515e0')

        
build() {
    cd $srcdir
    # Run the installer
    chmod +x CoolVLViewer-${pkgver}-Linux-x86-Setup
    ./CoolVLViewer-${pkgver}-Linux-x86-Setup --mode silent --destination $srcdir/coolvlviewer/
}

package(){
    # Install Desktop File
    install -D -m644 $srcdir/coolvlviewer.desktop \
        $pkgdir/usr/share/applications/coolvlviewer.desktop
 
    # Install Icon File
    install -D -m755 $srcdir/coolvlviewer/cvlv_icon.png \
        $pkgdir/usr/share/pixmaps/clvl_icon.png

    # Install Launcher
    install -D -m755 $srcdir/../coolvlviewer.launcher \
        $pkgdir/usr/bin/coolvlviewer
    # Install License
    install -D -m644 $srcdir/coolvlviewer/licenses.txt \
        $pkgdir/usr/share/licenses/$pkgname/LISENSE
    # Move Data to Destination Directory
    install -d $pkgdir/opt/
    mv coolvlviewer/ $pkgdir/opt/
}
