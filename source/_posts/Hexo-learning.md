---
title: Hexo learning
tags:
  - hexo
categories:
  - Technology
  - Hexo
date: 2016-08-17 20:27:14

---
To start to learn Hexo is a very insteresting thing. It takes time to understand the structure and learn to use git tools, as well as the markdown language.
Following below links to start hexo travel. 
## Basic about Hexo
> * Hexo main website. [Hexo](https://hexo.io/zh-cn/docs/variables.html)
> * Hexo and Git, chinese website [Hello dog](https://wsgzao.github.io/post/hexo-guide/)
> * Theme, [NexT](http://theme-next.iissnan.com/third-party-services.html)
> * **Markdown** editor, this is web editor [Cmd Markdown](https://www.zybuluo.com/mdeditor)
> * **Tag plugins**. Hexo official [site](https://hexo.io/docs/tag-plugins.html)
<!-- more-->

------
## Examples for plugins.

### 1. If we would like to do a quote, we use below

```mkd
{% blockquote David Levithan, Wide Awake %}
Do not just seek happiness for yourself. Seek happiness for all. Through kindness. Through mercy.
{% endblockquote %}
```

### 2. If we want to quote a image, it is better to use asset.
```mkd 
{% asset_img example.jpg This is an example image %}
```

### 3. To quote a code, we can reference to the [**link**](https://hexo.io/zh-cn/docs/tag-plugins.html#代码块)
```mkd
{% codeblock [title] [lang:language] [url] [link text] %}
code snippet
{% endcodeblock %}
```
it will render like 
{% codeblock [title] %}
code snippet
{% endcodeblock %}

### 4. Tag plugs example
```
{% centerquote %}
blah blah blah
Wanlu {% endcenterquote %}
```

will render as
{% centerquote %}
blah blah blah
Wanlu {% endcenterquote %}

### 5. Insert image example
```
{% asset_img [class names] /path/to/image [width] [height] [title text [alt text]] %}
```
which will render as
{% asset_img image_ex.jpg How to insert image %}

