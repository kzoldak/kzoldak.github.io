---
layout: post
title: Pygments
comments: true
---

Today I discovered a neat tool for displaying code within Jupyter notebooks. It invoves the use of [Pygments](https://pygments.org/). Pygments 

{% highlight ruby %}
from pygments import highlight
from pygments.lexers import PythonLexer
from pygments.formatters import HtmlFormatter
import IPython


with open('out.json') as f:
    code = f.read()
formatter = HtmlFormatter()
IPython.display.HTML('<style type="text/css">{}</style>{}'.format(formatter.get_style_defs('.highlight'), 
                                                                  highlight(code, PythonLexer(), 


{% endhighlight %}

This will display what is within the `out.json` file. 