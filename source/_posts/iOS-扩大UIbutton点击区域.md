---
title: iOS-扩大UIbutton点击区域
categories:
  - iOS
date: 2019-09-25 16:37:23
tags:
---


## 一、扩大点击区域的两种方式
> 实现原理：重写系统```- (BOOL)pointInside:(CGPoint)point withEvent:(UIEvent *)event```方法，实现对可响应区域的改变

### 1、添加`UIButton`分类
- 优点
	- 使用方便，导入头文件，设置点击区域即可
- 缺点
	- 如果多个分类重写了`UIButton`的系统方法，那么最终只会执行某一个分类的系统方法，导致其它分类功能出问题
	- 分类重写父类方法之后，每个`UIButton`对象都会调用分类的方法，修改容易出问题
	
### 2、子类继承`UIButton`父类

- 优点
	- 不侵入系统的`UIButton`类，功能清晰
- 缺点
	- 使用的时候需要修改`UIButton`为子类`TFQEnlargeButton`，比分类多了一步操作
	
### 3、选择
首先分类是用来给原来的类增加方法的，并不是让大家用来重写父类方法的，且添加分类的方式有致命的缺点，所以这里强烈推荐继承的方式来实现扩大点击区域的功能

[GitHub Demo](https://github.com/LiZhiDaDa/TFQEnlargeButton)