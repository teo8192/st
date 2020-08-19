# The following guidelines are specific to BZR, GIT, HG and SVN packages.
# Other VCS sources are not natively supported by makepkg yet.

# Maintainer: Teodor Dahl Knutsen <teodor@dahlknutsen.no>
pkgname='st-git' # '-bzr', '-git', '-hg' or '-svn'
pkgver=0.8.3
pkgrel=1
pkgdesc="A simple X terminal."
arch=('x86_64')
url="https://github.com/teo8192/st.git"
license=('MIT')
groups=()
depends=('libxft')
makedepends=('git') # 'bzr', 'git', 'mercurial' or 'subversion'
provides=("${pkgname%-git}")
conflicts=("${pkgname%-git}")
install=
source=('dwm::git://github.com/teo8192/st.git')
# source=('FOLDER::VCS+URL#FRAGMENT')
noextract=()
md5sums=('SKIP')

# Please refer to the 'USING VCS SOURCES' section of the PKGBUILD man page for
# a description of each element in the source array.

pkgver() {
	cd "$srcdir/${pkgname%-git}"

# The examples below are not absolute and need to be adapted to each repo. The
# primary goal is to generate version numbers that will increase according to
# pacman's version comparisons with later commits to the repo. The format
# VERSION='VER_NUM.rREV_NUM.HASH', or a relevant subset in case VER_NUM or HASH
# are not available, is recommended.
# Git, no tags available
	printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

# prepare() {
# 	cd "$srcdir/${pkgname%-VCS}"
# 	patch -p1 -i "$srcdir/${pkgname%-VCS}.patch"
# }

build() {
	cd "$srcdir/${pkgname%-git}"
	# ./autogen.sh
	# ./configure --prefix=/usr
	make
}

# check() {
# 	cd "$srcdir/${pkgname%-git}"
# 	make -k check
# }

# package() {
# 	cd "$srcdir/${pkgname%-git}"
# 	# make install
# 	# install -Dm755 ./${pkgname%-git} "usr/bin/${pkgname%-git}"
# 	# install -Dm644 ./${pkgname%-git}.1 "usr/share/man/man1"

# 	# sed "s/VERSION/${VERSION}/g" < dwm.1 > ${DESTDIR}${MANPREFIX}/man1/dwm.1
# 	# chmod 644 ${DESTDIR}${MANPREFIX}/man1/dwm.1
# 	# make install
# }

package() {
	cd "$srcdir/${pkgname%-git}"
	make DESTDIR="$pkgdir/" PREFIX="usr/" install
}
