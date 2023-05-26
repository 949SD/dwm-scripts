# Maintainer: David K david.dk949@gmail.com
pkgname=dwm-scripts
pkgver=unknown
pkgrel=0
pkgdesc="Scripts to be used with my build of dwm."
arch=('x86_64')
url="https://github.com/dk949/$pkgname"
license=('MIT')
provides=(
    'batnotify'
    'highestUsageProcess'
    'layout-check'
    'makebg'
    'picom-end'
    'picom-start'
    'try-connect'
    'turnoff'
    'update-variables'
)
source=("git+$url")
md5sums=() #autofill using updpkgsums
sha256sums=('SKIP')

pkgver() {
    ___DATE="$(git -C "$pkgname" log -1 --format='%cd' --date=format:'%F')"
    ___DATE_TIME="$___DATE 00:00"
    ___COMMIT_COUNT=$(git -C "$pkgname" rev-list --count HEAD --since="$___DATE_TIME")
    echo "$(date -d "$___DATE" +'%Y%m%d')_$___COMMIT_COUNT"
    unset ___DATE
    unset ___DATE_TIME
    unset ___COMMIT_COUNT
}

build() {
    cd "$pkgname"
    make -j
}

package() {
    cd "$pkgname"

    make DESTDIR="$pkgdir/" PREFIX="/usr" install
    install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
