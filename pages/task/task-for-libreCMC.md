# -*- mode:org; coding: utf-8 -*-

#+TITLE:     task for libreCMC
#+AUTHOR:    Wensheng Xie
#+EMAIL:     wxie@member.fsf.org
#+LANGUAGE:  en
#+OPTIONS: H:2 num:nil toc:nil \n:nil @:t ::t |:t ^:{} _:{} *:t TeX:t LaTeX:t
#+STYLE: <link rel="stylesheet" type="text/css" href="org.css" />
#+LATEX_CLASS: article
#+LATEX_CLASS_OPTIONS: [a4paper]
#+ATTR_LATEX: width=0.38\textwidth wrap placement={r}{0.4\textwidth}
#+ATTR_LATEX: :float multicolumn
#+REVEAL_TRANS: None
#+REVEAL_THEME: Black
#+TAGS: @work(w) @home(h) @road(r) laptop(l) pc(p) { @read : @read_book @read_ebook }
#+ATTR_ORG: :width 30
#+ATTR_HTML: width="100px"
#+EXPORT_SELECT_TAGS: export
#+EXPORT_EXCLUDE_TAGS: noexport
#+STARTUP: fold

* tasks for libreCMC
** [2020]
*** [2020-12]
**** [2020-12-08 二]
***** build libreCMC
****** TODO Get the latest libreCMC source code
#+BEGIN_SRC shell
git clone https://git.librecmc.org/git/librecmc/librecmc.git
cd librecmc
./scripts/feeds update && ./scripts/feeds install -a
#+END_SRC
****** TODO Configure libreCMC for your device
Generally, a good default configuration includes: [0/3]
 - [ ] luci : Collections -> luci + luci -> protocols -> luci-proto-relayd
 - [ ] Networking : wpa-cli + wpa-supplicant + iw
 - [ ] Utilities : Editors -> Nano
#+BEGIN_SRC shell
cd librecmc
make menuconfig
#+END_SRC
****** TODO pre-fetch all source code for all dependencies
#+BEGIN_SRC shell
make download
#+END_SRC
****** TODO build process
#+BEGIN_SRC shell
make
# or
make -j <your number of CPU cores + 1>
#+END_SRC
****** TODO built image available in
$SRC_ROOT/bin/$BUILD_TARGET/librecmc-$BUILD_TARGET-generic-$TARGET_PROFILE-$VERSION-$FS_TYPE-factory.bin
e.g.:
$BUILD_TARGET = target (ex. ar71xx), $TARGET_PROFILE = device, $VERSION = device version (some haven't any)
****** TODO flash the image to your device [0/3]
 - [ ] can easily be flashed from the stock firmware's web-ui
 - [ ] require a tFTP flash
 - [ ] require opening up the router/external hardware for initial install (serial cable, SPI flasher or both)
