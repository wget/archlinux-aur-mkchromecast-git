# Maintainer: Térence Clastres <t dot clastres at gmail dot com>

pkgname=mkchromecast-git
_gitname=mkchromecast
pkgver=r1213.c046ba2f
pkgrel=1
pkgdesc="Cast Audio/Video to your Google Cast and Sonos Devices"
arch=('any')
url="http://mkchromecast.com"
license=('MIT')
depends=('faac' 'flac' 'lame' 'python-flask' 'python-gobject' 'python-psutil' 'pulseaudio-dlna'
         'sox' 'vorbis-tools')
optdepends=('alsa-utils: to cast with ALSA'
            'ffmpeg: for ffmpeg backend (which is also needed to cast with ALSA)'
            'gstreamer: for gstreamer backend'
            'pavucontrol: for parec backend or just to cast with PulseAudio'
            'pulseaudio: for parec backend or just to cast with PulseAudio'
            'python-pychromecast: to cast to Chromecast devices'
            'python-pyqt5: for system tray menu support'
            'python-soco: to cast to Sonos devices'
            'youtube-dl: for --youtube')
provides=('mkchromecast')
conflicts=('mkchromecast')
options=('!emptydirs')
source=("git+https://github.com/muammar/${_gitname}.git")
md5sums=('SKIP')

pkgver() {
	cd "${_gitname}"
	printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

package() {
   cd "${_gitname}"

  install -d "${pkgdir}/usr/bin/"
  install -d "${pkgdir}/usr/share/${_gitname}/"
  install -d "${pkgdir}/usr/share/${_gitname}/${_gitname}/getch/"
  install -d "${pkgdir}/usr/share/${_gitname}/images/"
  install -d "${pkgdir}/usr/share/${_gitname}/nodejs/"

  install -D -m755 bin/${_gitname} "${pkgdir}/usr/share/${_gitname}/${_gitname}.py"
  ln -s "/usr/share/${_gitname}/${_gitname}.py" "${pkgdir}/usr/bin/${_gitname}"

  install -D -m644 mkchromecast/*.py "${pkgdir}/usr/share/${_gitname}/${_gitname}/"
  install -D -m644 mkchromecast/getch/* "${pkgdir}/usr/share/${_gitname}/${_gitname}/getch/"
  install -D -m644 images/*.png "${pkgdir}/usr/share/${_gitname}/images/"
  install -D -m644 nodejs/html5-video-streamer.js "${pkgdir}/usr/share/${_gitname}/nodejs/"


  install -D -m644 "man/${_gitname}.1" "${pkgdir}/usr/share/man/man1/${_gitname}.1"
  install -D -m644 LICENSE "${pkgdir}/usr/share/licenses/${_gitname}/LICENSE"
  install -D -m644 "images/${_gitname}.xpm" "${pkgdir}/usr/share/pixmaps/${_gitname}.xpm"
  install -D -m644 "${_gitname}.desktop" "${pkgdir}/usr/share/applications/${_gitname}.desktop"
}
