---
layout: default
title: Contact
permalink: /contact/
icon_class: envelope
---

### <font size = 6> Email </font>
<font size = 4><span style="color:black;">Feel free to email us at [{{ site.email }}](mailto:{{ site.email }})</span></font>

### <font size = 6> Newsletter </font>
<font size = 4><span style="color:black;">Follow our newsletter to keep informed of all the events we have going on at [newsletter link] (http://beesbeesbees.com/)</span></font>

### <font size = 6> Social Media </font>
<ul class="icons">
     <li><a href="https://www.facebook.com/{{ site.facebook_page| cgi_escape | escape }}" class="icon circle fa-facebook" target="_blank"><span class="label">Facebook</span>         </a></li>
     <li><a href="https://www.instagram.com/nu_csa/" class="icon circle fa-instagram" target="_blank"><span class="label">Instagram</span></a></li>
     <li><a href="https://linktr.ee/nu_csa" class="icon circle fa-tree" target="_blank"><span class="label">LinkTree</span></a></li>
     {%- if site.youtube_username -%}<li><a href="https://youtube.com/{{ site.youtube_username| cgi_escape | escape }}" class="icon circle fa-youtube" target="_blank"><span          class="label">Youtube</span></a></li>{%- endif -%}
</ul>
