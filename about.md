---
layout: page
title: About
permalink: /about/
jump_links: ['2005', '2010', '2015']
---

I'm a 22-year-old software developer, born and raised in Edinburgh. Currently working as a full-stack (ReactJS/C&#35; Entity Framework) developer at [Managed Response Marketing](http://mrmbrand.com).

This site was created using [Jekyll](https://jekyllrb.com) and the source code can be found on [my github page](https://github.com/maxatkinson/maxatkinson.github.io).

### Contact me

[itsmaxatk@gmail.com](mailto:itsmaxatk@gmail.com)

### Music [[2015](#2015) / [2010](#2010) / [2005](#2005)]

{% for gig_hash in site.data.gigs %}
{% assign year = gig_hash[0] %}

{% if page.jump_links contains year %}
#### <a name="{{ year }}">{{ year }}</a> [[Back to top](#)]
{% else %}
#### {{ year }}
{% endif %}

{% assign gigs = gig_hash[1] | sort: 'date' | reverse %}
<ul>
  {% for gig in gigs %}
  {% if gig.act.name != "" %}
  <li>{{ gig.date | date: "%a, %-d %b" }}: <a href="{{ gig.act.url }}" target="_blank">{{ gig.act.name }}</a> @ <a href="{{ gig.venue.url }}" target="_blank">{{ gig.venue.name }}</a></li>
  {% endif %}
  {% endfor %}
</ul>
---
{% endfor %}
