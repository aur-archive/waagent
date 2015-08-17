# Maintainer: Bartłomiej Piotrowski <nospam@bpiotrowski.pl>

pkgname=waagent
pkgver=2.0.3
pkgrel=1
pkgdesc='Windows Azure Linux Agent'
arch=('any')
url='https://github.com/WindowsAzure/WALinuxAgent'
license=('Apache')
depends=('python2' 'python2-pyasn1')
makedepends=('git' 'python2-setuptools')
backup=(etc/waagent.conf
        etc/logrotate.d/waagent)
source=(git://github.com/WindowsAzure/WALinuxAgent.git#tag=WALinuxAgent-$pkgver)
md5sums=('SKIP')

prepare() {
    cd WALinuxAgent
    sed -i '1s/python/python2/' waagent
    sed -i 's/sbin/bin/' distro/systemd/waagent.service
}

package() {
    cd WALinuxAgent

    install -Dm755 waagent "$pkgdir"/usr/bin/waagent
    install -Dm644 config/waagent.conf "$pkgdir"/etc/waagent.conf
    install -Dm644 config/waagent.logrotate "$pkgdir"/etc/logrotate.d/waagent
    install -Dm644 distro/systemd/waagent.service \
            "$pkgdir"/usr/lib/systemd/system/waagent.service
}
