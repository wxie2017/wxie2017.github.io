# -*- mode:org; coding: utf-8 -*-

#+TITLE:     task for openssl git fork
#+AUTHOR:    Wensheng Xie
#+EMAIL:     wxie@member.fsf.org
#+LANGUAGE:  en
#+OPTIONS: H:2 num:nil toc:nil \n:nil @:t ::t |:t ^:{} _:{} *:t TeX:t LaTeX:t
#+STYLE: <link rel="stylesheet" type="text/css" href="org.css" />
#+LATEX_CLASS: myclass
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

* tasks for openssl git fork
** [2020]
*** [2020-05]
**** [2020-05-25 一]
***** build openssl for git
****** DONE “Fork” button at the top right of [[https://github.com/openssl/openssl][openssl git]] [1/1]
       DEADLINE: <2020-05-25 一>
 - [X] forked: https://github.com/wxie2017/openssl from
   https://github.com/openssl/openssl
****** DONE magit-clone https://github.com/wxie2017/openssl ~/work/openssl/
       DEADLINE: <2020-05-25 一>
#+BEGIN_SRC shell
    $ git clone git@github.com/wxie2017/openssl
    $ cd openssl
    $ git remote add openssl git://github.com/openssl/openssl # magit remote
    $ git remote -v # display setup
    $ git pull openssl master # get changes from master remotely: magit pull
    $ git push # push the changes to your fork remotely
    $ git pull # get the changes from your fork to local git
#+END_SRC
**** [2020-05-26 二]
***** build openssl locally
****** DONE read installation document
       DEADLINE: <2020-05-26 二>
#+BEGIN_SRC shell
cd openssl
./config
make
# make check
make test
sudo make install #/usr/local/bin
# make installcheck
#+END_SRC
***** submit a build issue to githbu - [[https://github.com/openssl/openssl/issues/11958][11958]] [1/1]
 - [X] provide output
#+BEGIN_SRC shell
make VF=1 TESTS=test_evp test # big
#+END_SRC
***** DONE issue: openssl: error while loading shared libraries: libssl.so.3: cannot open shared object file: No such file or directory
      DEADLINE: <2020-05-26 二>
 #+BEGIN_SRC shell
su
ln -s /usr/local/lib/libssl.so.3 /usr/lib/libssl.so.3
ln -s /usr/local/lib/libcrypto.so.3 /usr/lib/libcrypto.so.3
 #+END_SRC
