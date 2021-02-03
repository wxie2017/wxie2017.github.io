# -*- mode:org; coding: utf-8 -*-

#+TITLE:     task for GNU make
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

* tasks for GNU make
** [2020]
*** [2020-05]
**** [2020-05-28 四]
***** DONE test new release 2.1.3 [3/3]
      DEADLINE: <2020-05-28 四>
 - [X] add 'ls' test for SparkStudio
 - [X] upgrade local SparkStudio version
 - [X] update sparksource.stdout to 2.1.3
*** [2020-06]
**** [2020-06-01 一]
***** DONE GNU make format: Makefile
      CLOSED: [2020-06-01 一 11:01]
#+BEGIN_SRC makefile
# comment
target (file to be created): prerequisities (file depended)
# commands must use TAB not spaces
	command1; \
	continue-command1;
	command2;
#+END_SRC
***** DONE define variables in Makefile
      CLOSED: [2020-06-01 一 11:05]
#+BEGIN_SRC makefile
VAR=--abc --help --verbose

target1: need-file1
	command1 $(VAR)
	command2 ${VAR}
#+END_SRC
***** DONE automatic variable in Makefile
      CLOSED: [2020-06-01 一 11:07]
    $@    the file name of the target
    $<    the name of the first prerequisite (i.e., dependency)
    $^    the names of all prerequisites (i.e., dependencies)
    $(@D)    the directory part of the target
    $(@F)    the file part of the target
    $(<D)    the directory part of the first prerequisite (i.e., dependency)
    $(<F)    the file part of the first prerequisite (i.e., dependency)
***** DONE Pattern rules
      CLOSED: [2020-06-01 一 11:10]
#+BEGIN_SRC makefile
# use the symbol % as a wildcard, to be expanded to any string of text
R_OPTS=--vanilla

Figs/%.pdf: R/%.R
    cd $(<D);R CMD BATCH $(R_OPTS) $(<F)
#+END_SRC
*** [2020-07]
**** [2020-07-02 四]
***** DONE list all targets on a Makefile [4/4]
      CLOSED: [2020-07-02 四 21:10]
      - CLOSING NOTE [2020-07-02 四 21:10] \\
        try it for sparksource
 - [X] read the original page
   [[https://diamantidis.github.io/tips/2020/07/01/list-makefile-targets][all targets]]
 - [X] default make target
#+BEGIN_SRC makefile
# the default target of `make` is `all`
# so when is do `make`, it runs `make all`
# change it to `help`
.DEFAULT_GOAL := help
.PHONY: help

help:
	@grep -E '^[a-zA-Z0-9_-]+:.*?## .*$$' $(MAKEFILE_LIST) \
	| sed -n 's/^\(.*\): \(.*\)##\(.*\)/\1\3/p' \
	| column -t  -s ' '
#+END_SRC
 - [X] add comment for each target as
#+BEGIN_SRC makefile
install: ## Install
	@echo "Installing..."

run: ## Run
	@echo "Running..."
#+END_SRC
 - [X] the final result is
#+BEGIN_SRC shell
make
#output:
# install Install
# run Run
#+END_SRC
