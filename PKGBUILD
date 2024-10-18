# Maintainer: Chaiwat Suttipongsakul <cwt@bashell.com>
pkgname="th1520-npu"
pkgver=r3.3c351ad
pkgrel=1
pkgdesc="TH1520 NPU for Arch Linux"
arch=('riscv64')
url="https://github.com/revyos/th1520-npu"
license=('proprietary')
depends=('linux-cwt-510-thead-lpi4a')
makedepends=('git')
options=('!strip')
source=("git+https://github.com/revyos/th1520-npu.git"
        "91-npu.rules"
	"modprobe.d-vha.conf"
	"mkinitcpio.conf.d-vha.conf")
sha256sums=('SKIP'
            'c98deda3626442728b54502ebbfae04e3d812625e3ddb92a3599f15a5533bc84'
            'ec7d665e015aab577452fa53b1ad5131c75558f7531ecb75a127fd3f4fe49919'
            '87e2a6a162965e1c088b01ba8e249e2067333f3014cf1a669a3038bfbd257361')

pkgver() {
  cd "$srcdir/$pkgname"
  printf 'r%s.%s' "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

package() {
  cd "$srcdir"
  install -Dm644 modprobe.d-vha.conf \
    "${pkgdir}/etc/modprobe.d/vha.conf"
  install -Dm644 mkinitcpio.conf.d-vha.conf \
    "${pkgdir}/etc/mkinitcpio.conf.d/vha.conf"
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

