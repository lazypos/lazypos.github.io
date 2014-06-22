---
layout: post
title: 第二篇测试文章
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
