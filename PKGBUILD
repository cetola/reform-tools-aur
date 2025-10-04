# Maintainer: Stephano Cetola <stephano@cetola.net>
pkgname=reform-tools
pkgver=1.79
pkgrel=1
pkgdesc="MNT Reform system tools & helpers"
arch=('x86_64' 'aarch64')
url="https://source.mnt.re/reform/reform-tools"
license=('GPL3')


depends=(
  'python'
  'python-psutil'
  'i2c-tools'
)
optdepends=(
  'mtd-utils: for NAND flashing tools'
  'alsa-utils: for audio-related tools'
  'lm_sensors: for sensor monitoring'
  'ircii: for Reform chat/IRC tools'
  'pavucontrol: GUI mixer control (if using PulseAudio)'
)

source=(
  "git+https://source.mnt.re/reform/reform-tools.git#tag=$pkgver"
  'motd-full'
  'motd-rescue'
)
sha256sums=(
  'SKIP'
  '5df16d0ad47909ffc6a7a890d9814ec0749f13707f5343466264d4fbe2d46f1c'
  'f7986b5dce945a9dcc923bbc66db11f6f5cba1e78576873b644fadff4dc5ad8d'
)

build() {
  cd "$srcdir/reform-tools"
  make
}

package() {
  cd "$srcdir/reform-tools"

  # Binaries (from bin/)
  install -d "$pkgdir/usr/bin"
  install -m755 bin/* "$pkgdir/usr/bin/"


  install -Dm644 systemd/reform-hw-setup.service "$pkgdir/usr/lib/systemd/system/reform-hw-setup.service"

  # MOTD files
  install -Dm644 "$srcdir/motd-full"   "$pkgdir/etc/motd-full"
  install -Dm644 "$srcdir/motd-rescue" "$pkgdir/etc/motd-rescue"
}

