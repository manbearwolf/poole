---
layout: post
title: "No Linenos Highlighter Line Numbering In Jekyll w/Only JS & CSS"
date: 2017-11-15
author: Matthew Bott
tags: [coding]
---

<script>new Clipboard('.btn');</script>

Here is how to create a line numbering in Jekyll without the uses of linenos, which is a command with highlighter [<a href="https://jekyllrb.com/docs/templates/#line-numbers" rel="nofollow" target="_blank">Source</a>].

Let's look at how the code works...

<!--more-->

SCSS
<div id="foo4">
{% highlight scss %}

pre {
    padding: 30px 30px 30px 40px;
    word-wrap: break-word;
    max-height: 800px;
    white-space: pre;
    overflow: auto;
    border: 1px solid #ddd;
    font-size: 14px;
    line-height: 1.6;

    code {
      color: inherit;
      background-color: transparent;
      padding: 0;

    }
    .line-number {
      display: block;
      float: left;
      border-right: 1px solid #ddd;
      font-size: 14px;
      line-height: 1.6;
      text-align: right;
      margin: 0 1em 0 -1em;
      -webkit-touch-callout: none;
      -webkit-user-select: none;
      -khtml-user-select: none;
      -moz-user-select: none;
      -ms-user-select: none;
      user-select: none;

      span {
        display: block;
        padding: 0 .5em 0 1em;
        color: #ccc;
      }
    }
    .cl {
      display: block;
      clear: both;
    }
  }
{% endhighlight %}
</div>
<!-- Trigger -->
<button class="btn" data-clipboard-target="#foo4">
Copy to clipboard
</button>

You can change the style in the pre, code, and line number classes.  Add these lines for cut and copy, etc. around the line numbering. ↓

Side Note
{% highlight scss %}
-webkit-touch-callout: none;
-webkit-user-select: none;
-khtml-user-select: none;
-moz-user-select: none;
-ms-user-select: none;
user-select: none;
{% endhighlight %}

JavaScript
<div id="foo5">
{% highlight javascript %}
(function() {
  var pre = document.getElementsByTagName('pre'), pl = pre.length;

  for (var i = 0; i < pl; i++) {
    pre[i].innerHTML = '<span class="line-number"></span>' + pre[i].innerHTML + '<span class="cl"></span>';

    var num = pre[i].innerHTML.split(/\n/).length;

    for (var j = 0; j < (num - 1); j++) {
      var line_num = pre[i].getElementsByTagName('span')[0];
      line_num.innerHTML += '<span>' + (j + 1) + '</span>';
    }
  }
})();
{% endhighlight %}
</div>
<!-- Trigger -->
<button class="btn" data-clipboard-target="#foo5">
Copy to clipboard
</button>

Pretty easy JavaScript (No JQuery needed) for the additions line numbering, itself. Note, the num variable in there, it can subtract or addition line numbers if you need more or less numbering. 

Example:
<p>See the Pen <a href="https://codepen.io/robott1982/pen/rYGwZb/" rel="nofollow" target="_blank">No-Linenos #2 (Jekyll) CSS Java Only!</a> by Matthew Bott (<a href="https://codepen.io/robott1982" rel="nofollow" target="_blank">@robott1982</a>) on <a href="https://codepen.io" rel="nofollow" target="_blank">CodePen</a>.</p>

This does have some drawbacks, like font size has to match, but looks fairly reasonable or better than linenos, I think, and is simple. Plus gets the job done, well. The original CodePen looked at... <a href="https://codepen.io/heiswayi/pen/jyKYyg" rel="nofollow" target="_blank">here</a>.

