---
layout: frontpage
title: wxie2017
description: wxie2017 is a free software believer who is trying to be a freelancer working with free software.
keywords: wxie, free software, freelancer, CTT
---


<iframe title="FSF Fundraiser Banner"
  src="//static.fsf.org/nosvn/banners/202311fundraiser/" scrolling="no"
  style="width: 100%; height: 150px; display: block; margin: 0; border: 0 none; overflow: hidden;">
</iframe>

<div class="navbar">
  <div class="navbar-inner">
      <ul class="nav">
          <li><a href="{{ BASE_PATH }}/assets/cv.pdf">cv</a></li>
<!-- no github anymore         <li><a href="https://github.com/wxie2017">github</a></li>  -->
          <li><a href="https://gitlab.com/wxie2017">gitlab</a></li>
          <li><a href="https://savannah.gnu.org/projects/www-zh-cn/">GNU/CTT</a></li>
          <li><a href="https://community.mozilla.org/groups/mozilla-china-l10n/">Mozilla China L10N</a></li>
      </ul>
  </div>
</div>

<table class="wide">
<tr>
  <td class="left">
    <a href="https://yulifeclub.gitlab.io/">Yu-Life Toastmasters Club</a>
  </td>
  <td class="right">
    <a href="https://schools-disappeared-in-china.gitlab.io/webpages/schools.html">Schools Disappeared in China</a>
  </td>
</tr>
<tr>
  <td class="left">
    <a href="https://www.gnu.org/">GNU Home</a>
  </td>
  <td class="right">
    <a href="https://www.fsf.org/">FSF Frontpage</a>
  </td>
</tr>
</table>

<div class="navbar">
  <div class="navbar-inner">
      <ul class="nav">
          <li><a href="https://www.gnu.org/help/help.html">Help GNU</a></li>
      </ul>
  </div>
</div>

<div id="freedom-iframe-container" style="position: relative; padding-top: calc(60% + 100px); width: 100%;">
<iframe src="https://www.fsf.org/videos/escape-to-freedom/" scrolling="no" style="overflow: hidden; margin: 0; border: 0 none; display: block; position: absolute; width: 100%; height: 100%; top: 0;"></iframe>
</div>
<script>
// @license magnet:?xt=urn:btih:1f739d935676111cfff4b4693e3816e664797050&dn;=gpl-3.0.txt GPL-3.0-or-later
window.onmessage = function (e) { if (e.data.hasOwnProperty("freedom-iframe-height")) { document.getElementById('freedom-iframe-container').style.height=`${e.data["freedom-iframe-height"]}px`;  document.getElementById('freedom-iframe-container').style["padding-top"]="unset";} };
// @license-end
</script>
