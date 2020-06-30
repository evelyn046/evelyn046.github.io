---
title: Github Pages+Jekyll搭建个人博客
author: Evelyn
date: 2020-06-30 10:32:00 +0800
categories: [技术]
tags: [Github, Jekyll]
math: true
---
最近课程都结束了，终于可以静下心做一些拖延了好久的事情，也要好好为实习做些准备。第一步，搭建个个人博客，作为学习记录。

备选方案有三：

- 简书/知乎
- 域名 + 服务器 + wordpress
- GitHub + Jekyll

在简书上注册个账号可能是最简单的方法了，简单得过于无聊，不花心思和时间建立的博客总让人难以坚持维护，想想我这种三分钟热度的性格，还是算了吧。况且自己从零搭建的博客发布内容会更加自由，不用受第三方管束，还能定义成自己喜欢的样子。所以，方案一pass。

域名 + 服务器 + wordpress似乎是比较专业的方案，大三小学期项目中也基于新浪云做了个项目的小前端，难度不大。然而，为什么要用这个方案呢？还不是为了有个炫酷的域名，可注册域名太麻烦了，还要实名认证、备案，时间开销太大；购买国外的域名又会面临网络不稳定的问题。想想这个方案也pass吧。

GitHub pages + Jekyll是上学期高老师上课时提到的一种建站方法。

Github Pages 是面向用户、组织和项目开放的公共静态页面搭建托管服务，站点可以被免费托管在 Github 上，你可以选择使用 Github Pages 默认提供的域名 github.io 或者自定义域名来发布站点。

使用GitHub pages 建站有以下优点：
- 完全免费，服务器、流量、域名都有，零费用搭建技术博客
- 写博客和提交代码的方式一致
- 支持绑定自己的域名（万一哪天我心血来潮注册了一个域名呢~）
- 提供流行的网页主题模板

缺点：
- 不支持动态内容，必须是静态网页
- 博客内容不能被百度索引
- 仓库空间不能大于1G（足够了）
- 每个月流量不能超过100G（足够了 x2）
- 每个小时更新不超过10次

GitHub建站可基于jekyll或者hexo或者其它的，官方提供的Jekyll主题更多，样式也更好看，而且能直接链接到源码主页，所以选择了Jekyll

> Jekyll 是一个简单的博客形态的静态站点生产机器。它有一个模版目录，其中包含原始文本格式的文档，通过一个转换器（如 Markdown）和我们的 Liquid 渲染器转化成一个完整的可发布的静态网站，你可以发布在任何你喜爱的服务器上。

简单来说，Jekyll能够将纯文本转化为静态博客网站，不需要数据库支持，也没有评论功能，想要评论功能的话可以借助第三方的评论服务。

## 第一步 安装Jekyll

1. 下载安装[Ruby installer](
https://rubyinstaller.org/)
2. 下载[RubyGems](
https://rubygems.org/pages/download) 并解压
3. 在命令行执行  `gem install jekyll`

## 第二步 搭建博客
### 选模板
[Jekyll官网](
http://jekyllthemes.org/)提供了大量精美的博客模板，可以选择一个喜欢的fork下来，然后在基础上修改，也可以自己从零搭建属于自己的模板。
1. 从官网选择合适的主题
2. 点击Homepage进入发布者的GitHub。
   
    ![Desktop View]({{ "/assets/img/6.29/2.png" |  }})

> Jekyll的目录结构主要包含以下内容:
>- _posts 博客内容
>- _pages 其他需要生成的网页，如Post页
>- _layouts 网页排版模板
>- _includes 被模板包含的HTML片段
>- _data 动态数据
>- _sites 最终生成的静态网页
>- _config.yml 网站的一些配置信息(首先修改)
>- index.html 网站的入口
>
>jekyll是将分散在各个目录下的html文件拼接起来运行。

### 网站托管
1. 将模板fork到自己的GitHub上。
      ![Desktop View]({{ "/assets/img/6.29/3.png" |  }})
2. 回到自己的GitHub，进入刚刚fork的项目，点击settings，将仓库名字修改为username.github.io
   
   ![Desktop View]({{ "/assets/img/6.29/1.png" |  }})

3. 这个时候在浏览器中访问 https://evelyn046.github.io 就可以访问了。

## 第三步 写博客
写博客前需要先把GitHub上的项目clone到本地，然后进到博客目录在命令行执行jekyll serve开启本地预览，这样就可以边写边看效果，一般本地没有报错等问题，写好后上传到github后也是没问题的，如果出现构建Github Pages错误的问题，GitHub 会向你的账户发送邮件。

_posts目录就是专门存放博客文件的，可以使用markdown、或者html格式的文件来写，不管使用哪种可是，文件的**YAML头信息**绝不能少。

```
---
layout: post
title:  "This is a title"
date:   2020-06-29 11:36:26 +0800
tags:
     
---
```

写好文章后，上传GitHub后需要等一两分钟刷新，Github Pages就会更新博客了。
