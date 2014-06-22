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

标签和超链接测试
-------
你好，[这里](http://www.dagouge.com)将成为超链接，`这里`成为标签。

