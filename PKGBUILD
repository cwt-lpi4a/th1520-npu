# Maintainer: Chaiwat Suttipongsakul <cwt@bashell.com>
pkgname="th1520-npu"
pkgver=r2.492b7e6
pkgrel=2
pkgdesc="TH1520 NPU for Arch Linux"
arch=('riscv64')
url="https://github.com/revyos/th1520-npu"
license=('proprietary')
depends=('linux-cwt-510-thead-lpi4a')
makedepends=('git')
options=('!strip')
source=("git+https://github.com/revyos/th1520-npu.git"
        "91-npu.rules"
	"vha.conf")
md5sums=('SKIP'
         '2300bcb6f6606212ba3394b14396ab66'
         '2c0f83de4128beba7f9ae593be171eb1')

pkgver() {
  cd "$srcdir/$pkgname"
  printf 'r%s.%s' "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

package() {
  cd "$srcdir"
  install -Dm644 vha.conf \
    "${pkgdir}/etc/modprobe.d/vha.conf"
  install -Dm644 91-npu.rules \
    "${pkgdir}/usr/lib/udev/rules.d/91-npu.rules"

  cd "$srcdir/$pkgname/addons/usr/lib/riscv64-linux-gnu"
  install -Dm755 libPVRScopeServicesNNA.so \
    "${pkgdir}/usr/lib/libPVRScopeServicesNNA.so"
  install -Dm755 libimgcustom.so \
    "${pkgdir}/usr/lib/libimgcustom.so"
  install -Dm755 libimgdnn.so \
    "${pkgdir}/usr/lib/libimgdnn.so"
  install -Dm755 libimgdnn_execute.so \
    "${pkgdir}/usr/lib/libimgdnn_execute.so"
  install -Dm755 libnnahelper.so \
    "${pkgdir}/usr/lib/libnnahelper.so"
  install -Dm755 libnnasession.so \
    "${pkgdir}/usr/lib/libnnasession.so"

  cd "$srcdir/$pkgname/addons/usr/share/npu/test"
  install -Dm755 cnn_testbench \
    "${pkgdir}/usr/share/npu/test/cnn_testbench"
  install -Dm755 lstm_testbench \
    "${pkgdir}/usr/share/npu/test/lstm_testbench"
  install -Dm755 nnvm_testbench \
    "${pkgdir}/usr/share/npu/test/nnvm_testbench"
  install -Dm755 run_cnn_testbench.sh \
    "${pkgdir}/usr/share/npu/test/run_cnn_testbench.sh"
  install -Dm755 run_nnvm_testbench.sh \
    "${pkgdir}/usr/share/npu/test/run_nnvm_testbench.sh"

  install -Dm755 bin/print_top_label.sh \
    "${pkgdir}/usr/share/npu/test/bin/print_top_label.sh"
  install -Dm755 bin/print_top_labels.py \
    "${pkgdir}/usr/share/npu/test/bin/print_top_labels.py"

  install -Dm644 resource/cnn_testbench/lenet/OCM_1M5/model.mbs.bin \
    "${pkgdir}/usr/share/npu/test/resource/cnn_testbench/lenet/OCM_1M5/model.mbs.bin"

  install -Dm644 resource/cnn_testbench/lenet/label.txt \
    "${pkgdir}/usr/share/npu/test/resource/cnn_testbench/lenet/label.txt"
  install -Dm644 resource/cnn_testbench/lenet/m1.tensor.bin \
    "${pkgdir}/usr/share/npu/test/resource/cnn_testbench/lenet/m1.tensor.bin"

  install -Dm644 resource/nnvm_testbench/light_hw_config.json \
    "${pkgdir}/usr/share/npu/test/resource/nnvm_testbench/light_hw_config.json"
  install -Dm644 resource/nnvm_testbench/light_mapconfig.json \
    "${pkgdir}/usr/share/npu/test/resource/nnvm_testbench/light_mapconfig.json"
  install -Dm644 resource/nnvm_testbench/m1.tensor.bin \
    "${pkgdir}/usr/share/npu/test/resource/nnvm_testbench/m1.tensor.bin"
  install -Dm644 resource/nnvm_testbench/m1_hist.imgir \
    "${pkgdir}/usr/share/npu/test/resource/nnvm_testbench/m1_hist.imgir"
  install -Dm644 resource/nnvm_testbench/m1_hist.imgir.params \
    "${pkgdir}/usr/share/npu/test/resource/nnvm_testbench/m1_hist.imgir.params"
}

