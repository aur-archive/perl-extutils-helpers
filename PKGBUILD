# Contributor: xRemaLx <anton.komolov@gmail.com>

pkgname='perl-extutils-helpers'
_pkgname='ExtUtils-Helpers'
pkgver=0.022
pkgrel=1
pkgdesc="ExtUtils::Helpers - Various portability utilities for module builders"
arch=(any)
license=('perl')
url="http://search.cpan.org/dist/ExtUtils-Helpers/"
options=(!emptydirs)

depends=('perl>=5.10.1')
makedepends=('perl')

provides=("extutils-helpers=${pkgver}" "ExtUtils::Helpers=${pkgver}" "perl-extutils-helpers=${pkgver}"
          "extutils-helpers-unix=${pkgver}" "ExtUtils::Helpers::Unix=${pkgver}" "perl-extutils-helpers-unix=${pkgver}"
          "extutils-helpers-vms=${pkgver}" "ExtUtils::Helpers::VMS=${pkgver}" "perl-extutils-helpers-vms=${pkgver}"
          "extutils-helpers-windows=${pkgver}" "ExtUtils::Helpers::Windows=${pkgver}" "perl-extutils-helpers-windows=${pkgver}")

source=("http://search.cpan.org/CPAN/authors/id/L/LE/LEONT/${_pkgname}-${pkgver}.tar.gz")
sha512sums=('ffdec8c1cf96daadfea34860bbd72d205620dec891d617721bb8ac242ccd2ba0cd5a5f50440633e03ae5fd575add6ac539c95ed68909a64a44b97ac2bba2bb39')

build() {
  ( export PERL_MM_USE_DEFAULT=1 PERL5LIB=""                 \
      PERL_AUTOINSTALL=--skipdeps                            \
      PERL_MM_OPT="INSTALLDIRS=vendor DESTDIR='$pkgdir'"     \
      PERL_MB_OPT="--installdirs vendor --destdir '$pkgdir'" \
      MODULEBUILDRC=/dev/null

    cd "${srcdir}/${_pkgname}-${pkgver}"
    /usr/bin/perl Makefile.PL
    make
  )
}

check() {
  cd "${srcdir}/${_pkgname}-${pkgver}"
  ( export PERL_MM_USE_DEFAULT=1 PERL5LIB=""
    make test
  )
}

package() {
  cd "${srcdir}/${_pkgname}-${pkgver}"
  make install
  find "$pkgdir" -name .packlist -o -name perllocal.pod -delete
}

# vim:set ts=2 sw=2 et:
