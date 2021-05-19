# Maintainer: Pichponereay NGOR <isaacjacksonreay at gmail dot com>

pkgname=google-classroom-nativefier
pkgver=1.1
pkgrel=1
pkgdesc="Google Classroom Desktop build with Nativefier"
arch=("any")
url='https://classroom.google.com/u/0/h'
license=("MIT")
depends=("npm" "nodejs")
optdepends=("libindicator-gtk3")
source=(
  "${pkgname}.png"
  "${pkgname}.desktop"
)
sha256sums=(
  "8240db876144232a24fadc68a2222b7ee94db58a0e929c9d99a3326aade5b2b5"
  "6485e9904212b139a7aa568cbb26e77a3b8b9ea0c4e529ab9c4c2a04ccd25c15"
)

prepare(){
  cd "${srcdir}"
  npm i -g nativefier
}

build() {
  cd "${srcdir}"
  
  nativefier \
    --name "Google Classroom" \
    --icon "${pkgname}.png" \
    --user-agent 'Mozilla/5.0 (X11; Linux x86_64; rv:89.0) Gecko/20100101 Firefox/89.0' \
    --verbose \
    --internal-urls "(.*?classroom\.google\.com.*?|.*?accounts\.google\.com.*?)" \
    --single-instance \
    "${url}"
}

package() {

  # install main file
  install -d -m755 "${pkgdir}"/opt
  cp -Rr "${srcdir}"/GoogleClassroom* "${pkgdir}"/opt/GoogleClassroom

  chmod +x "${pkgdir}"/opt/GoogleClassroom/GoogleClassroom

  # intall desktop Entry
  install -D -m644 "${pkgname}".desktop "${pkgdir}"/usr/share/applications/"${pkgname}".desktop

  # install icon
  install -D -m755 "${srcdir}"/"${pkgname}.png" "${pkgdir}"/usr/share/icons/GoogleClassroom/"${pkgname}.png"

}
