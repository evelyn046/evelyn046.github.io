---
title: Markdown快速插入截图
author: Evelyn
date: 2020-07-02 10:22:00 +0800
categories: [技术]
tags: [Markdown]
math: true
---

写博客用的是VScode + Markdown，但用markdown插入图片是件非常麻烦的事情。通常有两种方法：
- 把图片上传到图床，然后把链接写到`![]()`里
- 把图片保存到本地，使用相对路径添加

无论哪种方法，都必须经过“保存图片” -> “插入”这一步，那么有没有类似微信截图，可以直接复制插入剪切板上的图片的方法呢？

## 第一次尝试

### 使用VScode中的**Paste Image**插件

在 *Extension* 中搜索 **Paste Image** 下载安装即可

![]({{ "/assets/img/2020-07-02-09-37-12.png" |  }})

截图后按下`ctrl + alt + v`即可快速插入图片。

![]({{ "/assets/img/2020-07-02-09-37-58.png" |  }})

图片默认保存在当前文档所在的目录，可以对目录进行修改。

在 *File* -> *Preferences* -> *Settings*中搜索“Paste Image”即可修改保存路径

![]({{ "/assets/img/1.png" |  }})


> 我将路径修改为了当前目录下的assets文件夹中的img文件夹，如果输入的文件夹不存在，则会自动创建同名文件夹。

此外，还可以修改保存的文件名，默认为**年-月-日-时-分-秒**


然后快乐的push到GitHub

然后....

**翻车了**

---
## 第二次尝试

push到远端后，所有的图片都无法查看，于是开始了漫长的排错之路...

网上关于Paste Image的教程通常到了ctrl+alt+v插入图片后就结束了，但这种方法只能在本地插入图片，push到远端就无效了。

推荐的博客快速插图方法最终还是图云。

但是，我本着从哪里跌倒就从哪里爬起来（不想花钱懒得注册账号不想下软件）的原则，开始琢磨有什么方法能在Paste Image的基础上插图呢？

首先，对比正常的插图代码和Paste Image导入的有何区别。

  ```
  <!-- Paste Image导入的格式 -->
  ![](..\assets\img\2020-07-01-17-35-50.png)

  <!-- Jekyll支持的插入格式 -->
![]({{ "/assets/img/2020-07-01-17-35-50.png" |  }})

  ```
- 语法不一致。
  Jekyll中的语法为`![Alt text]({{ "图片链接" | absolute_url }})`, 而Paste Image插入的是Markdown默认插图语法 `![Alt text](图片链接 "optional title")`
- 路径不一致。
  Jekyll使用的是绝对路径，而md是相对路径。
- 斜杠与反斜杠

确定好问题后，有针对性地一一突破就好了
1. 关于语法不一致
   
   在PI的settings里修改Paste Image: Insert Pattern
    >The pattern of string that would be pasted to text.

   ![]({{ "/assets/img/2020-07-02-10-12-51.png" |  }})

2. 关于路径不一致
   
   在settings中修改Base Path和Path

   ![]({{ "/assets/img/2020-07-02-10-15-31.png" |  }})

   ![]({{ "/assets/img/2020-07-02-10-15-52.png" |  }})

3. 关于斜杠与反斜杠
   
   在settings中勾选Force Unix Style Separator

   ![]({{ "/assets/img/2020-07-02-10-17-46.png" |  }})

   > Force Unix Style Separator默认是勾选状态，可能是我之前修改settings时不小心点掉了QAQ

至此，问题解决！

---

最后展示一下我愚蠢的尝试过程

![]({{ "/assets/img/2020-07-02-10-22-20.png" |  }})



