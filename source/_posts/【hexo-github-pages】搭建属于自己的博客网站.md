---
title: 【hexo + github pages】搭建属于自己的博客网站
abbrlink: 53595
date: 2022-03-23 17:50:05
tags:
- Hexo
categories:
- Hexo
---

今天在翻看自己GitHub的时候，忽然发现了那会刚开始做前端的时候搭建的博客，好几年前了，看到新奇的东西就想自己动手鼓捣一下，回想起那会搭建的时候也是费了老鼻子的劲了，最近一年也会偶尔在CSDN写博客记录点东西，那便记录一下怎么利用GitHub和hexo来搭建一个属于自己的博客网站。
<!-- more -->
## 用Hexo + GitHub 搭建自己的博客网站

### **什么是[hexo](https://hexo.io/zh-cn/)**

官方给我们的描述是快速、简洁且高效的博客框架。Hexo是一款基于Node.js的静态博客框架，依赖少易于安装使用，支持 **Markdown** 的所有功能，一键部署，只需要一个指令就可以部署到`github pages`或者其他平台，支持多种模板引擎和工具。

### 安装搭建hexo

要用GitHub 和 hexo 搭建个人的博客网站，首先必须有自己的github账号没什么问题吧，其次需要提前准备的环境：下载安装`git`, `nodeJs`，这个怎么去安装我想应该不用说了吧（真不知道的话分别百度nodejs， git去官网点击下载安装即可）。准备好环境后我们还要安装 `hexo`:

```js
npm install hexo-cli -g
```

前面安装了`nodejs`，现在就i可以直接用 `npm`安装 `hexo`，同时按下 `window + R` 键，输入 `cmd` 打开终端，执行上面的命令，等待安装完成，完成以后可用

`hexo -v` 查看版本，同时也是验证是否安装完成。

