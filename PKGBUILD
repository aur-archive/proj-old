# Author: lfleischer <lfleischer@9fca08f4-af9d-4005-b8df-a31f2cc04f65>
# Committer: svntogit <svntogit@gerolde.archlinux.org>
# Mantainer: Luigi Ranghetti <luigi.ranghetti@gmail.com>

pkgname=proj-old
pkgver=4.7.0
pkgrel=2
pkgdesc='Cartographic Projections library. Old version (< 4.8.0) is needed by saga-gis, otherwise the file projects.h could not be found.'
arch=('i686' 'x86_64')
url="http://trac.osgeo.org/proj/"
license=('MIT')
options=('!libtool')
conflicts=('proj')
provides=('proj')
source=("http://download.osgeo.org/proj/proj-$pkgver.tar.gz"
        "http://download.osgeo.org/proj/proj-datumgrid-1.5.zip"
        "chenyx06a.zip::http://www.swisstopo.admin.ch/internet/swisstopo/en/home/topics/survey/lv03-lv95/chenyx06/distortion_grids.parsys.65772.downloadList.94632.DownloadFile.tmp/chenyx06antv2.zip")
md5sums=('927d34623b52e0209ba2bfcca18fe8cd'
         'f5bf28a2a9c6afe9a3f670f0c0adb783'
         'fbbfe2b6bcbc41168fe3bdc4a6c1082a')


build() {
  bsdtar -xzvf "${srcdir}/proj-datumgrid-1.5.zip" -C "${srcdir}/proj-${pkgver}/nad"
  bsdtar -xzvf "${srcdir}/chenyx06a.zip" -C "${srcdir}/proj-${pkgver}/nad" CHENYX06a.gsb
  cd "${srcdir}/proj-${pkgver}"

  ./configure --prefix=/usr
  make
  make DESTDIR="${pkgdir}" install

  install -D COPYING "${pkgdir}/usr/share/licenses/proj/LICENSE"
}