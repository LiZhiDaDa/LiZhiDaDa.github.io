---
title: iOS-认识Mach-O
categories:
  - iOS
date: 2019-11-22 11:35:14
tags:
---

## 一、名词解释
> - Mach-O：Mach Object文件格式的缩写，它是一种用于可执行文件，目标代码，动态库，内核转储的文件格式，曾经为大部分基于Mach核心的操作系统所使用
> - Mach：一个由卡内基梅隆大学开发的用于支持操作系统研究的操作系统内核

## 二、```Mach-O```文件格式
```Mach-O```文件是一类文件的简称，从源文件中可以得到结果
```#import <mach-o/loader.h>```

```
#define	MH_OBJECT	0x1		/* relocatable object file */
#define	MH_EXECUTE	0x2		/* demand paged executable file */
#define	MH_FVMLIB	0x3		/* fixed VM shared library file */
#define	MH_CORE		0x4		/* core file */
#define	MH_PRELOAD	0x5		/* preloaded executable file */
#define	MH_DYLIB	0x6		/* dynamically bound shared library */
#define	MH_DYLINKER	0x7		/* dynamic link editor */
#define	MH_BUNDLE	0x8		/* dynamically bound bundle file */
#define	MH_DYLIB_STUB	0x9		/* shared library stub for static */
					/*  linking only, no section contents */
#define	MH_DSYM		0xa		/* companion file with only debug */
					/*  sections */
#define	MH_KEXT_BUNDLE	0xb		/* x86_64 kexts */
```
<img src="./iOS-认识Mach-O/Mach-O.png">
下边就用我们项目的可执行文件介绍一下```Mach-O```文件的结构，如下图所示，把```ipa```文件的后缀名改为```zip```，解压后得到```teyuntong.app```，然后显示包内容得到可执行文件，复制到下载文件夹中
<img src="./iOS-认识Mach-O/WX20191122-161029.png">
<img src="./iOS-认识Mach-O/WX20191122-161316.png">






## 三、```CPU```架构
由于苹果手机更新换代比较快，所以你的代码必须要支持市面上大部分苹果手机的架构，而苹果手机使用的处理器是arm架构，下图明确表达了苹果的机型都用的什么处理器，所以可以这么说，你的代码以及导入的所有三方库只要支持```arm64```一种架构即可
> iPhone6s中的s是speed，速度的意思

<img src="./iOS-认识Mach-O/iPhone CPU架构.png">


