# Maintainer: Pichponereay NGOR <isaacjacksonreay at gmail dot com>

pkgname=google-classroom-nativefier
pkgver=2.0
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
  "14c499875c6ac81eab06c09e8b2361fd349729d4e02966c8ea32460c88d45cd6"
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

  install -d -m755 "${pkgdir}/usr/bin"
  ln -sr "${pkgdir}/opt/GoogleClassroom/GoogleClassroom" "${pkgdir}/usr/bin/${pkgname}"

}
