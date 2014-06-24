---
layout: post
title: 功能测试文章
---


代码测试
-------

{% highlight cpp %}

CCPoint tileCoordForPosition(CCPoint position)
{ 
	int x = position.x / this->getTileSize().width; 
	int y = (((this->getMapSize().height) * this->getTileSize().height) - position.y) / this->getTileSize().height; 
	return ccp(x, y); 
}

{% endhighlight %}


图片测试
-------
![map]({{site:url}}/images/tiledmap.png)

其他文本测试
-------
你好，[这里](http://www.dagouge.com)将成为超链接，`这里`成为标签。字体**加粗**，字体*倾斜*，~~字体被删除~~，注释[^1]</br>
[^1]:这里是注释内容

`</br>`是换行[^2]  

代码段

```
Fenced code blocks are like Stardard Markdown’s regular code
blocks, except that they’re not indented and instead rely on
a start and end fence lines to delimit the code block.
```

# 标题
## 标题
### 标题
#### 标题
##### 标题


名字 | 年龄 | 身高
------|------|-----
lazypos|35|172
doslin|23|175



