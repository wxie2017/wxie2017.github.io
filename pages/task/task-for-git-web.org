# -*- mode:org; coding: utf-8 -*-

#+TITLE:     task for webpage using git
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

* tasks for webpage using git
** [2020]
*** [2020-06]
**** [2020-06-09 二]
***** DONE study the mini-howto for git web
      CLOSED: [2020-06-10 三 15:40] DEADLINE: <2020-06-10 三>
      - CLOSING NOTE [2020-06-10 三 15:40] \\
        go over
[[https://kbroman.org/simple_site/][simple git website]]
Github Pages provide a simple way to make a website using Markdown and git.
The sites use Jekyll, a ruby gem, to convert Markdown files to html, and this
part is done automatically when you push the materials to the gh-pages branch of
a GitHub repository.

**** [2020-06-10 三]
***** DONE go through the process of making a git page web [1/1]
      CLOSED: [2020-06-12 五 18:44] DEADLINE: <2020-06-10 三>
      - CLOSING NOTE [2020-06-12 五 18:44] \\
        https://sparksource-cn.github.io/web/ is on-line.
 - [X] These GitHub Pages sites are constructed by having a gh-pages branch of a
   GitHub repository, with specific files layed out in a specific way.
****** directory layout
#+BEGIN_SRC shell
_includes/
_layouts/
_plugins/
_site/
assets/
pages/
.gitignore
License.md
Rakefile
ReadMe.md
_config.yml
index.md
#+END_SRC
****** directory explanation
The directories beginning with an underscore contain materials defining the
basic layout and style for the site.

The assets/ directory contains any non-Markdown materials for the site (e.g.,
images or example code). These files won’t be touched in the conversion but
will be just copied over as-is.

The pages/ directory contains Markdown files that will become html pages on your
site.

_site/ directory is for local testing purposes containing the actual site (with
Markdown files converted to html). You don’t want the _site/ directory in your
repository, so include that in the .gitignore file.
#+BEGIN_SRC shell
cat .gitignore
# exclude directory _site/ and its subdirectories
_site/
#+END_SRC
****** file explanation
The _config.yml file contains all sorts of configuration parameters (some of
which you’ll need to modify).

The Rakefile contains instructions for the conversion; you won’t modify this
file.

It’s best to always include License.md and ReadMe.md files. But you wouldn’t
need these to be placed on the website; they’d just be viewed in the repository
on GitHub.

The _config.yml file contains a line sort of like the following (but listing a
few more files), indicating files to not move to the final site.
#+BEGIN_SRC shell
exclude: ["ReadMe.md", "Rakefile", "License.md"]
#+END_SRC

index.md is the Markdown version of the main page for your site.
****** index.md file
The index.md file and the Markdown files in pages/ have
a header with a particular form:
#+BEGIN_SRC shell
---
layout: page
title: simple site
tagline: Easy websites with GitHub Pages
description: Minimal tutorial on making a simple website with GitHub Pages
---
#+END_SRC
In the conversion of the site from Markdown to html, this bit says that the
current file is to be converted with the “page” layout, and gives the title
and the (optional) “tagline.” The “description:” part gets converted into
<meta name="description" content="Minimal tutorial on..."> which, in principle,
may be used in the results of google searches.

The rest is basically plain Markdown.
 - [X] make an independent site
 - [X] git clone a sample site, e.g. https://github.com/SparkSource-cn/web
 - [X] edit _config.yml file to include your information
 - [X] Edit _includes/themes/twitter/default.html, edit the footer information
 - [X] Edit the index.md file, which will become the main page
 - [X] go into the pages/ directory and remove or rename and modify all of the Markdown files
 - [X] git init/git add ./git commit -m "Initial commit"/
 - [X] git branch -m master gh-pages
***** push everything into git [2/2]
 - [X] git remote add origin https://github.com/SparkSource-cn/web
 - [X] git push -u origin gh-pages
***** Check whether it worked: https://sparksource-cn.github.io/web
**** [2020-06-12 五]
***** DONE create a git personal site [8/8]
      CLOSED: [2020-06-12 五 18:53]
      - CLOSING NOTE [2020-06-12 五 18:53] \\
        just read through this
 - [X] The repository needs to be called username.github.io
 - [X] The site sits in the master branch rather than the gh-pages branch.
 - [X] Clone my kbroman.github.io repository
 - [X] Remove the .git directory
 - [X] Edit index.html, 404.html, README.md, and License.md
 - [X] Use git init, git add, git commit
 - [X] Create a new repository on GitHub named username.github.io
 - [X] Go back to the command line and do git remote add and git push -u origin master
