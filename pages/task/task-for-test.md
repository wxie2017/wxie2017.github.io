# -*- mode:org; coding: utf-8 -*-

#+TITLE:     task for test frame
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

* tasks for test framework using 'make' and 'git diff'
** [2020]
*** [2020-05]
**** [2020-05-23 六]
***** DONE read testframe website
      DEADLINE: <2020-05-23 六>
[[https://chrismorgan.info/blog/make-and-git-diff-test-harness/][Using make and git diff for a simple and powerful test harness]]
**** [2020-05-24 日]
***** DONE go through the file Makefile [6/6]
      DEADLINE: <2020-05-24 日>
#+BEGIN_SRC makefile
rwildcard = $(foreach d,$(wildcard $1*),$(call rwildcard,$d/,$2) $(filter $2,$d))

.PHONY: test
test: $(patsubst %.test,%.stdout,$(call rwildcard,,%.test))

%.stdout: %.test
	./$< > $@ 2> $(patsubst %.stdout,%.stderr,$@) \
		|| (touch --date=@0 $@; false)
	git diff --exit-code --src-prefix=expected/ --dst-prefix=actual/ \
		$@ $(patsubst %.stdout,%.stderr,$@) \
		|| (touch --date=@0 $@; false)
#+END_SRC
  - [X] have GNU Make installed and are using Git
  - [X] Paste the code above into a file called Makefile.
  - [X] Create an executable file (mode +x) called [sparksource].test that contains the script of what you want to test.
  - [X] Run make test (the test run will seem to succeed, since the expected output hasn’t been added to Git yet)
  - [X] Review the contents of [sparksource].stdout and [sparksource].stderr which have just been created, that they match what you expected.
  - [X] Run git add sparksource.test sparksource.stdout sparksource.stderr
***** DONE detailed explanation [5/5]
      DEADLINE: <2020-05-24 日>
 - [X] ensuring that all of the tests will be run each time you run make test.
mark all test as .PHONY
#+BEGIN_SRC makefile
.PHONY: test $(patsubst %.test,%.stdout,$(call rwildcard,,%.test))
#+END_SRC
 - [X] if you just once want to run all the tests
#+BEGIN_SRC shell
 make --always-make test
#+END_SRC
 - [X] If you want to run tests concurrently
#+BEGIN_SRC shell
 make --jobs=8 test
#+END_SRC
 - [X] $(patsubst %.test,%.stdout,$(call rwildcard,,%.test))
“find all *.test files recursively ($(call rwildcard,,%.test)), then change
each one’s ‘.test’ extension to ‘.stdout’ ($(patsubst
%.test,%.stdout,…))”.
 - [X] %.stdout: %.test
	./$< > $@ 2> $(patsubst %.stdout,%.stderr,$@) \
		|| (touch --date=@0 $@; false)
	git diff --exit-code --src-prefix=expected/ --dst-prefix=actual/ \
		$@ $(patsubst %.stdout,%.stderr,$@) \
		|| (touch --date=@0 $@; false)
This rule says “any file with extension ‘.stdout’ can be created based upon
the file with the same base name but the extension ‘.test’, by running these
two commands”.

    $@ expands to the name of the target, which we’ll call sparksource.stdout.
    $< expands to the name of the first prerequisite, which in this case will be sparksource.test.

    Run ./sparksource.test, piping stdout to sparksource.stdout and stderr to sparksource.stderr.
    If that fails: zero sparksource.stdout’s mtimeThat is.
    Run git diff in such a way as to print any unstaged changes to those files.
    If there were any unstaged changes to those files, then zero foo.stdout’s
    mtime.
