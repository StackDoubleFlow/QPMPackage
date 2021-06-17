# Maintainer: StackDoubleFlow <ojaslandge@gmail.com>
pkgname=questpackagemanager-git
pkgver=0.1.0
pkgrel=1
pkgdesc="A package manager for making Quest il2cpp mods and libraries."
arch=('x86_64')
url="https://github.com/sc2ad/QuestPackageManager"
license=('GPLv3')
depends=('dotnet-runtime-5.0' 'dotnet-host>=5.0')
makedepends=('git' 'dotnet-sdk-5.0')
provides=("qpm")
source=('git+https://github.com/sc2ad/QuestPackageManager'
        'qpm')
sha256sums=('SKIP'
            '99f20aa6c3828881838b3f6df91fe957407b6513c356612288db7a31e6e71aac')

build() {
    export DOTNET_CLI_TELEMETRY_OPTOUT=1
    export DOTNET_SKIP_FIRST_TIME_EXPERIENCE=true

    cd "$srcdir/QuestPackageManager"

    dotnet publish -r linux-x64 -c Release -p:PublishReadyToRun=true --output "./out"
}

package() {
    cd "$srcdir"
    install -do root "$pkgdir/usr/share/QuestPackageManager"
``
    cd "$srcdir/QuestPackageManager/out"
    cp -r ./* "$pkgdir/usr/share/QuestPackageManager"

    cd "$srcdir"
    install -Dm 755 -o root "qpm" -t "$pkgdir/usr/bin"
}
