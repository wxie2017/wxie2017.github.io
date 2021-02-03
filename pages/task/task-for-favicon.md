# -*- mode:org; coding: utf-8 -*-

#+TITLE:     task for favicon
#+AUTHOR:    Wensheng Xie
#+EMAIL:     wxie@member.fsf.org
#+LANGUAGE:  en
#+OPTIONS: H:2 num:nil toc:nil \n:nil @:t ::t |:t ^:{} _:{} *:t TeX:t LaTeX:t
#+STYLE: <link rel="stylesheet" type="text/css" href="org.css" />
#+LATEX_CLASS: report
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

* tasks for favicon
** [2020]
*** [2020-12]
**** [2020-12-24 四]
***** short version [2/2]
 - [X] HTML file for the browser
#+BEGIN_SRC html
<link rel="icon" href="/favicon.ico" /><!-- 48×48 -->
<link rel="icon" href="/icon.svg" type="image/svg+xml" sizes="any" />
<link rel="apple-touch-icon" href="/apple.png" /><!-- 180×180 -->
<link rel="manifest" href="/manifest.webmanifest" />
#+END_SRC
 - [X] web app manifest
#+BEGIN_SRC js
// manifest.webmanifest
{
  "icons": [
    { "src": "/192.png", "type": "image/png", "sizes": "192x192" },
    { "src": "/512.png", "type": "image/png", "sizes": "512x512" }
  ]
}
#+END_SRC
***** long version [5/5]
 - [X] sticking to a single 48×48
 - [X] https://example.com website should have a favicon on
   https://example.com/favicon.ico.
 - [X] A single SVG icon with light/dark version for modern browsers.
 - [X] 180×180 PNG image for Apple devices
 - [X] Web app manifest with 192×192 and 512×512 PNG icons for Android
***** build our Ultimate Favicon Set [6/6]
 - [X] Prepare the SVG
Be sure that the SVG image is square.
Save your file as icon.svg.
open your SVG file in a text editor.
#+BEGIN_SRC
  <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 500 500">
+   <style>
+     @media (prefers-color-scheme: dark) {
+     .a { fill: #f0f0f0 }
+     }
+   </style>
-   <path fill="#0f0f0f" d="…" />
+   <path class="a" fill="#0f0f0f" d="…" />
  </svg>
#+END_SRC
 - [X] Create an ICO file
Open your icon.svg file in GIMP.
Accept rendering SVG to raster. Set width and height to 48 pixels. Export file
to favicon.ico using 32 bpp, 8-bit alpha, no palette settings.
To include a separate 16×16 version of an icon:
    Open favicon.ico with 48×48 icon.
    Create a new layer with 16×16 size.
    Put a 16×16 version of an icon into this layer.
    Export the file. GIMP will save each layout as a separate version of an icon.
 - [X] Create PNG images
Open your source SVG file in a raster graphics editor again and create a
512×512 image. Export it as icon-512.png. Scale the image to 192×192 and
export it to icon-192.png. Now scale the image itself to 140×140 and set the
canvas to 180×180, and export as apple-touch-icon.png.
 - [X] Optimize PNG and SVG files
#+BEGIN_SRC shell
magick in.png -background none -resize 128x128 -density 128x128 out.ico
# or
convert -resize x16 -gravity center -crop 16x16+0+0 input.png -flatten -colors 256 -background transparent output/favicon.ico
#+END_SRC
 - [X] Add icons to HTML
#+BEGIN_SRC html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <title>My website</title>
    <meta name="viewport" content="width=device-width,initial-scale=1" />
    <link rel="icon" href="/favicon.ico" />
    <link
      rel="icon"
      type="image/svg+xml"
      sizes="any"
      href="<%=
     require('./icon.svg').default
   %>"
    />
    <link
      rel="apple-touch-icon"
      href="<%=
     require('./apple-touch-icon.png').default
   %>"
    />
  </head>
  <body></body>
</html>
#+END_SRC
 - [X] Separate icon for staging
Create a favicon-dev.ico with the same logo, but invert the colors (or do
something else that makes sense for you). Same for SVG, create icon-dev.svg.
Replace icons in your HTML template depending on
~process.env.NODE_ENV === 'production' condition~
#+BEGIN_SRC html
<!doctype html>
  <html lang="en">
    <head>
      <meta charset="utf-8">
      <title>My website</title>
      <meta name="viewport" content="width=device-width,initial-scale=1">
-     <link rel="icon" href="/favicon.ico">
+     <link rel="icon" href="<%=
+       process.env.NODE_ENV === 'production'
+         ? '/favicon.ico'
+         : require('./favicon-dev.ico').default
+     %>">
      <link rel="icon" type="image/svg+xml" sizes="any" href="<%=
-       require('./icon.svg').default
+       process.env.NODE_ENV === 'production'
+         ? require('./icon.svg').default
+         : require('./icon-dev.svg').default
      %>">
      <link rel="apple-touch-icon" href="<%=
        require('./apple-touch-icon.png').default
      %>">
    </head>
    <body></body>
  </html>
#+END_SRC
