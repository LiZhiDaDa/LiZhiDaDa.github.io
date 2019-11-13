---
title: iOS-修改UIButton图片位置
categories:
  - iOS
date: 2019-11-12 17:09:06
tags:
---

## 一、背景
相信大家都碰到过这样的需求，```button```中的图片需要摆放在各种位置，每次都需要通过```imageEdgeInsets```、```titleEdgeInsets```一点一点的调整```button```中```label```、```image```的位置，所以我干脆写了个```UIButton```分类，这样以后使用起来就及其方便了，具体使用方法见[Demo-TFQPositionButton](https://github.com/LiZhiDaDa/TFQPositionButton)，效果图如下：
<img src=iOS-修改UIButton图片位置/QQ20191112-182641@2x.png width=200>

## 二、开发过程中注意点
### 1、```imageEdgeInsets```
在分类的开发过程中，需要用到以下代码设置子控件的偏移量
```
self.imageEdgeInsets = UIEdgeInsetsMake(0, 0, 0, 0);
```

方法中四个参数分别代表上、左、下、右四个方向的偏移距离，比如第一个参数```top```，如果设置```10```，代表图片向下移动```10```，设置```-10```，代表向上移动```10```，但是如果我设置了

```
self.imageEdgeInsets = UIEdgeInsetsMake(10, 0, 0, 0);
```

这时候图片应该向下移动```10```的距离，经过实际调试得知，图片只向下移动了```5```，由于```UIEdgeInsetsMake```方法有上、左、下、右四个参数，但是图片肯定又不可能同时向四个方向移动，所以我怀疑图片在纵向移动的距离应该是上、下两个参数相减然后取平局值，即```(top-bottom)/2.0```，所以我有理由怀疑，让图片向下移动```10```的距离有如下两种写法

- ```self.imageEdgeInsets = UIEdgeInsetsMake(10, 0, 0, -10);```
- ```self.imageEdgeInsets = UIEdgeInsetsMake(10*2, 0, 0, 0);```

经过调试，发现两种方法得到的效果是一样的，所以我就开开心心的用上、左```*2```并完全抛弃下、右两个参数的方式(```UIEdgeInsetsMake(top*2, left*2, 0, 0)```)去开发我的分类，而且这样超级方便有木有，我一度觉得开发这个方法的人秀逗了，当我设置图片向右移动的时候问题出现了，我设置的方式是```UIEdgeInsetsMake(0, left*2, 0, 0)```，我发现图片并没有向右移动```left```的距离，而是移动了一个不知道咋得来的值，所以我改变了策略，使用了方法```UIEdgeInsetsMake(0, left, 0, -left)```，这次图片规规矩矩的向右移动了```left```的距离，不知道此方法内部是怎么实现的，但是大家还是要用```UIEdgeInsetsMake(0, left, 0, -left)```的方式来设置偏移量

### 2、计算```UILabel```的```size```






