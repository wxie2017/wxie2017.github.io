# -*- mode:org; coding: utf-8 -*-

#+TITLE:     task for dkpg and .deb
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

* tasks for dkpg and .deb
** [2020]
*** [2020-06]
**** [2020-06-03 三]
***** DONE read article of .deb
      CLOSED: [2020-06-04 四 15:40]
[[https://www.internalpointers.com/post/build-binary-deb-package-practical-guide]]
      DEADLINE: <2020-06-07 日>
**** [2020-06-04 四]
***** DONE basic deb package control [3/3]
      CLOSED: [2020-06-04 四 15:46]
 - [X] A deb package contains a collection of folders that mimics a typical Linux file system, such as /usr, /usr/bin, /opt and so on.
 - [X] A file put in one of those directories will be copied to the same location in the actual file system during installation.
 - [X] For example a binary file put into <.deb>/usr/local/bin/binaryfile will be installed to /usr/local/bin/binaryfile.
***** DONE all deb package files follow a specific naming convention: [6/6]
      CLOSED: [2020-06-04 四 15:50]
- [X] <name>_<version>-<revision>_<architecture>.deb
- [X] <name> – the name of your application;
- [X] <version> – the version number of your application;
- [X] <revision> – the version number of the current deb package;
- [X] <architecture> – the hardware architecture your program will be run on.
- [X] something like hello_1.0-1_arm64.deb
***** DONE create deb package from scratch [5/5]
      CLOSED: [2020-06-04 四 16:10]
 - [X] Create the working directory for your package
#+BEGIN_SRC shell
mkdir hello_1.0-1_arm64
#+END_SRC
 - [X] Create the internal structure in your package directory
#+BEGIN_SRC shell
mkdir -p hello_1.0-1_arm64/usr/local/bin
cp ~/YourProjects/Hello/hello hello_1.0-1_arm64/usr/local/bin
#+END_SRC
 - [X] create control file in DEBIAN directory (not debian, debian directory is
   for source code)
#+BEGIN_SRC shell
mkdir helloworld_1.0-1_arm64/DEBIAN
touch helloworld_1.0-1_arm64/DEBIAN/control
#+END_SRC
 - [X] edit the control file with a text editor
for example:
Package: hello
Version: 1.0
Architecture: arm64
Maintainer: Internal Pointers <info@internalpointers.com>
Description: A program that greets you.
 You can add a longer description here. Mind the space at the beginning of this
paragraph.
Depends: dependencies

explanation:
    Package – the name of your program;
    Version – the version of your program;
    Architecture – the target architecture;
    Maintainer – the name and the email address of the person in charge of the package maintenance;
    Description – a brief description of the program;
    Depends - the libraries your program depends on.
 - [X] last step - Build the deb package: generate the nice .deb file
#+BEGIN_SRC shell
# dpkg-deb --build --root-owner-group <package-dir>
dpkg-deb --build --root-owner-group <helloworld_1.0-1_arm64>
#+END_SRC
***** DONE Test your deb package
      CLOSED: [2020-06-04 四 16:16]
#+BEGIN_SRC shell
sudo dpkg -i <package> # install
sudo dpkg -r <appname> # remove
sudo dpkg -P <appname> # remove completely
dpkg -l | grep <appname> # find package
# remove unsuccessful installation
sudo mv /var/lib/dpkg/info/<packagename>.* /tmp/
sudo dpkg --remove --force-remove-reinstreq <packagename>
#+END_SRC
***** DONE Taking care of external dependencies
      CLOSED: [2020-06-04 四 16:22]
#+BEGIN_SRC shell
mkdir helloworld_1.0-1_arm64/debian
touch helloworld_1.0-1_arm64/debian/control
dpkg-shlibdeps -O path/to/binary/file >> control #need source files
#+END_SRC
***** DONE Run scripts before or after package installation and removal
      CLOSED: [2020-06-04 四 16:23]
Four files: postinst, preinst, postrm, and prerm are called maintainer scripts.
Such files live inside the DEBIAN directory and, as their names suggest, preinst
and postinst are run before and after installation, while prerm and postrm are
run before and after removal. They must be marked as executables. Also, remember
to set permissions: must be between 0555 and 0775.
