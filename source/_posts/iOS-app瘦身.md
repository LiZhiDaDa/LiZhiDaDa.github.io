---
title: iOS-app瘦身
categories:
  - iOS
date: 2019-10-18 14:17:45
tags:
---


## 一、准备工作
### 1、目前`app`的情况
- 项目包大小475.6M
- ipa 57.2M
- 蒲公英 54.4M

### 2、`ipa`包内容解析
给app打包，得到ipa文件，然后把后缀名改为zip，解压后如图

- 有1430个项目，共87.3MB
- 图片数量占到了99%以上
- 占内存最大的是app的可执行文件，占了50.6MB

<img src=iOS-app瘦身/QQ20191018-145132.png width=500>
<img src=iOS-app瘦身/QQ20191018-145611.png width=500>
接下来我们就可以针对这些文件进行优化了

## 二、废弃资源、代码清理
### 1、`AppCode`排查废弃类、方法、属性
下载```AppCode```(```AppCode```是一个可以用来开发iOS程序的民间付费IDE)，```Code``` -> ```Inspect Code``` -> ```Unused Code```，这时候就会显示出哪些类、方法、属性、引用、参数没有被使用过，就可以进行优化，记得二次确认。

在这一步删除了没有使用到的类几十个，方法几十个，无效引用几百个

### 2、`LSUnusedResources`排查废弃的图片资源
[LSUnusedResources](https://github.com/tinymind/LSUnusedResources)，下载之后按照教程操作即可，点击`Full Path(Double Click to Open)`这一列，会按照文件排序，方便删除
如下图所示，没有用到的图片288张，总共4248.14kb，现在可以挨个进行删除了，需要再次确认下是不是真的没有用到，比如有些图片资源在代码中是这样写的，那么这些图片就不能删除了，一定要小心

```
NSString *imageName = [NSString stringWithFormat:@"newfeature_%d", i+ 1];
```
<img src=iOS-app瘦身/QQ20191018-170720.png width=500>

> 这一波操作结束之后，删除图片540多张，`ipa`包的大小由原来的57.2M减小为51.2M

<img src=iOS-app瘦身/QQ20191019-150035@2x.png width=500>
<img src=iOS-app瘦身/QQ20191019-150103@2x.png width=500>

> 可执行文件的也小了好多

<img src=iOS-app瘦身/QQ20191019-150733.png width=500>

## 四、高德等sdk减肥











