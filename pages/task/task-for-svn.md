# -*- mode:org; coding: utf-8 -*-

#+TITLE:     task for svn
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

* tasks for svn
** [2020]
*** [2020-06]
**** [2020-06-02 二]
***** company svn server address is (can be input to browser):
 [[https://192.168.2.103/svn/CompanyBusiness]] xiewensheng:111111
 [[https://sparksourceserver/svn/CompanyBusiness]]
***** DONE The essential Subversion lifecycle is the following: [5/5]
      CLOSED: [2020-06-02 二 14:18] DEADLINE: <2020-06-02 二>
 - [X] Check out a project (a directory path) from a repository.
 - [X] In that project directory, create or edit files and subdirectories.
 - [X] Update your local copy from the repository, picking up changes your team members may have made since your last update.
 - [X] Go to step 2. If you're ready to commit your changes, go to step 5.
 - [X] Commit your changes to the repository. Go to step 2.
***** DONE check out the project first time
      CLOSED: [2020-08-21 五 21:13]
      - CLOSING NOTE [2020-08-21 五 21:13] \\
        work via another computer (win)
#+BEGIN_SRC shell
cd ~/work/sparksource/company
svn checkout https://192.168.2.103/svn/CompanyBusiness CompanyBusiness
Username:
Password for 'user':
#+END_SRC
***** DONE update and commit
      CLOSED: [2020-08-21 五 21:13]
      - CLOSING NOTE [2020-08-21 五 21:13] \\
        use windows computer
#+BEGIN_SRC shell
cd ~/.subversion
rm -rf auth
export EDITOR=emacs
svn update
svn add -m "messages" [file-name]
svn commit -m "messages" [file-name]
svn log -v
svn status
svn help
#+END_SRC
