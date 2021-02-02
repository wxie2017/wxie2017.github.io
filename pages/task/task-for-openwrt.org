# -*- mode:org; coding: utf-8 -*-

#+TITLE:     task for openwrt
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

* tasks for openwrt
** [2020]
*** [2020-12]
**** [2020-12-08 二]
***** build librewrt
****** DONE Get the latest openwrt source code
       CLOSED: [2020-12-31 四 13:11]
       - CLOSING NOTE [2020-12-31 四 13:11] \\
         succeed
#+BEGIN_SRC shell
git clone https://git.openwrt.org/openwrt/openwrt.git
cd openwrt
./scripts/feeds update -a
./scripts/feeds install -a
#+END_SRC
****** DONE Configure openwrt for your device
       CLOSED: [2020-12-31 四 13:24]
       - CLOSING NOTE [2020-12-31 四 13:24] \\
         selected
#+BEGIN_SRC shell
cd openwrt
make menuconfig
#+END_SRC
Example, OpenWrt configuration menu for setting target and options: [4/4]
 - [X] “Target System” ⇒ “Select” ⇒ “Atheros AR7xxx/AR9xxx” ⇒ “Select”
 - [X] “Subtarget” ⇒ “Select” ⇒ “Devices with small flash” ⇒ “Select”
 - [X] “Target Profile” ⇒ “Select” ⇒ “TP-LINK TL-WR841N/ND v11” ⇒ “Select”
 - [X] “Exit” ⇒ “Yes”
****** DONE pre-fetch all source code for all dependencies
       CLOSED: [2021-01-05 二 13:16]
       - CLOSING NOTE [2021-01-05 二 13:16] \\
         succeeded
#+BEGIN_SRC shell
make download
#+END_SRC
****** DONE build process
       CLOSED: [2021-01-06 三 09:32]
       - CLOSING NOTE [2021-01-06 三 09:32] \\
         succeed
#+BEGIN_SRC shell
make # first time build
# or
make -j <your number of CPU cores + 1>
#+END_SRC
****** DONE built image available in [2/2]
       CLOSED: [2021-01-06 三 09:38]
       - CLOSING NOTE [2021-01-06 三 09:38] \\
         bin is available
$SRC_ROOT/bin/$BUILD_TARGET/librecmc-$BUILD_TARGET-generic-$TARGET_PROFILE-$VERSION-$FS_TYPE-factory.bin
e.g.:
$BUILD_TARGET = target (ex. ar71xx), $TARGET_PROFILE = device, $VERSION = device version (some haven't any)
 - [X] *-factory.bin image file is for the first installation of OpenWrt on the
   target.
 - [X] *-sysupgrade.bin image file is for updating an existing OpenWrt
   installation.
****** TODO flash the image to your device [0/3]
 - [ ] can easily be flashed from the stock firmware's web-ui
 - [ ] require a tFTP flash
 - [ ] require opening up the router/external hardware for initial install (serial cable, SPI flasher or both)
****** TODO work with N-OpenWrt board 7628N [1/6]
 - [X] use image:
openwrt-19.07.0-ramips-mt76x8-hilink_hlk-7628n-squashfs-sysupgrade.bin
 - [ ] use serial port near the power jack give access to the bootloader at
   57600 bauds, using a TTL-USB dongle. Under Windows 7 I use Teraterm. Setup
   for serial is 8 bit, no parity, 1 bit stop and no flow control.
 - [ ] Then it is easy to upload the new firmware through tftp.
 - [ ] connect one of the Lan port (not the Wan port) of the MT7688AN to the
   box. It is necessary to annotate the IP that the Dhcp server of the box
   assign to that port.
 - [ ] When the MT7688AN is booting, press 2 to load the firmware and flash it.
 - [ ] after the reboot I am able to access OpenWrt 19.07.02 on the same serial
   port.
****** DONE configure OpenWrt according [4/4]
       CLOSED: [2021-01-06 三 09:40]
       - CLOSING NOTE [2021-01-06 三 09:40] \\
         tried in another board
 - [X] modify the configuration of OpenWrt: ~/etc/config/network~
#+BEGIN_SRC
config interface 'loopback'
	option ifname 'lo'
	option proto 'static'
	option ipaddr '127.0.0.1'
	option netmask '255.0.0.0'

config globals 'globals'
	option ula_prefix 'fdb0:c1c7:3423::/48'

config switch
	option name 'switch0'
	option reset '1'
	option enable_vlan '1'

config switch_vlan
	option device 'switch0'
	option ports '6t 4 3 2 1'
	option vlan '1'

config switch_vlan
	option device 'switch0'
	option ports '6t 0'
	option vlan '2'

config interface 'wan'
	option ifname 'eth0.2'
	option proto 'dhcp'
	option macaddr '40:xx:xx:xx:xx:xx'
	option stp '1'

config interface 'lan'
	option type 'bridge'
	option stp '1'
	option proto 'static'
	option ipaddr '192.168.0.1'
	option netmask '255.255.255.0'
	option ip6assign '60'
	option ifname 'eth0.1'
	list dns '8.8.8.8'
	list dns '8.8.4.4'
#+END_SRC
 - [X] access to LuCI at 192.168.0.1
 - [X] set the administrator password
 - [X] make the first backup of configurations files
