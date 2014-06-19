---
layout: post
title: CCTMXTiledMap的应用
---

`CCTMXTiledMap`可以导入由Tiled创建的地图文件格式。
tmx地图的内部坐标是从左上角开始的， tiled可以有多层，使用`layerNamed()`函数获取某个层的`CCTMXLayer`指针

比如下图有一个hill层：
`CCTMXTiledMap* pMap = CCTMXTiledMap::create("test.tmx”);`
`CCTMXLayer* hillLayer = pMap->layerNamed("hill”);`

然后在Tiled编辑器里可以看到每块图都有一个序号，比如下图是（1，22），其实这里面每一块图都是一个`CCSprite`，我们可以用 `CCSprite* sp = hillLayer->tileAt(1, 22)`; 来获取到这块地图对应的精灵。 
*这里要注意这个精灵的锚点默认是左下角的，如果调用 `sp->getPosition()`; 得到的点是该图块左下角的点，而一般的CCSprite创建后是锚点是在图片中央。

可以调用`CCTMXTiledMap的getMapSize()`获取整个地图的大小，`getTiledSize()`来获得每一个小块的尺寸。

我们经常看到网上两个坐标转换的函数：

{% highlight cpp %}

CCPoint GameMap::tileCoordForPosition(CCPoint position)
{
    int x = position.x / this->getTileSize().width;
    int y = (((this->getMapSize().height) * this->getTileSize().height) - position.y) / this->getTileSize().height;
    return ccp(x, y);
}

{% endhighlight %}

这个是cocos2dx转tiled的坐标（上面说的tileAt（1，22）的参数1，22），原理如下：
假设每块小地图的长度宽度都是32，如果参数是（120，200）那么，相当于小地图的X轴的 4 块， Y轴的 6 块。因为tiled地图从第0块算起的，所以X轴是3。 而Y轴是从上往下的，所以要(总块数-6)，才是Y轴的坐标。

![map]({{site.url}}/images/tiledmap.png)


