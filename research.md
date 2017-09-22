---
layout: default
title: Research
---
<div class="container main">
  <div class="row">
    <header>
      <center><span itemprop="name"><h1>{{ page.title }}</h1></span></center>
      <center><p>{{ page.date | date: "%-d %b %Y" }}</p></center>
      <center><img class="icon icons8-Light-On" width="25" height="25" src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADIAAAAyCAYAAAAeP4ixAAADaUlEQVRoQ+2Z/ZFNQRDFz0ZABogAESACRIAIEAEiQASIYIkAESACZEAE1K9qDuPae6e7996rbL35Z1+97Znu09/d70hn5BztgOND43F1S157APnRAGzKa9PHG4ADkIwrHiyS0NbHRnslcSdNGrXIY0mXJd2T9C3NpXbhvKRjSe8lwX/xRIG8lnRTEtq9sQMYQLyVhBXfSLq1FhAeftesMgIDc0Bfl8Q9uxT3sCbvIJxdbipjD+JTe2foBVGLwGwKZlrg7jQXuDjSXvv/F0kPJWHt/lBAAR8GweUMkB4Mn61pBH/RNMf3X5twaB5h+2CHFkvhKhea9NARe9ByTA/d0BLWQBbIVNmAwZexFgAIypdBi9xt9ABCYGJvzt2GT54GCCDcR+HzCBbWYJMMBQCcmOLgriUwVSC4CCAQ5FUDMdTaAgFgiDEUARi7WfjNKhDcCR8OpcagNE7xxAxuljoVILgQwU1M4F5Zd5oTEOviVsTM7ROy2SKwCpDPknAtMk00sKPatZJwrUvRS5X06wDHGtF6kZEHWkBglVTgZy1Cen0k6bmkB1kJg/TPJN2X9CTSY1XrCIF4reLDQRCQUSzdLJJQQidrEbcPKbOHJPlNZPcl8MNzfg+ErEEg87c//YO7jK2Sej4Ruf7otfr01wOheXNf9a+AOC3PyZVuGnmQAWsP12Kg2ixGHOxUXj5vcRCezmFTIO6JmCNIk1sc0vrTbA+XzVqljJJE68yYsnoWSF95U4yCYMqdQwWIq3upSx0AcledquqVXos7fZpeM1Zc0UtddcUifRtx6hG1WagfmdMtfNUi9g5nsNF6aBQe/fqnPG1WLWLhXCCrYEo7rJM0kwVixrxFde93XViIYStzmDQZpvq48EIjtdHMAOm111dd/JsMdi45Qzj7fW+tiLcnJStHgYxcoF8NMaKOtiBMl3Tatmy/AsqsZ39ZPwokssa0hiMB60QxVy9G69m/3DcKhFUNj5Pr57YmvZajcbJkPfjBF36rbeOjgnleidJHFTl8b7WHGqfo4BWlGwIwwQHIjKqsac/5XubNaXY1Ra720MS1POe7Jvx3QMgwFMalmb48cywFzNoWcS2JBGl65tgTCLwAQ//kn9am/OmrKIjDn5wj2tgqa015GxTfry58z2xt18oocVXaMwPkJ47N1DPl+lOgAAAAAElFTkSuQmCC"></center>
    </header>
  </div>
  <div class="row">
  <div class="col-md-1"></div>
  <div class="col-md-8 offset-md-1">
  <div markdown="1">
  My research interests include multiagent systems, mobile computing, cloud applications architecture, embedded linux systems, topological data analysis and catastrophe theory. With the exception of cloud applications architecture, they all stem from courses completed during my master's studies at the Faculty of Mathematics and Information Science, Warsaw University of Technology. I developed an interest in cloud applications becuase of my experience developing such applications as a freelance developer.
  
  The blog posts listed below are grouped by the research projects they belong to:
  </div>
    
  {% assign projects = site.posts | group_by: "project" %}
  {% for project in projects %}
    <h3>{{ project.name }}</h3>
    {% for post in project.items %}
      {{forloop.index}}. <a href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>{% if forloop.last == false %},&nbsp;&nbsp;{% endif %}
    {% endfor %}
  {% endfor %}
  </div>
  </div>
</div>
