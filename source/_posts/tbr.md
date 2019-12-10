---
title: 基于Tile的渲染
date: 2019-11-28 12:00:00
tags: GPU
---

TBR，Tile Based Rendering，基于Tile的渲染。

TBR是一种渲染模式，除此之外，还有立即渲染模式和基于Tile的延迟渲染模式。

传统的渲染模式是这样的：
```js
foreach(primitive)
    foreach(fragment in primitive)
        render(fragment)
```

TBR的处理逻辑是这样的：

```js
foreach(tile)
    foreach(primitive in tile)
        foreach(fragment in primitive in tile)
            render(fragment)
```

可以看到，TBR要求先将一帧画面中的所有顶点染色完成然后生成多边形列表之后，才能进行光栅化和片段染色，否则遍历Tile里面的图元时会发生遍历不完全的情况。

TBR使得深度模板和颜色缓冲区放在片上成为可能。因为一个Tile通常不大，如32x32，所以Tile对应的深度模板和颜色所占的存储也不大，可以使用片上存储来存放深度模板值和颜色值。

将深度模板和颜色放在片上之后，访问速度相比之前要快得多，因为之前需要去访问显存。
