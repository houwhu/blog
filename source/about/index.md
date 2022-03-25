---
title: 关于作者
date: 2022-03-23 09:28:20
---

# 用markdown制作一个简历
----

怎么找到一份合适的工作，首先我们要有一份好的简历，那么大家一般怎么写简历呢，用word写？word写的好处是简单，但是不足时太丑了，在网上找的模板好看是挺好看，但是模板不一定适合自己，而且修改起来特别的麻烦，那么作为一个前端程序员，为什么不用 `markdown` 和 `html` 来制作自己的简历呢。

我们的简历大致上包含这些东西, 列出来以后只需要去设计我们的简历就行：

+ 个人信息:
+ 我的技能 / 擅长技术等
+ 求职意向
+ 工作经验 / 项目经验
+ 教育背景
+ 社交主页：比如技术博客地址，github等。

> 根据上面内容我们大致可以设计成如下格式，然后再填入相关信息。

```markdown
## 姓名
---
## 职位
邮箱/手机号/工作年限和职位

---
### 我的技能
/开发语言/擅长技能/

---
### 求职意向
到岗时间/期望薪水/行业/目标岗位

---
### 工作经验
公司/工作时间/工作描述/主要业绩

----
### 项目经验
项目描述/职责描述

----
### 教育背景
大学/专业

----
### 社交主页
github/博客
```

使用纯文字填充简历，虽然简洁，但是纯文字缺少美感，我们可以将我们的markdown导出成html文件，然后修改字体，调整边距，然后可以修改css样式按照自己的审美调整部分布局和样式，让简历变得更美观生动。我们也可以下载安装字体图标，给我们的简历分类的标题前面添加图标。总之，作为一个前端程序员，当这个markdown转换成html文件后，还不是为所欲为的修改样式。



当然我们也可以不用那么复杂，利用markdown能插入的表情图标来代替html字体图标完成的工作：

-----

```js
## 张三 / zhang san

### 前端开发工程师

+ :e-mail: **邮&ensp;&ensp;&ensp;&ensp;箱：** <font color="#4ea1db">254xxx512@qq.com</font>
+ :phone: **手&ensp;机&ensp;号：** 187xxxxxxxx
+ :alarm_clock: **工作年限：** 2年

---

### :file_folder: 我的技能

+ <div style="display: flex;align-items: center;width: 60%;">
    <span style="width: 50px;">Vue</span>
    <div style="flex:1;background-color: #ddd;">
    	<div style="display: flex;width: 90%;height: 10px;">
    	<div style="text-align: right; padding-right: 20px;height: 10px;line-height: 10px;color: white;width: 90%; background-color: #8B0000;"></div>
  		</div>
  	</div>
  </div>

+ <div style="display: flex;align-items: center;width: 60%;">
    <span style="width: 50px;">React</span>
    <div style="flex:1;background-color: #ddd;">
    	<div style="display: flex;width: 75%;height: 10px;">
    	<div style="text-align: right; padding-right: 20px;height: 10px;line-height: 10px;color: white;width: 90%; background-color: #2196F3;"></div>
  		</div>
  	</div>
  </div>

+ <div style="display: flex;align-items: center;width: 60%;">
    <span style="width: 50px;">Node</span>
    <div style="flex:1;background-color: #ddd;">
    	<div style="display: flex;width: 55%;height: 10px;">
    	<div style="text-align: right; padding-right: 20px;height: 10px;line-height: 10px;color: white;width: 90%; background-color: #f44336;"></div>
  		</div>
  	</div>
  </div>

---

### :file_folder: 求职意向

+ **到岗时间:**
+ **期望薪水:**
+ **目标岗位:**

---

### :file_folder: 工作经验

公司/工作时间/工作描述/主要业绩

----

### :file_folder: 项目经验

项目描述/职责描述

----

### :file_folder: 教育背景

+ **<span align=left>2015-09 到 2019-07</span>**&emsp;&emsp;&emsp;&emsp; **xx师范大学**&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;**研究生**  
+ **<span align=left>2015-09 到 2019-07</span>**&emsp;&emsp;&emsp;&emsp; **xx科技大学**&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;**本 &ensp;科**                       

----

### :file_folder: 社交主页

<img src="https://img-blog.csdnimg.cn/4e998997c23846f997560287de604f67.png" width="30" align='left'/>**github：**

<img src="https://img-blog.csdnimg.cn/b4bf8c3191e04da3b0b0868070b0cff6.png" width=30 align="left"/>**CSDN：**


----

<p align=right style="color: red">@2022 created by zhang san</p>
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/6577892e5fad4b909ba2db2350024f11.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAc21hbGxfQXhl,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)

也可以直接用markdown直接写好简历，部分需要调节样式的用行内样式调节，然后导出未**PDF**或者 **HTML**文件即可，链接打印机的也可以直接打印简历。