# -*- mode:org; coding: utf-8 -*-

#+TITLE:     task for test etcher
#+AUTHOR:    Wensheng Xie
#+EMAIL:     wxie@member.fsf.org
#+LANGUAGE:  en
#+OPTIONS: H:2 num:nil toc:nil \n:nil @:t ::t |:t ^:{} _:{} *:t TeX:t LaTeX:t
#+STYLE: <link rel="stylesheet" type="text/css" href="org.css" />
#+LATEX_CLASS: report
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

* tasks for test etcher
** [2021]
*** [2021-02]
**** [2021-02-02 二]
***** DONE install etcher for Debian GNU/Linux [4/4]
      CLOSED: [2021-02-02 二 15:24]
      - CLOSING NOTE [2021-02-02 二 15:24] \\
        installed
 - [X] Add Etcher debian repository
#+BEGIN_SRC shell
echo "deb https://deb.etcher.io stable etcher" | sudo tee /etc/apt/sources.list.d/balena-etcher.list
#+END_SRC
 - [X] Trust Bintray.com's GPG key
#+BEGIN_SRC shell
sudo apt-key adv --keyserver hkps://keyserver.ubuntu.com:443 --recv-keys 379CE192D401AB61
#+END_SRC
 - [X] Update and install
#+BEGIN_SRC shell
sudo apt-get update
sudo apt-get install balena-etcher-electron
#+END_SRC
 - [X] uninstall
#+BEGIN_SRC shell
sudo apt-get remove balena-etcher-electron
sudo rm /etc/apt/sources.list.d/balena-etcher.list
sudo apt-get update
#+END_SRC
