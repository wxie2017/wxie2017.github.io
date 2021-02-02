# -*- mode:org; coding: utf-8 -*-

#+TITLE:     task for gitlab custom domain
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

* tasks for setting up gitlab custom domain for webpages
** [2020]
*** [2020-12]
**** [2020-12-28 一]
***** From your project's dashboard, go to ~Settings > Pages > New Domain~
***** Add your domain to the first field: mydomain.com
***** If you have an SSL/TLS digital certificate and its key, add them to their respective fields. If you don't, just leave the fields blank.
***** Click on Create New Domain.
***** Finally, access your domain control panel and create a new DNS A record pointing to the IP of GitLab Pages server:
#+BEGIN_SRC
mydomain.com A 35.185.44.232
#+END_SRC
***** You can also add subdomains: ~Add the subdomain to the first field: subdomain.mydomain.com~
***** Then create a new DNS CNAME record pointing to myusername.gitlab.io:
#+BEGIN_SRC
subdomain.mydomain.com CNAME myusername.gitlab.io
#+END_SRC
