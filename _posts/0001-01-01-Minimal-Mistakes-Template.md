---
excerpt: "Minimal-Mistakes发布模板，包括一些边缘案例"
categories:
  - Others
tags:
  - Tool
---

# 插入图像方法

```markdown
{% raw %}![alt]({{ site.url }}{{ site.baseurl }}/assets/images/filename.png){% endraw %}
![]()
```

或者

```html
{% raw %}<img src="{{ site.url }}{{ site.baseurl }}/assets/images/filename.jpg" alt="">{% endraw %}
<img src="" alt="">
```

当访问网络上的图片出现http 403防止盗链的错误时，使用

```markdown
{% raw %}![alt](https://images.weserv.nl/?url={{ site.url }}{{ site.baseurl }}/assets/images/filename.png){% endraw %}
![](https://images.weserv.nl/?url=)
```

或者

```html
{% raw %}<img referrerPolicy="no-referrer" src="{{ site.url }}{{ site.baseurl }}/assets/images/filename.jpg" alt="">{% endraw %}
<img referrerPolicy="no-referrer" src="" alt="">
```

# title 标题

# excerpt 摘录

# categories 分类

# tags 标

