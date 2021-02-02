# -*- mode:org; coding: utf-8 -*-

#+TITLE:     task for printer
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

* tasks for installing printer in Debian
** [2020]
*** [2020-11]
**** [2020-11-05 四]
***** install printer packages
#+BEGIN_SRC shell
sudo aptitude install cups
#+END_SRC
***** open printer administration webpage
#+BEGIN_SRC html
http://localhost:631
#+END_SRC
***** click on 'add printer' button to search available printers
***** customization the cups [4/4]
~/etc/cups/cupsd.conf~ is the file to edit.
 - [X] print area
~Listen localhost:631~ # one computer
Listen 0.0.0.0:631   # local network
 - [X] priviledge for printers
#<Location />
# Order allow,deny
# Allow localhost
#</Location>

<Location />
Order deny,allow
Allow From 192.168.1.* # printer ip
</Location>
 - [X] start service
#+BEGIN_SRC shell
sudo /etc/init.d/cups restart
#+END_SRC
 - [X] search for printers
input something like
~http://192.168.1.102:631/printers/Officejet-5600-series~
into browser
**** [2020-11-12 四]
***** commandline commands for printers [7/7]
 - [X] see a list of printer, local or network
#+BEGIN_SRC shell
lpstat -p -d
#+END_SRC
 - [X] print to a specific printer
#+BEGIN_SRC shell
lp -d printer filename
# or
lpr -P printer filename
#+END_SRC
 - [X] specify printer options
#+BEGIN_SRC shell
lpoptions -p printer -l # list options
lp -o landscape -o fit-to-page -o media=A4 filename.jpg
lpr -o portrait -o fit-to-page -o media=A4 filename.jpg
#+END_SRC
 - [X] printer copies
#+BEGIN_SRC shell
lp -n num-copies -o collate=true filename
lpr -#num-copies -o collate=true filename
#+END_SRC
 - [X] printer job
#+BEGIN_SRC shell
# cancel job
cancel job-id
lprm job-id
# move job to another printer
lpmove job-id destination
#+END_SRC
 - [X] remove a printer
#+BEGIN_SRC shell
lpadmin -x PrinterName
#+END_SRC
 - [X] remove authentication (make sure the server side also set to no
   autherication)
#+BEGIN_SRC shell
lpadmin -p <queue-name> -o auth-info-required=none
#+END_SRC
**** [2020-11-13 五]
***** driverless printing [2/2]
 - [X] devices support driveless printing are listed
 [[https://support.apple.com/en-gb/HT201311][AirPrint device list from Apple]]
 - [X] install driveless printer for Debian
 [[https://wiki.debian.org/CUPSDriverlessPrinting][Driverless printing with CUPS]]
***** installing driverless printing [5/5]
 - [X] ~CreateIPPPrinterQueues All~ is uncommented in file _/etc/cups/cups-browsed.conf_
 - [X] ~systemctl restart cups-browsed~ is executed.
 - [X] Obtain the URI of a printer: ~driverless~ or ~driverless list~
 - [X] try ~ippfind -T 5~ if possible
 - [X] try ~avahi-browse -rt _ipp._tcp~ and ~avahi-browse -rt _uscan._tcp~
***** installing driverless from CUPS webinterface
1. Open the [[localhost:631][web interface]] and choose ~Administration~. Select ~Add Printer~.
2. Your printer will be under the ~Discovered network Printers:~, probably with
   more than one entry. Choose the entry that contains the word driverless and
   move on to ~Continue~.
3. Check that Connection is ipp://... and ~Continue~ to the next page.
4. Under Model there should be an option of driverless, cups-filters. This
   option uses the _cups-filters_ PPD generator. Select and activate ~Add Printer~.
