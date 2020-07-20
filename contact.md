---
layout: default
title: Contact
permalink: /contact/
icon_class: envelope
---

<h3 style ='font-size:110%'><b>Email</b></h3>
<span style="font-size:110%;">Feel free to email us at [{{ site.email }}](mailto:{{ site.email }})</span>

<h3 style ='font-size:110%'><b>Newsletter</b></h3>
<p style="font-size:110%;">Follow our newsletter to keep informed of all the events we have going on! <a href='http://beesbeesbees.com/'>newsletter link</a></p>

<h3 style ='font-size:110%'><b>Social Media</b></h3>
<p style = 'text-align:center'>
<ul class="icons">
     <li><a href="https://www.facebook.com/{{ site.facebook_page| cgi_escape | escape }}" class="icon circle fa-facebook" target="_blank"><span class="label">Facebook</span>         </a></li>
     <li><a href="https://www.instagram.com/nu_csa/" class="icon circle fa-instagram" target="_blank"><span class="label">Instagram</span></a></li>
     <li><a href="https://linktr.ee/nu_csa" class="icon circle fa-tree" target="_blank"><span class="label">LinkTree</span></a></li>
     {%- if site.youtube_username -%}<li><a href="https://youtube.com/{{ site.youtube_username| cgi_escape | escape }}" class="icon circle fa-youtube" target="_blank"><span          class="label">Youtube</span></a></li>{%- endif -%}
</ul>
</p>
