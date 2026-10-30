# 『れがしーなOS達: FPGAで動かす PDP-11と2.11BSD』リンク集

本書に出てくるリンクを、章の順に並べました。電子書籍の端末でリンクが開けないときや、PC で作業するときに使ってください。

- 対応する版：タグ `book-v2`（ソースのコミット `b935933427af18def5804802fa2a7d95e7f81fa5`）
- リンク先が移ったときは、このページを直します。本と違うときは、このページの URL を使ってください。

## よく使うもの

- [配布ファイル（GitHub Releases、book-v2）](https://github.com/itoh5588/w11/releases/tag/book-v2)：`.bit`、microSD のイメージ、SHA-256
- [単体動作版 README](https://github.com/itoh5588/w11/blob/b935933427af18def5804802fa2a7d95e7f81fa5/rtl/sys_gen/w11a/artys7_standalone/README.md)：回路の構成と追加回路の案内
- [book-scripts](https://github.com/itoh5588/w11/tree/5c49bb27fdd46c91708a5e35fe16638a601266a1/book-scripts)：本文のコマンドを節ごとに切り出したスクリプト

第3章でソースを取得するコマンド：

```sh
git clone --branch book-v2 https://github.com/itoh5588/w11.git w11-standalone
```

第3章・第4章・付録Dで配布ファイルを取得する場所：

```text
https://github.com/itoh5588/w11/releases/download/book-v2
```

## 第2章　部品と道具を準備する

- [AMD のダウンロードページ（Vivado 2025.2）](https://www.amd.com/en/support/downloads/adaptive-socs-and-fpgas/development-tools/2025-2.html)：Vivado Lab Edition を入れる
- [Tera Term のプロジェクトのページ](https://teratermproject.github.io/)：端末ソフト
- [balenaEtcher](https://etcher.balena.io/)：microSD への書込み
- 回路や媒体を自分で作る場合（Vivado 2022.1、UG973）
  - [導入案内（Download the Installation File）](https://docs.amd.com/r/2022.1-English/ug973-vivado-release-notes-install-license/Download-the-Installation-File)
  - [公式の導入手順（Installation Flow）](https://docs.amd.com/r/2022.1-English/ug973-vivado-release-notes-install-license/Installation-Flow)
  - [対応 OS 一覧（Supported Operating Systems）](https://docs.amd.com/r/2022.1-English/ug973-vivado-release-notes-install-license/Supported-Operating-Systems)
  - [ケーブルドライバの手順（Install Cable Drivers）](https://docs.amd.com/r/2022.1-English/ug973-vivado-release-notes-install-license/Install-Cable-Drivers)

## 第3章　回路データを用意する

- [配布 `.bit` のリリースのページ（book-v2）](https://github.com/itoh5588/w11/releases/tag/book-v2)
- [w11 のリポジトリ（単体動作版）](https://github.com/itoh5588/w11)：`git clone` で取得する
- [単体動作版 README](https://github.com/itoh5588/w11/blob/b935933427af18def5804802fa2a7d95e7f81fa5/rtl/sys_gen/w11a/artys7_standalone/README.md)

## 第4章　2.11BSD の microSD を用意する

- [配布イメージ（book-v2）](https://github.com/itoh5588/w11/releases/tag/book-v2)：`rp07_w11_tape481_fpsim.img.xz`
- [2.11BSD-481-simh-dist.tap](https://www.tuhs.org/Archive/Distributions/UCB/2BSD/2.11BSD-patch481/2.11BSD-481-simh-dist.tap)：媒体を自分で作るときの入力（TUHS）
- [2.11BSD の設置文書 setup.pdf](https://www.tuhs.org/Archive/Distributions/UCB/2BSD/2.11BSD-patch481/setup.pdf)：RP07 の形と区画（Appendix B）

## 第5章　配線、構成、初回起動

- [Arty S7 Reference Manual（Web 版）](https://digilent.com/reference/programmable-logic/arty-s7/reference-manual)：Pmod の端子の並び
- [picocom のマニュアル](https://raw.githubusercontent.com/npat-efault/picocom/master/picocom.1.md)：Ubuntu で端末を開く場合
- [Vivado 2022.1 チュートリアル（UG936）](https://docs.amd.com/r/2022.1-English/ug936-vivado-tutorial-programming-debugging/Step-2-Program-the-KC705-Board-and-Interact-with-the-JTAG-to-AXI-Master-Core)：JTAG で構成する

## 第6章　構成フラッシュへ保存する

- [Arty S7 Reference Manual（PDF）](https://digilent.com/reference/_media/reference/programmable-logic/arty-s7/arty-s7_rm.pdf)：フラッシュの型番（第2節・図2.1）
- [Vivado 2022.1 の構成メモリー手順（UG908）](https://docs.amd.com/r/2022.1-English/ug908-vivado-programming-debugging/Programming-Configuration-Memory-Devices)

## 付録B　ブロック図と VHDL ファイルの対応

ソースはすべて固定コミット `b935933` の版です。

- 全体の接続：[sys_w11a_sa_as7.vhd](https://github.com/itoh5588/w11/blob/b935933427af18def5804802fa2a7d95e7f81fa5/rtl/sys_gen/w11a/artys7_standalone/sys_w11a_sa_as7.vhd)
- CPU と主記憶の境界：[w11_cpu_dma_path.vhd](https://github.com/itoh5588/w11/blob/b935933427af18def5804802fa2a7d95e7f81fa5/rtl/sys_gen/w11a/artys7_standalone/w11_cpu_dma_path.vhd)
- CPU システム：[pdp11_sys70.vhd](https://github.com/itoh5588/w11/blob/b935933427af18def5804802fa2a7d95e7f81fa5/rtl/w11a/pdp11_sys70.vhd)
- CPU の中核：[pdp11_core.vhd](https://github.com/itoh5588/w11/blob/b935933427af18def5804802fa2a7d95e7f81fa5/rtl/w11a/pdp11_core.vhd)
- 番地の変換：[pdp11_mmu.vhd](https://github.com/itoh5588/w11/blob/b935933427af18def5804802fa2a7d95e7f81fa5/rtl/w11a/pdp11_mmu.vhd)
- CPU のキャッシュ：[pdp11_cache.vhd](https://github.com/itoh5588/w11/blob/b935933427af18def5804802fa2a7d95e7f81fa5/rtl/w11a/pdp11_cache.vhd)
- CPU と DMA の調停：[w11_mem_arbiter.vhd](https://github.com/itoh5588/w11/blob/b935933427af18def5804802fa2a7d95e7f81fa5/rtl/sys_gen/w11a/artys7_standalone/w11_mem_arbiter.vhd)
- DDR3 への接続：[sramif_mig_artys7.vhd](https://github.com/itoh5588/w11/blob/b935933427af18def5804802fa2a7d95e7f81fa5/rtl/bplib/artys7/sramif_mig_artys7.vhd)
- ディスクの装置制御：[ibdr_rp07n.vhd](https://github.com/itoh5588/w11/blob/b935933427af18def5804802fa2a7d95e7f81fa5/rtl/sys_gen/w11a/artys7_standalone/ibdr_rp07n.vhd)
- SD の制御：[sdspi_ctl.vhd](https://github.com/itoh5588/w11/blob/b935933427af18def5804802fa2a7d95e7f81fa5/rtl/sys_gen/w11a/artys7_standalone/sdspi_ctl.vhd)
- SD の信号：[sdspi_phy.vhd](https://github.com/itoh5588/w11/blob/b935933427af18def5804802fa2a7d95e7f81fa5/rtl/sys_gen/w11a/artys7_standalone/sdspi_phy.vhd)
- カードから主記憶へ：[sd_dma_wr.vhd](https://github.com/itoh5588/w11/blob/b935933427af18def5804802fa2a7d95e7f81fa5/rtl/sys_gen/w11a/artys7_standalone/sd_dma_wr.vhd)
- 主記憶からカードへ：[sd_dma_rd.vhd](https://github.com/itoh5588/w11/blob/b935933427af18def5804802fa2a7d95e7f81fa5/rtl/sys_gen/w11a/artys7_standalone/sd_dma_rd.vhd)
- 文字端末：[ibd_dl11n.vhd](https://github.com/itoh5588/w11/blob/b935933427af18def5804802fa2a7d95e7f81fa5/rtl/sys_gen/w11a/artys7_standalone/ibd_dl11n.vhd)
- CPU の自動開始：[w11_autostart.vhd](https://github.com/itoh5588/w11/blob/b935933427af18def5804802fa2a7d95e7f81fa5/rtl/sys_gen/w11a/artys7_standalone/w11_autostart.vhd)
- ディスクの選択：[sd_label_probe.vhd](https://github.com/itoh5588/w11/blob/b935933427af18def5804802fa2a7d95e7f81fa5/rtl/sys_gen/w11a/artys7_standalone/sd_label_probe.vhd)
- 本書で使わないディスク：[ibdr_rk05n.vhd](https://github.com/itoh5588/w11/blob/b935933427af18def5804802fa2a7d95e7f81fa5/rtl/sys_gen/w11a/artys7_standalone/ibdr_rk05n.vhd)、[ibdr_rl02n.vhd](https://github.com/itoh5588/w11/blob/b935933427af18def5804802fa2a7d95e7f81fa5/rtl/sys_gen/w11a/artys7_standalone/ibdr_rl02n.vhd)
- UNIBUS マップの写し：[ubmap_shadow.vhd](https://github.com/itoh5588/w11/blob/b935933427af18def5804802fa2a7d95e7f81fa5/rtl/sys_gen/w11a/artys7_standalone/ubmap_shadow.vhd)

## 付録C　参考文献とオンライン資料

### UNIX・C と歴史的背景

- [Software Tools](https://search.worldcat.org/title/Software-tools/oclc/471569428)（Kernighan, Plauger）
- [The C Programming Language](https://1535.sydneyplus.com/genieplus/final/ViewRecord.aspx?record=598c01cf-6682-467b-a1c7-93a668f37f7a&template=Books)（Kernighan, Ritchie）
- [The Evolution of the Unix Time-sharing System](https://www.nokia.com/bell-labs/about/dennis-m-ritchie/hist.html)（Ritchie）
- [David Cutler](https://computerhistory.org/profile/david-cutler/?alias=bio&person=david-cutler)（Computer History Museum）

### PDP-11 と 2.11BSD

- [PDP-11/70 Processor Handbook](https://bitsavers.org/pdf/dec/pdp11/1170/PDP-11_70_Handbook_1977-78.pdf)
- [Installing and Operating 2.11BSD on the PDP-11（setup.pdf）](https://www.tuhs.org/Archive/Distributions/UCB/2BSD/2.11BSD-patch481/setup.pdf)
- [2.11BSD-481-simh-dist.tap](https://www.tuhs.org/Archive/Distributions/UCB/2BSD/2.11BSD-patch481/2.11BSD-481-simh-dist.tap)
- [History of the Berkeley Software Distribution](https://en.wikipedia.org/wiki/History_of_the_Berkeley_Software_Distribution)（Wikipedia）
- [211bsd_rlset.tgz](http://www.retro11.de/data/oc_w11/oskits/211bsd_rlset.tgz)
- [RL01/RL02 Disk Drive Technical Manual](https://bitsavers.org/pdf/dec/disc/rl01_rl02/EK-RL012-TM-PRE_RL01_RL02_Disk_Drive_Technical_Manual_Preliminary_Dec79.pdf)

### Sixth Edition UNIX と Lions 本

- [はじめてのOSコードリーディング ―UNIX V6で学ぶカーネルのしくみ](https://gihyo.jp/book/2013/978-4-7741-5464-0)
- [Odd Comments and Strange Doings in Unix](https://www.nokia.com/bell-labs/about/dennis-m-ritchie/odd.html)（Ritchie）
- [unix-v6-on-simh](https://github.com/retux/unix-v6-on-simh)
- [Ancient UNIX の使用許諾](https://www.tuhs.org/Archive/Caldera-license.pdf)

### w11 のソースと実装資料

- [w11 — PDP-11/70 CPU core and SoC（公開元）](https://github.com/wfjm/w11)、[ライセンス本文](https://github.com/wfjm/w11/blob/master/License.txt)
- [standalone README](https://github.com/itoh5588/w11/blob/b935933427af18def5804802fa2a7d95e7f81fa5/rtl/sys_gen/w11a/artys7_standalone/README.md)
- [GitHub Releases（book-v2）](https://github.com/itoh5588/w11/releases/tag/book-v2)
- [book-scripts](https://github.com/itoh5588/w11/tree/5c49bb27fdd46c91708a5e35fe16638a601266a1/book-scripts)（コミット `5c49bb27`）
- [Guide to install and build w11a systems, test benches and support software](https://github.com/itoh5588/w11/blob/b935933427af18def5804802fa2a7d95e7f81fa5/doc/INSTALL.md)
- [Guide to the Build System (Xilinx Vivado Version)](https://github.com/itoh5588/w11/blob/b935933427af18def5804802fa2a7d95e7f81fa5/doc/README_buildsystem_Vivado.md)
- [SD_CARD.md](https://github.com/itoh5588/w11/blob/b935933427af18def5804802fa2a7d95e7f81fa5/rtl/sys_gen/w11a/artys7_standalone/SD_CARD.md)
- [RP07 設計メモ](https://github.com/itoh5588/w11/blob/b935933427af18def5804802fa2a7d95e7f81fa5/Docs/artys7_standalone_rp07_design.md)
- [211bsd_rl キットの README](https://github.com/itoh5588/w11/blob/b935933427af18def5804802fa2a7d95e7f81fa5/tools/oskit/211bsd_rl/README.md)

book-scripts を取得するときの URL：

```text
https://raw.githubusercontent.com/itoh5588/w11/5c49bb27fdd46c91708a5e35fe16638a601266a1/book-scripts
```

### FPGA・ディジタル回路設計の日本語入門書

- [作ろう！CPU ― 基礎から理解するコンピューターのしくみ](https://book.mynavi.jp/manatee/books/detail/id=117231)（[対象基板](https://amane-uehara.github.io/cpubook/product/)、[操作手順](https://amane-uehara.github.io/cpubook/compile/)）
- [Verilog HDLで学ぶコンピュータアーキテクチャ](https://www.coronasha.co.jp/np/isbn/9784339029406/)
- [SystemVerilogによるFPGA/ディジタル回路設計入門](https://www.ohmsha.co.jp/book/9784274231018.html)
- [改訂 VHDLによるハードウェア設計入門](https://shop.cqpub.co.jp/hanbai/books/33/33961.htm)

### FPGA 基板・開発ツール・端末

- [Arty S7 Reference Manual（PDF）](https://digilent.com/reference/_media/reference/programmable-logic/arty-s7/arty-s7_rm.pdf)
- [Arty S7 Reference Manual（Web 版）](https://digilent.com/reference/programmable-logic/arty-s7/reference-manual)
- [UG973：Release Notes, Installation, and Licensing](https://docs.amd.com/r/2022.1-English/ug973-vivado-release-notes-install-license/Download-the-Installation-File)
- [UG908：Programming and Debugging](https://docs.amd.com/r/2022.1-English/ug908-vivado-programming-debugging/Programming-Configuration-Memory-Devices)
- [UG936：Tutorial: Programming and Debugging](https://docs.amd.com/r/2022.1-English/ug936-vivado-tutorial-programming-debugging/Step-2-Program-the-KC705-Board-and-Interact-with-the-JTAG-to-AXI-Master-Core)
- [Downloads 2025.2](https://www.amd.com/en/support/downloads/adaptive-socs-and-fpgas/development-tools/2025-2.html)
- [balenaEtcher](https://etcher.balena.io/)
- [Tera Term](https://teratermproject.github.io/)
- [picocom manual](https://raw.githubusercontent.com/npat-efault/picocom/master/picocom.1.md)

### 写真の出典

- [RP07 Disk Drive Service Manual](http://bitsavers.org/pdf/dec/disc/rp07/ER-ORP07-SV_RP07_ServiceMan_Oct80.pdf)（bitsavers.org）
- PDP-11/70（Joe Mabel、[CC BY-SA 3.0](https://creativecommons.org/licenses/by-sa/3.0/)）：[Wikimedia Commons](<https://commons.wikimedia.org/wiki/File:PDP-11-70_Minicomputer_from_Digital_Equipment_Corporation_(DEC),_exhibited_at_Living_Computer_Museum_in_Seattle,_USA_(edited_image_without_background).jpg>)
- RK05（Autopilot、[CC BY-SA 3.0](https://creativecommons.org/licenses/by-sa/3.0/)）：[Wikimedia Commons](https://commons.wikimedia.org/wiki/File:RK05.jpg)
- RL02 のカートリッジ（Selquim、[CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)）：[Wikimedia Commons](https://commons.wikimedia.org/wiki/File:DEC_RL02_Data_Cartridge.jpg)
- VT100（Jason Scott、[CC BY 2.0](https://creativecommons.org/licenses/by/2.0/)）：[Wikimedia Commons](https://commons.wikimedia.org/wiki/File:DEC_VT100_terminal.jpg)

## 付録D　Lions の V6 を同じ基板で動かす

- [配布イメージ（book-v2）](https://github.com/itoh5588/w11/releases/tag/book-v2)：`v6_rk_card_labeled.img.xz`
- [unix-v6-on-simh](https://github.com/retux/unix-v6-on-simh)：媒体を自分で作るときのキット

## 付録E　RL01・RL02 を一枚の microSD に収める

- [211bsd_rlset.tgz](http://www.retro11.de/data/oc_w11/oskits/211bsd_rlset.tgz)：RL 版 2.11BSD のディスクイメージ
- [211bsd_rl キットの README](https://github.com/itoh5588/w11/blob/b935933427af18def5804802fa2a7d95e7f81fa5/tools/oskit/211bsd_rl/README.md)：入手と展開の方法
- [RL01/RL02 Disk Drive Technical Manual](https://bitsavers.org/pdf/dec/disc/rl01_rl02/EK-RL012-TM-PRE_RL01_RL02_Disk_Drive_Technical_Manual_Preliminary_Dec79.pdf)（DEC）
