# Maintainer: BlackIkeEagle <ike DOT devolder AT gmail DOT com>
# Contributor: TZ86

pkgname=vivaldi-snapshot
pkgver=1.5.651.10
pkgrel=1
pkgdesc='An advanced browser made with the power user in mind. (weekly snapshot)'
url="https://vivaldi.com"
options=(!strip !zipman)
license=('custom')
arch=('i686' 'x86_64')
depends=('gtk2' 'nss' 'libxtst' 'gconf' 'libxss' 'freetype2' 'ttf-font' 'desktop-file-utils' 'shared-mime-info' 'alsa-lib' 'hicolor-icon-theme')
optdepends=(
    'vivaldi-snapshot-ffmpeg-codecs: playback of proprietary video/audio'
    'google-chrome: Widevine DRM Plugin'
    'vivaldi-widevine: Widevine DRM Plugin'
)
source_i686=("https://downloads.vivaldi.com/snapshot/vivaldi-snapshot-${pkgver}-1.i386.rpm")
source_x86_64=("https://downloads.vivaldi.com/snapshot/vivaldi-snapshot-${pkgver}-1.x86_64.rpm")
sha256sums_i686=('69443403f189f0b18d69cc0e7ca3734b699a76c8a6bbf5112bf6afad14cb8267')
sha256sums_x86_64=('18eedd250d19d663d0b981a71de0dffd52906694fa50c80eac8a8e8906433388')

package() {
    cp -a {opt,usr} "$pkgdir"

    # suid sanbox
    chmod 4755 "$pkgdir/opt/vivaldi-snapshot/vivaldi-sandbox"

    # make /usr/bin/vivaldi-snapshot available
    binf="$pkgdir/usr/bin/vivaldi-snapshot"
    if [[ ! -e "$binf" ]] && [[ ! -f "$binf" ]] && [[ ! -L "$binf" ]]; then
        install -dm755 "$pkgdir/usr/bin"
        ln -s /opt/$pkgname/$pkgname "$binf"
    fi

    # install icons
    for res in 16 22 24 32 48 64 128 256; do
        install -Dm644 "$pkgdir/opt/vivaldi-snapshot/product_logo_${res}.png" \
            "$pkgdir/usr/share/icons/hicolor/${res}x${res}/apps/vivaldi-snapshot.png"
    done
}

