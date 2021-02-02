# -*- mode:org; coding: utf-8 -*-

#+TITLE:     task for bash
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

* tasks for test framework using bash
** [2020]
*** [2020-10]
**** [2020-10-28 三]
***** DONE read about bash error handling [1/1]
      CLOSED: [2020-10-28 三 16:53]
      - CLOSING NOTE [2020-10-28 三 16:53] \\
        learned
 - [X] [[https://wizardzines.com/comics/bash-errors/][Bash error handling]]
****** by default, bash will continue after errors
****** ~set -e~ stops the script on errors
#+BEGIN_SRC shell
set -e
unzip fle.zip # script stops here because of typo
#+END_SRC
****** by default, unset variables don't error
#+BEGIN_SRC shell
rm -r "$HOME/$SOMEPTH" # when $SOMEPTH doesn't exist, use an empty string
#+END_SRC
****** ~set -u~ stops the script on unset variables
#+BEGIN_SRC shell
set -u
echo $UNSET #script stops here because $UNSET not known
#+END_SRC
****** by default, a command failing doesn't fail the whole pipeline
#+BEGIN_SRC shell
curl 404.html | grep 'panda' #curl failed, but grep ok, so all ok
#+END_SRC
****** ~set -o pipefail~ prevents this
#+BEGIN_SRC shell
set -euo pipefail #put this at the beginning of your scripts
#+END_SRC
***** summary
#+BEGIN_SRC shell
#!/usr/bin/env > #!/bin/bash

set -o pipefail  # trace ERR through pipes
set -o errtrace  # trace ERR through 'time command' and other functions
set -o nounset   ## set -u : exit the script if you try to use an uninitialised variable
set -o errexit   ## set -e : exit the script if any statement returns a non-true return value

exec 2>"$stderr_log" # standard error output
#+END_SRC
