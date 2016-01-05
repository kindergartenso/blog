---
layout: post
category: note
series: 技术日记
title: 2016 技术日记 - 01 月
excerpt: 每天学到的知识点和有用的网站收录。
first_time: 2016.01.03 20:33:52
time: 2016.01.05 13:00:10
tags:
- 中文
- JavaScript
- HTML
- jQuery
- Jekyll
---

# 3 日

### 判断浏览器语言

- `navigator.language` 获取诸如 `en` 之类的字符串
- [JavaScript for detecting browser language preference](http://stackoverflow.com/questions/1043339/javascript-for-detecting-browser-language-preference)
- [RFC：语言的合法取值](http://www.ietf.org/rfc/bcp/bcp47.txt#)



### HTML `article` and `section`

- [MDN `<article>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/article)

> The HTML `<article>` element represents a self-contained composition in a document, page, application, or site, which is intended to be **independently distributable or reusable** (e.g., in syndication). This could be a forum post, a magazine or newspaper article, a blog entry, an object, or any other independent item of content. Each `<article>` should be identified, typically by including a heading (`<h1>`-`<h6>` element) as a child of the `<article>` element.

> When an `<article>` element is nested, the inner element represents an article related to the outer element. For example, the comments of a blog post can be `<article>` elements nested in the `<article>` representing the blog post.
> Author information of an `<article>` element can be provided through the `<address>` element, but it doesn't apply to nested `<article>` elements.
> The publication date and time of an `<article>` element can be described using the `datetime` attribute of a `<time>` element. Note that the pubdate attribute of `<time>` is no longer a part of the *W3C HTML 5 standard*.

- [MDN `<section>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/section)

> The HTML `<section>` element represents a generic section of a document, i.e., a thematic grouping of content, typically with a heading. Each `<section>` should be identified, typically by including a heading (`<h1>`-`<h6>` element) as a child of the `<section>` element.



### jQuery `after`

- 在元素同级后方插入元素
- [jQuery API](http://api.jquery.com/after/)





# 5 日

### 解决 Jekyll markdown 新窗口打开连接的问题

我使用的 `rdiscount` markdown 不能识别 [Kramdown](http://kramdown.gettalong.org/) `[link](url){:target="_blank"}` 的形式，之前都是在 md 文件里手动写 `<a target="_blank" href="..."></a>` 的。现在[找到的解决办法](http://stackoverflow.com/questions/4425198/markdown-target-blank)是，使用 jQuery 判断页面中的链接是否是本站下（同域）的，如果不是，就添加 `target` 属性。

{% highlight js %}
$(document.links).filter(function() {
    return this.hostname !== window.location.hostname;
}).attr('target', '_blank');
{% endhighlight %}