![hexo](https://img-blog.csdnimg.cn/b53f0798d69b4162a5d94b8d43fbb7be.png)

如上图说明我们已经安装完成了，然后我们来初始化我们的hexo项目:

```js
// blog 是你的项目名字，取什么名字都行您随意
hexo init blog
```

然后进入你的项目中，安装依赖：

```node
cd blog // 进入项目中
npm install // 安装依赖包
```

完成后你的项目目录应该包含：

+ node_modules：依赖包
+ scaffolds：生成文章的模板
+ source：存放你写的文章
+ themes：主题
+ _config.yml：博客的配置文件

```hexo
hexo server
```

打开hexo的服务，在浏览器输入http://localhost:4000/就可以打开你的博客了。



### GitHub创建个人仓库

前面说过你要有自己的 `github` 账号，如果你还没有，去注册一个吧，注册完成后登录到GitHub页面，你会看到一个 `New repository`， 创建一个和你用户名**同名**的仓库，后面加上`.github.io`， 只有这样将来部署到 Github Page 的时候， 才会被识别， 也就是 用户名.github.io， 我已经创建过了，再次创建会提示 `The repository **xxx.github.io** already exists on this account.`，表示我这个账户已经创建过这个仓库。

如果你已经创建完成了和你注册GitHub同名的仓库，下面我们来生成ssh密钥：

在你项目文件夹点击鼠标右键，点击 `git base hero`, 打开你的 git base 后，在base中分别输入：

```git
git config --global user.name "yourname" // yourname输入你的github用户名
git config --global user.email "youremail" // youremail输入你GitHub的邮箱
```

可以检查一下你有没有输对

```git
git config user.name
git config user.email
```

### 配置GitHub ssh密钥

创建ssh密钥，一路回车，可以不设置密码

```
ssh -keygen -t rsa -C "youremail"
```

生成完成后，进入你的用户名文件夹下，找到`.ssh` 文件夹，里面有两个文件。这个就是密钥，其中 `id_rsa`是你电脑的私人密钥，`id_rsa.pub` 是公共密钥。我们要做的就是把公钥配置到GitHub中，这样当你访问链接自己的GitHub账号时，它就会根据公钥配到你的私钥，当能达到匹配的时候，你就能通过git上传你的项目到GitHub中了。

下面我们来配置自己的ssh密钥，进入你的GitHub页面，点击右上角你的账号头像，在下拉菜单中找到 `settings` 菜单，点击进入设置页面，然后在设置页面左边的菜单分类中找到 `Access` 下面的 `SSH and GPG keys` 菜单，然后点击 `New SSH key` 按钮，把你本地创建的公钥复制后粘贴到`key` 的输入框中， `title` 随便输都行，然后保存。在gitbase中查看是否成功

```js
ssh -T git@github.com
```

### 将hexo部署到GitHub

 如何将hexo和github关联起来呢，那就要把hexo生成文章部署到GitHub上，打开站点配置文件`_config.yml`, 翻到最后，修改配置：xxx为你的github账户

```yaml
# Deployment
## Docs: https://hexo.io/docs/deployment.html
deploy:
  type: git
  repo: https://github.com/xxx/xxx.github.io.git
  branch: master
```

要完成部署操作，你还需要安装 `deploy-git `：

```node
npm install hexo-deployer-git --save
```

然后我们需要了解一下hexo的常用命令：

```js
// 新建一个网站，如果没设置 floder hexo默认在当前文件夹下创建网站
hexo init [flolder]    
// 新建一篇文章，如果没有设置 layout 的话，默认使用 _config.yml 中的 default_layout 参数代替。如果标题包含空格的话，请使用引号括起来。
hexo new [layout] <title> 
// 生成静态文件。
hexo generate  //  hexo g -d, 文件生成后立即部署网站
// 发表草稿
hexo publish [layout] <filename>
// 启动服务器。默认情况下，访问网址为： http://localhost:4000
hexo server  
// 部署网站, 可以简写为hexo d
hexo deploy 
// 清除缓存文件 (db.json) 和已生成的静态文件 (public)
hexo clean
```

`hexo generate` 顾名思义，生成静态文章，可以用 `hexo g`缩写
`hexo deploy` 部署文章，可以用`hexo d`缩写

当然你也可以用 `hexo g -d` 一步完成部署。

> 如果在执行部署网站的时候出现下列错误: ”Software caused connection abort  fatal: Could not read from remote repository.”, 很可能是dns解析问题，用 `ssh -T git@github.com` 在gitbase中检测是否正常，打开cmd输入`ping github.com`是否能连接，配置本地的`hosts` 文件， 文件路径 `c:\windows\system32\drivers\etc\hosts`,在末尾添加上：
>
> ```js
> 140.82.112.4  github.com git 
> 140.31.16.184 github.global.ssl.fastly.net
> ```
>
> gitbase 再次`ssh -T git@github.com`成功。

## hexo的基本配置

### 网站 (# site)

| 参数        | 描述                                                         |
| ----------- | ------------------------------------------------------------ |
| title       | 网站标题                                                     |
| subtitle    | 网站的副标题                                                 |
| description | 网站描述                                                     |
| keywords    | 网站的关键词。支持多个关键词。                               |
| author      | 作者名字                                                     |
| language    | 网站使用的语言。对于简体中文用户来说，使用不同的主题可能需要设置成不同的值，请参考你的主题的文档自行设置，常见的有 `zh-Hans`和 `zh-CN`。 |
| timezone    | 网站时区。Hexo 默认使用您电脑的时区。般的，对于中国大陆地区可以使用 `Asia/Shanghai`。 |

### 网址(#URL)

| 参数                       | 描述                                                         | 默认值                    |
| -------------------------- | ------------------------------------------------------------ | ------------------------- |
| url                        | 网址, 必须以 `http://` 或 `https://` 开头                    |                           |
| root                       | 网站根目录                                                   | /                         |
| permalink                  | 文章的 [永久链接](https://hexo.io/zh-cn/docs/permalinks) 格式 | :year/:month/:day/:title/ |
| permalink_defaults         | 永久链接中各部分的默认值                                     |                           |
| pretty_urls                | 改写 [`permalink`](https://hexo.io/zh-cn/docs/variables) 的值来美化 URL |                           |
| pretty_urls.trailing_index | 是否在永久链接中保留尾部的 `index.html`，设置为 `false` 时去除 | true                      |
| pretty_urls.trailing_html  | 是否在永久链接中保留尾部的 `.html`, 设置为 `false` 时去除 (*对尾部的 `index.html`无效*） | true                      |

我们在配置文件中将url改成自己的网站域名，permalink是我们生成文章时候的那个链接格式。链接的变量很多，可以点击上面的永久链接去官方文档查找配置。

### 目录#Directory

```yaml
# Directory
source_dir: source # 资源文件夹，这个文件夹用来存放内容。
public_dir: public # 公共文件夹，这个文件夹用于存放生成的站点文件。
tag_dir: tags			# 标签文件夹
archive_dir: archives # 归档文件夹
category_dir: categories # 分类文件夹
code_dir: downloads/code # Include code 文件夹，source_dir 下的子目录
i18n_dir: :lang    # 国际化（i18n）文件夹
skip_render: 				# 跳过指定文件的渲染
```

> 如果您刚刚开始接触 Hexo，通常没有必要修改这一部分的值。

### 文章#Writing

```yaml
# Writing
new_post_name: :title.md  # 新文章的文件名称
default_layout: post     # 预设布局
titlecase: false       # 把标题转换为 title case
auto_spacing: false     # 在中文和英文之间加入空格
external_link:
  enable: true # Open external links in new tab
  field: site # Apply to the whole site
  exclude: '' # 需要排除的域名
filename_case: 0  # 把文件名称转换为 (1) 小写或 (2) 大写
render_drafts: false 	# 显示草稿
post_asset_folder: false # 启动 Asset 文件夹
relative_link: false # 把链接改为与根目录的相对位址
future: true # 显示未来的文章
highlight: # 代码块的设置, 请参考 Highlight.js 进行设置
  enable: true
  line_number: true
  auto_detect: false
  tab_replace: ''
  wrap: true
  hljs: false
prismjs: # 代码块的设置, 请参考 PrismJS 进行设置
  enable: false
  preprocess: true
  line_number: true
  tab_replace: ''
```

### 分类 & 标签

```yaml
# Category & Tag
default_category: uncategorized # 默认分类
category_map: # 分类别名	
tag_map: # 标签别名	
```

### 分页

```yaml
# Pagination
per_page: 10 # 每页显示的文章量 (0 = 关闭分页功能)	
pagination_dir: page # 分页目录
```

### 主题

通常情况下，Hexo 主题是一个独立的项目，并拥有一个独立的 `_config.yml` 配置文件。

除了自行维护独立的主题配置文件，你也可以在其它地方对主题进行配置。

hexo官网有300多个[主题](https://hexo.io/themes/)，在这里下载你喜欢的主题进行修改就可以了。直接在github链接上下载下来，然后放到`theme`文件夹下就行了，然后再在刚才说的配置文件中把`theme`换成那个主题文件夹的名字，它就会自动在`theme`文件夹中搜索你配置的主题。

我们也可以自定义自己的主题，或者修改已经安装的主题的样式。