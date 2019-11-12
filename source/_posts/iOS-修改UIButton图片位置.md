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
```
typedef struct __attribute__((objc_boxable)) UIEdgeInsets {
    CGFloat top, left, bottom, right;  // specify amount to inset (positive) for each of the edges. values can be negative to 'outset'
} UIEdgeInsets;
```
