---
layout: post
title: "LunrJS vs Simple Jekyll Search"
date: 2017-11-01
author: Matthew Bott
tags: [coding]
---

<script>new Clipboard('.btn');</script>

Search bars can be complicated, but I found a couple kinds that work with static websites.

<!--more-->

## [LunrJS](https://lunrjs.com/){:target="_blank" rel="nofollow"}

<p>See the Pen <a href="https://codepen.io/robott1982/pen/bYoYrr/" rel="nofollow" target="_blank">LunrJS Search</a> by Matthew Bott (<a href="https://codepen.io/robott1982" rel="nofollow" target="_blank">@robott1982</a>) on <a href="https://codepen.io" rel="nofollow" target="_blank">CodePen</a>.</p>

The first is LunrJS.  It is suppose to be fast in browsers, but can be heavy.  

In this example we store the search information in a [JSON](https://en.wikipedia.org/wiki/JSON){:target="_blank" rel="nofollow" title="Wiki"} file. Note the older versions of LunrJS that is used. Newer versions are harder to use for Jekyll.

Here is the .json file before compiled...

LunrJS JSON Setup (search_data.json) ↓
<div id="foo6">
{% highlight json %}
{% raw %}
---
layout: null
---
{
  {% for post in site.posts %}
    "{{ post.url | slugify }}": {
      "title": "{{ post.title | xml_escape }}",
      "content"	 : "{{post.content | strip_html | strip_newlines | remove:  "	" | escape | remove: "\"}}",
      "url": "{{ site.baseurl }}{{ post.url | xml_escape }}",
      "author": "{{ post.author | xml_escape }}",
      "categories": "{% for category in post.categories %}{{ category }}{% unless forloop.last %}, {% endunless %}{% endfor %}"
    }
    {% unless forloop.last %},{% endunless %}
  {% endfor %}

  {% for page in site.pages %}
    {% if page.url == '/speaking/index.html' or page.url == '/if-rudyard-kipling/index.html' or page.url == '/about/index.html' or page.url == '/contact/index.html' or page.url == '/sudo-disclaimer/index.html' %}
      ,

      "{{ page.url | slugify }}":  {
        "title": "{{ page.title | xml_escape }}",
      "content"	 : "{{page.content | strip_html | strip_newlines | remove:  "	" | escape | remove: "\"}}",
        "url": "{{ site.baseurl }}{{ page.url | xml_escape }}"
      }
    {% endif %}
  {% endfor %}
}
{% endraw %}
{% endhighlight %}
</div>
<!-- Trigger -->
<button class="btn" data-clipboard-target="#foo6">
Copy to clipboard
</button>

See the entire gist file tree on GitHub... <a href="https://gist.github.com/manbearwolf/073b7c47c96c38f38698e533176a1ee0" rel="nofollow" target="_blank">here</a>

## [Simple Jekyll Search](https://github.com/christian-fei/Simple-Jekyll-Search){:target="_blank" rel="nofollow"}

<p>See the Pen <a href="https://codepen.io/robott1982/pen/KyXZQO/" rel="nofollow" target="_blank">Simple Jekyll Search</a> by Matthew Bott (<a href="https://codepen.io/robott1982" rel="nofollow" target="_blank">@robott1982</a>) on <a href="https://codepen.io" rel="nofollow" target="_blank">CodePen</a>.</p>

The second example is Simple Jekyll Search, which is fast and easily, liked more.
Here is the .json file before compiled...

Simple Jekyll Search JSON Setup (search.json) ↓
<div id="foo7">
{% highlight json %}
{% raw %}
---
layout: null
---
[
  {% for post in site.posts %}
    {
    
      "title"    : "{{ post.title | escape }}",
      "url"      : "{{ site.baseurl }}{{ post.url }}",
      "tags"     : "{{ post.tags | join: ', ' }}",
      "date"     : "{{ post.date }}"
      
    } {% unless forloop.last %},{% endunless %}
  {% endfor %}
]
{% endraw %}
{% endhighlight %}
</div>
<!-- Trigger -->
<button class="btn" data-clipboard-target="#foo7">
Copy to clipboard
</button>

See the entire gist file tree on GitHub... <a href="https://gist.github.com/manbearwolf/f86195a237ba5d8f5d5f67e147acdbe1" rel="nofollow" target="_blank">here</a>

<b>Notes:</b>
* That it can be setup to write the database (json).
* Both use .json files.  We should delete any fields we do not use in them.
* It best operates in sepearate files (less errors this way).
* Loading it on one page should work and be used.
* Just LunrJS requires JQuery to load.

<div class="dota">
<a href="https://github.com/christian-fei/Simple-Jekyll-Search" rel="nofollow" target="_blank">Simple Jekyll Search</a> on GitHub.
</div>
