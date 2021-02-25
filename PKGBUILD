# Maintainer: Pichponereay NGOR <isaacjacksonreay at gmail dot com>

pkgname=google-classroom-nativefier
pkgver=1.0
pkgrel=1
pkgdesc="Google Classroom Desktop build with Nativefier"
arch=("any")
url='https://classroom.google.com/?emr=0'
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
    --user-agent 'Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:70.0) Gecko/20100101 Firefox/70.0' \
    --verbose \
    "${url}"
}

package() {
  mkdir -p "${pkgdir}"/opt
  mkdir -p "${pkgdir}"/usr/share/applications
  mkdir -p "${pkgdir}"/usr/share/icons/GoogleClassroom
  mv "${srcdir}"/GoogleClassroom* "${pkgdir}"/opt/GoogleClassroom
  mv "${pkgname}".desktop "${pkgdir}"/usr/share/applications
  mv "${srcdir}"/"${pkgname}.png" "${pkgdir}"/usr/share/icons/GoogleClassroom
  chmod +x "${pkgdir}"/opt/GoogleClassroom/GoogleClassroom
}
