# SPDX-License-Identifier: AGPL-3.0

#    ----------------------------------------------------------------------
#    Copyright © 2024, 2025  Pellegrino Prevete
#
#    All rights reserved
#    ----------------------------------------------------------------------
#
#    This program is free software: you can redistribute it and/or modify
#    it under the terms of the GNU Affero General Public License as published by
#    the Free Software Foundation, either version 3 of the License, or
#    (at your option) any later version.
#
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU Affero General Public License for more details.
#
#    You should have received a copy of the GNU Affero General Public License
#    along with this program.  If not, see <https://www.gnu.org/licenses/>.

# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>

_offline="false"
_git="false"
_proj="hip"
pkgname=termux-shortcuts-utils
pkgver="0.0.0.0.0.0.0.0.0.1"
_commit="4e6905bf79361204921879210f305c8f61e748f4"
pkgrel=1
_pkgdesc=(
  "Termux shortcuts utilities."
)
pkgdesc="${_pkgdesc[*]}"
arch=(
  'any'
)
_http="https://github.com"
_ns="themartiancompany"
url="${_http}/${_ns}/${pkgname}"
group=(
 "${_proj}"
)
license=(
  'AGPL3'
)
depends=(
  "findutils"
  "libcrash-bash"
)
_os="$( \
  uname \
    -o)"
optdepends=(
)
[[ "${_os}" != "GNU/Linux" ]] && \
[[ "${_os}" == "Android" ]] && \
  optdepends+=(
  )
makedepends=(
  'make'
)
checkdepends=(
  "shellcheck"
)
source=()
sha256sums=()
validpgpkeys=()
_url="${url}"
_tag="${_commit}"
_tag_name="commit"
_tarname="${pkgname}-${_tag}"
[[ "${_offline}" == "true" ]] && \
  url="file://${HOME}/${pkgname}"
if [[ "${_git}" == true ]]; then
  makedepends+=(
    "git"
  )
  source+=(
    "${_tarname}::git+${_url}#${_tag_name}=${_tag}?signed"
  )
  sha256sums+=(
    SKIP
  )
  validpgpkeys+=(
    # Truocolo <truocolo@aol.com>
    '97E989E6CF1D2C7F7A41FF9F95684DBE23D6A3E9'
  )
elif [[ "${_git}" == false ]]; then
  if [[ "${_tag_name}" == 'pkgver' ]]; then
    _tar="${_tarname}.tar.gz::${_url}/archive/refs/tags/${_tag}.tar.gz"
    _sum='b245547bdcdbfeb09f400305a4b515b6d49635be90f560a39302761fc2688571'
  elif [[ "${_tag_name}" == "commit" ]]; then
    _tar="${_tarname}.zip::${_url}/archive/${_commit}.zip"
    _sum='529d4045aa6d050f712a50d81dc740afcce934040c92a3ccd53be1aa1322f6ae'
  fi
  source+=(
    "${_tar}"
  )
  sha256sums+=(
    "${_sum}"
  )
fi

check() {
  cd \
    "${_tarname}"
  make \
    -k \
    check
}

package() {
  cd \
    "${_tarname}"
  make \
    PREFIX="/usr" \
    DESTDIR="${pkgdir}" \
    install
  install \
    -Dm644 \
    "COPYING" \
    "${pkgdir}/usr/share/licenses/${pkgname}/COPYING"
}

# vim: ft=sh syn=sh et
