---
title: Hexo博客迁移
date: 2019-07-12 01:31:31
tags:
---
![](https://upload-images.jianshu.io/upload_images/16749538-7294cc05e7e63552.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/640)

完成Hexo本地运行后，会在本地文件里生成一个public文件夹。public文件夹内是根据.md生成的html文件，也就博客的静态文件。
通常情况下，我们执行：

```
$ hexo d

```

就是把public文件夹下的文件同步到github，然后就能通过[https://username.github.io/](https://link.zhihu.com/?target=https%3A//kokofe.github.io/)访问博客了。所以，我们的思路其实就是把静态文件和Hexo环境，分别存在username.github.io的master和hexo分支上。

由于`hexo d`上传部署到github的其实是hexo编译后的文件，是用来生成网页的，不包含源文件。

<noscript>![image](https://upload-images.jianshu.io/upload_images/16749538-3db0b0b29c2c6b3d.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

</noscript>

![image](https://upload-images.jianshu.io/upload_images/16749538-60288d79b0d96c64.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

也就是上传的是在本地目录里自动生成的`.deploy_git`里面。

其他文件 ，包括我们写在source 里面的，和配置文件，主题文件，都没有上传到github

<noscript>![image](https://upload-images.jianshu.io/upload_images/16749538-4a0087d239f36885.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

</noscript>

![image](https://upload-images.jianshu.io/upload_images/16749538-e3507816d26e8c53.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

所以可以利用git的分支管理，将源文件上传到github的另一个分支即可。

## **上传分支**

首先，先在github上新建一个hexo分支，如图：

<noscript>![image](https://upload-images.jianshu.io/upload_images/16749538-a63aac240be2e556.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

</noscript>

![image](https://upload-images.jianshu.io/upload_images/16749538-617e556fccc78a7f.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

然后在这个仓库的settings中，选择默认分支为hexo分支（这样每次同步的时候就不用指定分支，比较方便）。

<noscript>![image](https://upload-images.jianshu.io/upload_images/16749538-b5442cbdf75b1be7.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

</noscript>

![image](https://upload-images.jianshu.io/upload_images/16749538-1ec95ba9e74d328f.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

然后在本地的任意目录下，打开git bash，

```
git clone git@github.com:ZJUFangzh/ZJUFangzh.github.io.git
```

将其克隆到本地，因为默认分支已经设成了hexo，所以clone时只clone了hexo。

接下来在克隆到本地的`ZJUFangzh.github.io`中，把除了.git 文件夹外的所有文件都删掉

把之前我们写的博客源文件全部复制过来，除了`.deploy_git`。这里应该说一句，复制过来的源文件应该有一个`.gitignore`，用来忽略一些不需要的文件，如果没有的话，自己新建一个，在里面写上如下，表示这些类型文件不需要git：

```
.DS_Store
Thumbs.db
db.json
*.log
node_modules/
public/
.deploy*/

```

注意，如果你之前克隆过theme中的主题文件，那么应该把主题文件中的`.git`文件夹删掉，因为git不能嵌套上传，最好是显示隐藏文件，检查一下有没有，否则上传的时候会出错，导致你的主题文件无法上传，这样你的配置在别的电脑上就用不了了。

而后

```
git add .
git commit –m "add branch"
git push 
```

这样就上传完了，可以去你的github上看一看hexo分支有没有上传上去，其中`node_modules`、`public`、`db.json`已经被忽略掉了，没有关系，不需要上传的，因为在别的电脑上需要重新输入命令安装 。

<noscript>![image](https://upload-images.jianshu.io/upload_images/16749538-7270ab00f110f2a3.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

</noscript>

![image](https://upload-images.jianshu.io/upload_images/16749538-150428f8c9754cb3.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

这样就上传完了。

## **更换电脑操作**

一样的，跟之前的环境搭建一样，

*   安装git

```
sudo apt-get install git

```

*   设置git全局邮箱和用户名

```
git config --global user.name "yourgithubname"
git config --global user.email "yourgithubemail"

```

*   设置ssh key

```
ssh-keygen -t rsa -C "youremail"
#生成后填到github和coding上（有coding平台的话）
#验证是否成功
ssh -T git@github.com
ssh -T git@git.coding.net #(有coding平台的话)

```

*   安装nodejs

```
sudo apt-get install nodejs
sudo apt-get install npm

```

*   安装hexo

```
sudo npm install hexo-cli -g

```

但是已经不需要初始化了，

直接在任意文件夹下，

```
git clone git@………………

```

然后进入克隆到的文件夹：

```
cd xxx.github.io
npm install
npm install hexo-deployer-git --save

```

生成，部署：

```
hexo g
hexo d

```

然后就可以开始写你的新博客了

```
hexo new newpage

```

**Tips:**

1.  不要忘了，每次写完最好都把源文件上传一下

```
git add .
git commit –m "xxxx"
git push 

```

1.  如果是在已经编辑过的电脑上，已经有clone文件夹了，那么，每次只要和远端同步一下就行了

```
git pull
```
