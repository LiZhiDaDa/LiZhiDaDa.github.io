---
title: Mac上GitHub+Hexo搭建个人博客网站
date: 2019-09-19 16:22:14
categories:
- iOS
tags:
- hexo
---

## 一、写此文章的原因
### 1.1、以后自己换了电脑能快速的集成环境，不用再去查别人的文章
### 1.2、记录一下自己在搭建过程中遇到的问题，利己利人

## 二、安装`git`、`Node.js`环境
`Hexo`需要`Node.js`、`git`这两个环境，所以需要先把这两个环境装好，所以首先检查一下本地是否已经安装了这两个环境

### 2.1、安装git
在终端中输入`git --version`来查看你的电脑上是否有`git`环境，如果出现了如下提示，则证明本地有`git`环境，跳过第1步，直接安装`Node.js`

```
wanglizhi@wlz:~$     git --version
git version 2.20.1 (Apple Git-117)
```

安装`git`有两种方法

- 官网下载安装包[git官网](https://git-scm.com/download)
- 用[homebrew](https://brew.sh/index_zh-cn.html)安装(`homebre`的安装教程官网上写的一清二楚)，命令为`brew install git`

### 2.2、安装`Node.js`环境
[Node.js简介](https://www.runoob.com/nodejs/nodejs-tutorial.html)、[NPM简介](https://www.runoob.com/nodejs/nodejs-npm.html)

去[Node.js官网](https://nodejs.org/en)下载安装包，左侧是安装人数最多的版本，右侧是最新版本，你随意选择

<img src=Mac上GitHub-Hexo搭建个人博客网站/QQ20190919-171312.png width=400>

下载并安装完成之后，输入如下命令即可检查安装结果

```
wanglizhi@wlz:~$     node --version
v10.16.3
wanglizhi@wlz:~$     npm --version
6.9.0
```

## 三、安装`Hexo`

```
sudo npm install -g hexo-cli --unsafe-perm
```

- `sudo`是用管理员权限执行命令
- `--unsafe-perm`是`npm`处于安全考虑不支持`root`用户运行，加上此命令就可以运行

## 四、初始化博客环境
### 4.1、创建文件夹
找一个位置创建文件夹，在此文件夹目录下初始化本地博客，例如我这里的文件夹是`TechnologyBlogs`

<img src=Mac上GitHub-Hexo搭建个人博客网站/QQ20190919-174259.png width=400>

### 4.2、依次执行以下命令，下载相关文件

```
wanglizhi@wlz:~/Documents/iOS/TechnologyBlogs$     hexo init
wanglizhi@wlz:~/Documents/iOS/TechnologyBlogs$     hexo install
```

### 4.3、启动本地服务器
[hexo常见命令](https://blog.csdn.net/dxxzst/article/details/76135935)

```
hexo server
```


然后根据提示在浏览器中打开网址`http://localhost:4000`可以访问默认页面如下图，至此代表配置本地环境成功

<img src=Mac上GitHub-Hexo搭建个人博客网站/5acca579bd9d8.png width=600>

## 四、配置`GitHub`
### 4.1、新建仓库，名字千万按照下边的规则取
我`GitHub`的用户名是`LiZhiDaDa`，那么我这个新仓库的名字一定要取为`LiZhiDaDa.github.io`
<img src=Mac上GitHub-Hexo搭建个人博客网站/QQ20190920-104912@2x.png width=500>

### 4.2、配置新建的仓库
点击新建仓库的`Settings`选项，下拉到`GitHub Pages`进行如下操作

<img src=Mac上GitHub-Hexo搭建个人博客网站/QQ20190920-110124@2x.png width=500>
<img src=Mac上GitHub-Hexo搭建个人博客网站/QQ20190920-110145@2x.png width=500>
<img src=Mac上GitHub-Hexo搭建个人博客网站/QQ20190920-110223@2x.png width=500>

然后继续点击仓库的`Settings`选项，下拉到`GitHub Pages`，可以看到如图所示的网址就是以后你博客的链接，至此`GitHub`配置完成

<img src=Mac上GitHub-Hexo搭建个人博客网站/QQ20190920-110507@2x.png width=500>

如果你的链接如下图所示，那么就是你的仓库名字配置错了，此处配置错误会导致你以后博客上的项目路径错误进而找不到`js`、`css`文件，所以一定要按照上边的规则修改仓库名称

<img src=Mac上GitHub-Hexo搭建个人博客网站/QQ20190920-110639@2x.png width=500>
<img src=Mac上GitHub-Hexo搭建个人博客网站/QQ20190920-110759@2x.png width=500>

## 五、项目发布到`GitHub`
### 5.1、修改配置文件`_config.yml`
修改仓库链接，把本地文件跟`GitHub`做关联，注意冒号之后有空格

```
deploy:
  type: git
  repo: https://github.com/LiZhiDaDa/wanglizhi-iOS.git
  branch: master
```
### 5.2、安装`git`部署器

在终端中你的博客目录（我的目录是`~/Documents/iOS/TechnologyBlogs$`）执行命令

```
npm install hexo-deployer-git –save
```

### 5.3、项目发布到`GitHub`
在终端中你的博客目录（我的目录是`~/Documents/iOS/TechnologyBlogs$`）下依次执行以下三个命令

```
hexo clean
hexo generate
hexo deploy
```
然后访问[https://lizhidada.github.io](https://lizhidada.github.io)链接看到和刚才访问[http://localhost:4000](http://localhost:4000)一样的页面，就代表你配置成功了

## 六、发布博客
### 6.1、新建博客
通过以下命令新建名字为`title`的博客

```
hexo new 'title'
```

### 6.2、编辑博客
通过`Markdown`语法编辑文章，这里推荐`MacDown`编辑器

### 6.3、发布博客
先通过如下命令把博客部署到本地，然后在[http://localhost:4000](http://localhost:4000)查看样式是否满意

```
hexo s
```

本地满意之后，通过如下命令把文章部署到服务器，然后别人就可以通过上述链接看到你的博客了，我的博客[https://lizhidada.github.io](https://lizhidada.github.io)

```
hexo clean
hexo g
hexo d
```

## 七、更换`Hexo`主题
### 7.1、挑选喜欢的主题
浏览[主题](https://hexo.io/themes/)，然后挑一个自己喜欢的，点击主题的名字，跳转到`GitHub`下载主题
### 7.2、配置主题
#### 7.2.1、把下载好的文件解压放到`themes`目录下
<img src=Mac上GitHub-Hexo搭建个人博客网站/QQ20190920-114141.png width=500>

#### 7.2.2、配置文件
在`_config.yml`文件中进行如下配置，注意这里`theme：`后边的名字一定要跟你下载的主题的文件夹名字一致，到这里主题就配置完成了
<img src=Mac上GitHub-Hexo搭建个人博客网站/QQ20190920-114355.png width=500>

## 八、插入本地图片
自己配置博客的方式，上传图片又是一个问题，现在只介绍我用的这种自认为比较方便的方法

### 8.1、修改配置文件
`_config.yml`里的`post_asset_folder:`这个选项设置为`true`
### 8.2、下载插件
在你的博客目录下终端执行命令安装一个可以上传本地图片的插件
```
npm install hexo-asset-image --save
```
### 8.3、使用
以上配置完成后再次执行`hexo new`命令的时候会生成一个同名的文件夹用来存放图片
<img src=Mac上GitHub-Hexo搭建个人博客网站/QQ20190920-115428.png width=500>

把要用的图片放到这个位置，然后博客中要用的话就使用如下格式
```
<img src=Mac上GitHub-Hexo搭建个人博客网站/QQ20190920-115428.png width=500>
```
这样插入图片功能就配置完成了

## 九、使用`alias`给组合命令添加别名
百度百科[alias](https://baike.baidu.com/item/Alias/3105303)
### 9.1、打开`.bash_profile`文件
```
vim ~/.bash_profile
```
### 9.2、添加别名
在`.bash_profile`文件末尾添加两行代码

```
alias hs='hexo clean && hexo g && hexo s'
alias hd='hexo clean && hexo g && hexo d'
```

保存文件，然后重新加载该配置文件

```
source .bash_profile
```
### 9.3、查看命令是否成功
运行`alias`命令，出现以下结果就代表配置成功，以后就可以用快捷命令`hs`、`hd`来部署项目了

```
wanglizhi@wlz:~$     alias
alias hd='hexo clean && hexo g && hexo d'
alias hs='hexo clean && hexo g && hexo s'
```

## 十、数据备份
如果你需要更换电脑写博客，那么你的备份尤为重要，如果不备份，那么你写过的文章就gg了，尴尬不，备份的方式有很多种，这里我只介绍在`GitHub`当前仓库下创建分支的方法进行备份

> 方案介绍：虽然新建了分支，但是这个分支跟主干没有一毛钱关系，其实这里创建分支与新建一个仓库没有什么区别，用分支主要是为了让自己的`GitHub`仓库看起来更清晰，就是个人问题，你想创建仓库你就创建

- master hexo部署之后的文件放在这里，供大家访问
- hexo 备份本地文件 

### 10.1、在仓库下新建分支
在仓库下新建名为`hexo`的分支，名字可以随便取

<img src=Mac上GitHub-Hexo搭建个人博客网站/QQ20190920-172831@2x.png width=400>

### 10.2、把默认分支设置为新建的分支
进入设置页面，设置刚刚创建的`hexo`分支为默认分支
<img src=Mac上GitHub-Hexo搭建个人博客网站/QQ20190920-172911@2x.png width=400>

### 10.3、把本地`Hexo`目录下的文件与创建的分支做关联
#### 10.3.1、提取`.Git`文件夹
随便新建个空文件夹，把远程仓库克隆下来，复制`.git`文件到你的博客目录下（我的目录为`~/Documents/iOS/TechnologyBlogs`），这些操作我用的`SourceTree`图形化工具，所以大家就各显神通吧
#### 10.3.2、把文件提交到`GitHub`
去你的博客目录下执行命令，提交文件到远端，因为这个项目只有我一个人在用，所以我就直接用`-f`强推了

```
git add .
git commit -m 'update blog'
git push -f
```

因为你把当前仓库的默认分支设置为了`hexo`，所以`hexo`分支下，至此备份工作完成

### 10.4、修改`alias`命令
参考第九步将``文件的`alias`命令进行修改
将如下命令

```
alias hd='hexo clean && hexo g && hexo d'
```
修改为

```
alias hd='hexo clean && hexo g && hexo d && git add . && git commit -m "update blog" && git push -f'
```
这样你每次用`hd`命令把你的博客部署到`GitHub`的同时也进行了备份，皆大欢喜

> 以后自己买了新电脑之后只需要按照此文章安装`hexo`环境，然后把备份文件`clone`下来，挑选你需要的文件替换本地文件，自己就又能继续愉快的写博客了














