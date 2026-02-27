# Maintainer: Elppans <elppansmk@*>
# shellcheck disable=all

pkgname=paclean
pkgver=1.0.0
pkgrel=1
arch=('any')
license=('MIT')
depends=('pacman')
provides=("$pkgname")
conflicts=("$pkgname")
pkgdesc="Keep the system clean (Equivalent to apt autoremove)"
url="https://github.com/elppans/${pkgname}"
source=("git+${url}.git#branch=main")
sha256sums=('SKIP')

# Automatically detect and use the correct install file
# if [ -e "${pkgname}.install" ]; then
	# install=${pkgname}.install
# elif [ -e "pkgbuild.install" ]; then
# 	install=pkgbuild.install
# fi

prepare() {
	pwd
	if [ -d "${srcdir}/${pkgname}" ]; then
	cd "${srcdir}/${pkgname}"
	# Determine the correct source directory
	if [ -d "${pkgname}" ]; then
		srcdir="${srcdir}/${pkgname}/${pkgname}"
	else
		srcdir="${srcdir}/${pkgname}"
	fi
	fi
	pwd

	echo "${pkgname}"
	echo "${srcdir}"

	# Add any preparation steps here, if needed
	# For example: patch -p1 < "${srcdir}/patch-file.patch"
}

package() {

	# Install files
	local dirs=("usr")
	for dir in "${dirs[@]}"; do
		if [ -d "${srcdir}/${dir}" ]; then
			cp -a "${srcdir}/${dir}" "${pkgdir}/"
		fi
	done

	# Install license file if present
	if [ -f "LICENSE" ]; then
		install -Dm644 LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
	fi

	# Install documentation if present
	if [ -f "README.md" ]; then
		install -Dm644 README.md "${pkgdir}/usr/share/doc/${pkgname}/README.md"
	fi
}
# cat > "${pkgname}.install" <<EOF
# post_install() {
# 	cat <<END

# O pacote foi instalado com sucesso...

# END
# }

# post_upgrade() {
#     post_install
# }

# post_remove() {

# 	cat <<END

# O "pacote" foi removido.

# END
# }
# EOF

