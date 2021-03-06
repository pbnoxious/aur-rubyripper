# Maintainer:
# Contributor: Alexander F Rødseth <xyproto@archlinux.org>
# Contributor: Maxime Gauduin <alucryd@gmail.com>
# Contributor: Dave Reisner <dreisner@archlinux.org>
# Contributor: Alexander Fehr <pizzapunk gmail com>

pkgname=rubyripper
pkgver=0.7.0rc2
pkgrel=11
pkgdesc='Secure audiodisc ripper'
arch=('any')
url='https://github.com/bleskodev/rubyripper'
license=('GPL3')
depends=('cdparanoia' 'gtk2' 'ruby-iconv')
# The configuration script will crash if ruby-gettext is installed without ruby-rake,
# ruby-gettex notes the dependency as optional.
optdepends=('ruby-gtk2: GTK+ GUI'
            'ruby-gettext: Localization support'
            'ruby-rake: Localization support'
            'cd-discid: Freedb support'
            'lame: MP3 encoding support'
            'vorbis-tools: Ogg Vorbis encoding support'
            'flac: FLAC encoding support'
            'wavegain: WAV ReplayGain support'
            'mp3gain: MP3 ReplayGain support'
            'vorbisgain: Ogg Vorbis ReplayGain support'
            'normalize: Normalization support'
            'cdrdao: Advanced TOC analysis')
source=("https://github.com/bleskodev/rubyripper/archive/v${pkgver}.tar.gz")
sha256sums=('977089c4a262936f9acf82ad1ab5932de97523ba31b61b5ccc1279a94eaea6ae')

prepare() {
  cd "${pkgname}-${pkgver}"
}

build() {
  cd "${pkgname}-${pkgver}"

  ./configure --prefix='/usr' --enable-{cli,gtk2} \
    --ruby="$(ruby -e 'v = RbConfig::CONFIG["vendorlibdir"] ; v["/usr"] = ""; puts v')"
}

package() {
  make DESTDIR="$pkgdir" -C "$pkgname-$pkgver" install
}

# vim: ts=2 sw=2 et:
