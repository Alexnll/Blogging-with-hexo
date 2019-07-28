---
title: 基于hexo框架的博客网站构建
date: 2019-07-27 10:28:25
tags: 
  - hexo
  - blog
  - git
  - node.js
---

### 摘要
本文简略地介绍了如何基于hexo框架搭建一个简单的博客网站，并将其部署到远端。

<!-- more -->
### 前置安装
###### 1. 安装node.js
检查是否安装成功：
```
node -v
npm -v
```
###### 2. 安装git
###### 3. 在国内时，可将npm源转化为cnpm源：
```
npm install -g cnpm --registry-http://registry.npm.taobao.org
```
转为taobao源，-g表示全局安装。可通过
```
cnpm
```
检查是否安装成功。

###### 4. 安装hexo框架： 
```
cnpm install -g hexo-cli
```

### 实际搭建
###### 1. 新建hexo项目于相应项目文件夹中：
```
hexo init
```

###### 2. 在本地启动/预览博客网站
```
hexo s
```
后便可通过http://localhost:4000 进行本地预览。

###### 3. 新建一篇文章：
```
hexo new "post name"
```

###### 4. 清理数据库：
```
hexo clean
```

###### 5. 生成新网页：
```
hexo g
```

###### 6. 更换网页主题/自定义主题
- 下载主题 git clone 主题网址.git themes/文件夹名
- 修改_config.yml
- 更改Extensions中的*themes*以更换主题


### 远端部署
#### github部署
###### 1. 新建仓库
仓库名必须为：用户名.github.io
用户部署个人博客的github仓库需符合要求

###### 2. 安装git部属用插件deployer： 
- Linux/git bash上：

```
cnpm install --save hexo-deployer-git
```

- 通过windows中cmd：

```
cnpm install -hexo-deployer-git --save
```
  
###### 3. 设置_config.yml
更改Deployment：
```
deploy:
  type: git
  repo: 仓库地址.git
  branch：master
```
###### 4. 部署到远端：
```
hexo d
```

完成后即可通过repo主页进行博客网站的浏览，而不需要使用本地ip的端口。

### 文章标签设置
##### 1. 使hexo首页显示摘要显示
由于Hexo博客首页默认显示整篇博文，故可通过在文章内容中插入一行标签：
```
<!-- more -->
```

该标签之上的文本为摘要，即需要点击阅读全文才能查看剩余的内容。另外也可以在_config.yml中设置每页显示的文章数。

##### 2. hexo文章中的引用
一般Hexo网页编辑可使用markdown的语法，但也有特殊的文本块与标签的使用方法，具体可参考附录3。

##### 3. hexo目录结构
见附录5.


---

#### 附录
1. https://www.bilibili.com/video/av44544186/index_1.html  Hexo博客搭建视频教程
2. https://www.jianshu.com/p/495ed3ef6d01  Hexo博客首页显示摘要
3. https://www.jianshu.com/p/56e879ddcf6c  Hexo文章中的标签引用
4. https://blog.csdn.net/qq_32337109/article/details/78755662  Hexo创建文章、标签、分类
5. https://blog.csdn.net/abc_12366/article/details/87864623 Hexo目录结构
6. https://www.jianshu.com/p/baab04284923  Hexo源文件备份