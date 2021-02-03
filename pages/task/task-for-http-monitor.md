# -*- mode:org; coding: utf-8 -*-

#+TITLE:     task for http monitor
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

* tasks for http monitor using bash
** [2020]
*** [2020-12]
**** [2020-12-28 一]
***** read [[https://raymii.org/s/software/Bash_HTTP_Monitoring_Dashboard.html][Bash HTTP Monitor Dashboard]] [4/4]
 - [X] The first part between the square brackets is the name, the second part
   between the quotes is the URL you want to monitor. It can be just a domain,
   an IP or an actual URL, including port and such.
~urls[gists]="https://gist.github.com"~
 - [X] the default status code for a check, this is the syntax. The first part
   between the square brackets must match the urls[] part.
~statuscode[gist.github.com]=302~
 - [X] Execute the script and send the output to a file in your webservers
   documentroot:
~bash srvmon.sh > /var/www/index.html~
 - [X] set up a cronjob
~* * * * * /bin/bash /opt/srvmon/srvmon.sh > /var/www/index.html.tmp && /bin/mv
/var/www/index.html.tmp /var/www/index.html~
***** another example with curl
#+BEGIN_SRC shell
alias hstat="curl -o /dev/null --silent --head --write-out '%{http_code}\n'" $1
# Example:
# hstat www.google.com
# output is
# 200
#+END_SRC
***** another example with curl
#+BEGIN_SRC shell
curl -s -w 'Testing Website Response Time for :%{url_effective}\n\nLookup Time:\t\t%{time_namelookup}\nConnect Time:\t\t%{time_connect}\nAppCon Time:\t\t%{time_appconnect}\nRedirect Time:\t\t%{time_redirect}\nPre-transfer Time:\t%{time_pretransfer}\nStart-transfer Time:\t%{time_starttransfer}\n\nTotal Time:\t\t%{time_total}\n' -o /dev/null https://google.com
#+END_SRC
***** example with bash only
#+BEGIN_SRC shell
hstat(){ exec 3<>/dev/tcp/$1/80; echo -e "GET / HTTP/1.1\r\nhost: http://$1\r\nconnection: close\r\n\r\n" >&3; sed -n '1s/^HTTP\/1\.[01] //;s/ .*//;p' <&3;}
#+END_SRC
***** exampel with busybox only
#+BEGIN_SRC shell
hstat(){ echo -e "GET / HTTP/1.1\r\nhost: http://$1\r\nconnection: close\r\n\r\n" \ |busybox nc $1 80|busybox sed "1s/^HTTP\/1\.[10] //;s/ .*//;q";}
#+END_SRC
