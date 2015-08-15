# Maintainer: Sebastien Luttringer <seblu+arch@seblu.net>
# Contributor: Marti Raudsepp <marti@juffo.org>
# Contributor: Manuel Mazzuola <origin.of@gmail.com>

pkgname=ferm
pkgver=2.1
pkgrel=1
pkgdesc='Tool to maintain complex firewalls'
arch=('any')
url='http://ferm.foo-projects.org/'
license=('GPL2')
depends=('iptables' 'perl')
optdepends=('ebtables' 'arptables')
backup=('etc/ferm.conf')
source=(
  "http://ferm.foo-projects.org/download/${pkgver:0:3}/$pkgname-$pkgver.tar.gz"
  'rc.d'
  'conf.d'
  'ferm.conf'
   ) 
md5sums=('ac5d11554a50e514cbad8f354b14e564'
         'b3a555430868cbd420ce2263eb658d9c'
         'beac7f5a6e44094637954161b2786dd4'
         '314ebaf66abbe754850449359620e2d8')

package() {
  # software setup
  cd $pkgname-$pkgver
  make PREFIX="${pkgdir}/usr" install

  # setup rc.d script
  install -D -m 755 "${srcdir}/rc.d" "${pkgdir}/etc/rc.d/ferm"
  
  # setup conf.d file
  install -D -m 644 "${srcdir}/conf.d" "${pkgdir}/etc/conf.d/ferm"

  # setup default config
  install -D -m 644 "${srcdir}/ferm.conf" "${pkgdir}/etc/ferm.conf"
}

# vim:set ts=2 sw=2 ft=sh et:
