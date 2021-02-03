# -*- mode:org; coding: utf-8 -*-

#+TITLE:     task for westlake
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

* tasks for westlake
** [2020]
*** [2020-12]
**** [2020-12-12 六]
***** Mushroom cloud Maker space workshop [8/8]
 - [X] update hlk-7628N to openwrt 19.07.x
 - [X] open luci with http://192.168.1.1
 - [X] setup wireless network in luci with scan
 - [X] in the pc, log in to hlk-7628N:
#+BEGIN_SRC shell
ssh root@192.168.1.1
#change source to tuna.tsinghua
sed -i 's_downloads.openwrt.org_mirrors.tuna.tsinghua.edu.cn/openwrt_' /etc/opkg/distfeeds.conf
#+END_SRC
 - [X] download mesh related package for hlk-7628N
#+BEGIN_SRC shell
opkg update
opkg install kmod-batman-adv

opkg install batctl-full

opkg remove wpad-basic
opkg install wpad-mesh-openssl
#+END_SRC
 - [X] setup network in hlk-7628N to enable mesh:
#+BEGIN_SRC shell
vi /etc/config/network
#+END_SRC
config interface 'lan'
	option type 'bridge'
	option ifname 'eth0.1 bat0'
	option proto 'static'
	option netmask '255.255.0.0'
	option ip6assign '60'
	option ipaddr '10.20.0.1'

config device 'lan_eth0_1_dev'
	option name 'eth0.1'

config interface 'wan'
	option ifname 'eth0.2'
	option proto 'dhcp'

config device 'wan_eth0_2_dev'
	option name 'eth0.2'

config switch
	option name 'switch0'
	option reset '1'
	option enable_vlan '1'

config switch_vlan
	option device 'switch0'
	option vlan '1'
	option ports '1 2 3 4 6t'

config switch_vlan
	option device 'switch0'
	option vlan '2'
	option ports '0 6t'

config interface 'wwan'
	option proto 'dhcp'

config interface 'bat0'
        option proto 'batadv'
        option routing_algo 'BATMAN_IV'
        option aggregated_ogms 1
        option ap_isolation 0
        option bonding 0
        option fragmentation 1
        #option gw_bandwidth '10000/2000'
        option gw_mode 'off'
        #option gw_sel_class 20
        option log_level 0
        option orig_interval 1000
        option bridge_loop_avoidance 1
        option distributed_arp_table 1
        option multicast_mode 1
        option network_coding 0
        option hop_penalty 30
        option isolation_mark '0x00000000/0x00000000'

config interface 'nwi_mesh0'
        option mtu '2304'
        option proto 'batadv_hardif'
        option master 'bat0'

 - [X] setup wireless in hlk-7628N to enable search of mesh:
#+BEGIN_SRC shell
vi /etc/config/wireless
#+END_SRC
config wifi-device 'radio0'
  option type 'mac80211'
  option channel '11'
  option path 'platform/10300000.wmac'
  option hwmode '11ng'

config wifi-iface 'default_radio0'
  option device 'radio0'
  option network 'lan'
  option mode 'ap'
  option ssid 'Project West Lake'
  option encryption 'psk2'
  option key 'projwestlake'
  option ieee80211r '1'
  option mobility_domain 'baad'
  option ft_psk_generate_local '1'
  option pmk_r1_push '1'

config wifi-iface 'mesh0'
  option device 'radio0'
  option ifname 'mesh0'
  option network 'nwi_mesh0'
  option mode 'mesh'
  option mesh_fwding '0'
  option mesh_id 'mesh_openwrt'
  option key 'vfrgj1235'
  option mesh_rssi_threshold '0'
  option encryption 'sae'
 - [X] reboot the hlk-7628N
