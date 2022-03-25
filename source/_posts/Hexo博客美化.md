---
title: Hexo博客美化
abbrlink: 7259
date: 2022-03-25 10:53:23
tags:
- hexo
categories:
- Hexo
---
# Hexo博客美化

我们搭建好自己的博客以后，可以在hexo官网的 [主题](https://hexo.io/themes/) 中选择自己喜欢的博客主题，可以直接在主题中点开预览主题样式或者打开主题项目的 `github` 地址，将该主题下载到我们自己的博客项目中的 `theme` 文件夹中，然后在 `_config.yml` 文件中找到 `theme` 修改为你主题的名字，重新编译启动你的项目，就可以替换为你喜欢的主题了。当然除了更换主题为，你也可以自定义你自己的主题，修改它的样式，或者干脆按照自己理想的布局和样式来自己属于自己的完美主题。除此之外，我们的博客还可以支持一些第三方的库，来给我们的博客增加更多的功能。

[我的博客](https://houwhu.github.io/)之前的主题是按照自己的喜好自定义的主题，最近决定换成 `next`主题，我们今天会讲如何在我们的博客中集成浏览量，浏览人数，搜索，评论，看板娘等各种功能，**本文这些设置和集成都是基于Next 主题集成的**，其他主题方法都一样，具体的各位看官们根据自己主题提供的 `_config_yml`文件灵活处理。

[toc]

> 本文所有的设置和插件都是基于 `next` 主题配置的，其他主题方法都类似，具体的配置字段参考自己下载主题的 `_config.yml`文件提供的字段，有些不知道怎么配置字段的，可以找到自己主题对应部位的模板文件去看代码然后做相应的配置，如果模板中没有相应的代码，可以自己定义去做修改。
>
> 因为博客和主题文件夹下都有`_config.yml` 文件，下文为了方便区分，我们把我们的博客的配置文件叫 `_config.yml`，主题下面的配置文件称为 `_config.theme.yml`，看官们注意，下文看到 `_config.theme.yml`文件的描述，可别说自己的项目中没有这个东西。

## 基础配置

在之前的[博客搭建](https://blog.csdn.net/houwhu/article/details/123692095) 中，我们就讲了一些基础的配置项，比如网站的标题，图标等，这里将不再多说，我们这里主要讲`next`主题的一些设置。

### 菜单

#### 菜单配置

在我们`_config.theme.yml`中找到 `menu`字段，下面就是我们菜单的相关配置，可以看到我们的菜单如下所示：

```yaml
menu:
  home: / || fa fa-home
  tags: /tags/ || fa fa-tags
  categories: /categories/ || fa fa-th
  archives: /archives/ || fa fa-archive
  # schedule: /schedule/ || fa fa-calendar
  about: /about/ || fa fa-user
  # sitemap: /sitemap.xml || fa fa-sitemap
  guestbook: /guestbook/ || fa fa-commenting

```

我们看到关于菜单的组成部分是由三部分组成，`key`为我们菜单的名称，`value`由两部分组成，前面部分为我们菜单对应的页面组成，我们点击该菜单后会跳转到对应的页面去，中间由`||`隔开，后面的部分为菜单对应的图标。因为`hexo`主题集成了[fontawesome](http://www.fontawesome.com.cn/)字体图标，后面对应的部分就是我们字体图标对应的类名，现在该字体库大概收录了将近700个图标，我们可以找到自己想要的图标，点击后就可以查看到该图标对应的类型，复制即可。

#### 图标的展示配置和角标的配置：

```yaml
menu_settings:
  icons: true
  badges: true
```

至于对应的页面，我们需要用命令去添加对应的文件类型就可:

```js
hexo new page <menuname>
```

用上面命令对应我们的菜单生成相对应的页面，生成普通的文章直接用命令`hexo new 'title'` 或者 `hexo new post 'title'`，因为我们的默认类型就是文章，所以可以省略`post`直接添加一篇新的博客。当然我们也可以在我们博文的头部去做一些简单的配置，比如 `title, date, tags...`等。

### 阅读全文

因为我们的博客会有很多，所以在首页展示的时候不可能每篇文章都展开去展示，这就只需要在首页展示博客的开头一部分去作为摘要显示，用小块的部分在首页展示排列，然后通过按钮点击查看全文，我们不做处理的话文章默认都是展开的，我们只需要在编辑我们的博文的时候，在你想要在首页只展示的部分添加一行代码`<!-- more -->`标识去做分割，我们的博客就会自动在首页在你添加标识的地方切割，然后生成 **阅读全文**按钮，我们通过点击进入全文，当然这个文字和样式我们也都可以根据自己的审美喜欢自行修改。`_config.theme.yml`中修改：

```js
read_more_btn: true
```

### 社交

我们只要找到`_config.theme.yml`中 的`social`字段，配置格式和前面提到的菜单的配置格式一样，我们只要找到自己想要配置的社交平台对应的图标简单配置就行，当然如果你不满足于该配置或者想做更个性化的配置的话，我们可以通过自定义的方式来添加自己想要的图标。而要显示我们配置的图标，则需要将`social_icons`下面的`enable`设置为`true`即可：

```yaml
social_icons:
  enable: true
  icons_only: true
  transition: true 
```

这里用`svg`格式的图片做自定义配置为例：我们可以在[阿里的图标矢量库](https://www.iconfont.cn/)中找到你想配置的图标，点击下载，选择`svg下载`，将下载的图片保存到我们的目录`themes/next/source/images`文件夹下，在`themes/next/source/css`文件夹下新建 `_cunstom` 文件夹，然后创建 `iconfont.styl`文件，在里面自定义我们的图标样式：

```stylus
/* sidebar social icon */
.common {
  display: flex;
  background-size: 1.5rem;
  opacity: 0.85;
  background-position: center;
  background-repeat: no-repeat;
  height: 1.5rem;
  width: 1.5rem; 
  border-radius: 0rem;
  /*鼠标停留在图标上时，图标呈现发光效果*/
  &:hover {
      opacity: 1;
    }
}
.csdn {
  background-image: url('/images/csdn.svg');
}
.github {
   background-image: url('/images/GitHub.svg');
}
...
```

这样我们就定义好了我们要的图标样式和图片，然后在我们的`_config.theme.yml`文件中修改配置：

```yaml
social:
  GitHub: https://github.com/xxx || common github
  CSDN: https://blog.csdn.net || common csdn
  ...
```

> 注意：我们自定义的样式文件需要导入到我们的 `main.styl`中。

这样我们就完成了社交模块的自定义配置。

### 语言配置

在根目录`_config.yml`文件中找到 `language`，设置为你想要设置的语言即可。打开`themes/next/languages`，可以看到有很多中语言，我们只需要将我们想要的语言设置即可，该主题支持国际化语言，我们配置的菜单图标等自己定义的字段，在自己设置的语言文件中添加对应的字段和展示文本即可。

> 注意：`next`主题中文设置可能与`next`的文档有些出入，当你设置了`zh-CN`可能无效，打开我们的语言文件夹，我们看到中文的文件叫`zh-Hans`，我们只需要将设置语言的地方改为该字段，或者将中文配置文件名改成`zh-CN.yml`都可以。

### 文章底部设置

#### 添加版权说明

我们可以在文章增加版权说明表明文章的作者，链接以及转载的信息等，如下图所示：

> - **本文作者：** Axe
> - **本文链接：** https://houwhu.github.io/hwh-blog.github.io/posts/53595.html
> - **版权声明：** 本博客所有文章除特别声明外，均采用 [BY-NC-SA](https://creativecommons.org/licenses/by-nc-sa/4.0/zh-Hans) 许可协议。转载请注明出处！

`next`主题已经为我们添加了版权说明，我们只需要做简单配置就能为我们的文章添加版权说明：

首先，打开`_config.theme.yml`文件，找到`footer`，在下面找到`post_copyright`，将其设置为可见：

```yaml
# If not defined, `author` from Hexo `_config.yml` will be used.
  post_copyright:
    enable: true
    license: CC BY-NC-SA 3.0
    license_url: https://creativecommons.org/licenses/by-nc-sa/3.0/
```

然后打开`_config.yml`，找到`url`，把内容改成自己的博客域名就可以了。

这样设置以后我们的每篇博文都会增加该说明，当然我们在不需要添加该说明的时候，我们只需要在该文章顶部的配置中添加`copyright: false`就可以了。

#### 添加分享

分享的插件有很多，比如百度分享，多说等，我这里用need-more-share2，配置简单：

```yaml
needmoreshare:
  enable: false
  postbottom:
    enable: false
    options:
      iconStyle: box
      boxForm: horizontal
      position: bottomCenter
      networks: Weibo,Wechat,Douban,QQZone,Twitter,Facebook
  float:
    enable: false
    options:
      iconStyle: box
      boxForm: horizontal
      position: middleRight
      networks: Weibo,Wechat,Douban,QQZone,Twitter,Facebook
```

#### 开启文章打赏

开启主题下的配置文件：

```yaml
reward_settings:
  # If true, a donate button will be displayed in every article by default.
  enable: true
  animation: false
  comment: 坚持原创技术分享，您的支持将鼓励我继续创作！

reward:
  wechatpay: /images/wechatpay.png
  alipay: /images/alipay.jpg
```

在`reward`中添加你的用于打赏的收款码，如果你觉得支付宝微信的收款码不好看，你可以在线生成二维码。

## 添加评论系统

评论系统的插件比较多，我这里添加的是`gitalk`，配置简单，样式简洁美观.

### 申请gitalk

申请网址：[https://github.com/settings/applications/new](https://github.com/settings/applications/new)，填写的这个信息后面是可以修改的，所以放心大胆的填，不要担心填错了。

![申请gitalk](https://img-blog.csdnimg.cn/8cdc6044756e4c36a471bd48fd1b219c.png)

注册完成后，进入 `settings/ Developer settings` 找到 `OAuth Apps`， 在这里，你就能看到`clientID`和`clientSecret`啦。把页面往下翻，能看到你刚刚填写得信息。如果你觉得不对，你可以重新填写，然后点击`Update application`，更新一下。

这里顺带提一下，平时我们怎么打开这个页面。进入你的GitHub主页，右上角点击`Settings`，点击`Developer settings`，进入APP界面，点击`OAuth Apps`，如果你申请好了，就会在这里看到。同样你也可以在右小角点击`New OAuth App`新建，和刚刚[https://github.com/settings/applications/new](https://github.com/settings/applications/new)的效果是一样的。

### **修改博客配置**

首先：`_config.theme.yml`

```yaml
comments:
  # Available values: tabs | buttons
  style: tabs
  # Choose a comment system to be displayed by default.
  # Available values: disqus | disqusjs | changyan | livere | gitalk | utterances
  active: gitalk
  # Setting `true` means remembering the comment system selected by the visitor.
  storage: true
  # Lazyload all comment systems.
  lazyload: false
  # Modify texts or order for any naves, here are some examples.
  nav:
    #disqus:
    #  text: Load Disqus
    #  order: -1
    gitalk:
      order: -1
```

然后找到`gitalk`, 添加配置，如果没有自己在`_config.theme.yml`中添加：

```yaml
gitalk:
  enable: true
  github_id: xxx # GitHub的
  repo: blog-comment # 存储issues的仓库名
  client_id: 6167b7xxxxxxx729a12 # GitHub Application Client ID
  client_secret: 07aaf16xxxxxxxxxxxxa8489855be8 # GitHub Application Client Secret
  admin_user: xxxx # GitHub repo owner and collaborators, only these guys can initialize gitHub issues
  distraction_free_mode: true # Facebook-like distraction free mode
  # Available values: en | es-ES | fr | ru | zh-CN | zh-TW
  language: zh-CN
  # When the official proxy is not available, you can change it to your own proxy address
  proxy: https://cors-anywhere.azm.workers.dev/https://github.com/login/oauth/access_token 
```

### **可能碰到的问题**

+ **未找到相关的issues进行评论**：这个问题不大，你点击下面，登入一下你的Guthub账户就好了。

+ **Error: Not Found**： 那一定是你信息没填对，`repo`那里，一定要填仓库名

+ **Error: Validation Failed**：

  ```js
  id: location.pathname,      // Ensure uniqueness and length less than 50
  ```

  就是说，你的整个链接不能太长，如果你链接超过50个字符，那么评论系统就会报错。会出现`Gitalk Error: Validation Failed.`你的链接，默认是根据你设置的名称来的。所以，你给文件命名的时候，注意一下。当然，你也可以用[md5](https://links.jianshu.com/go?to=https%3A%2F%2Fwww.npmjs.com%2Fpackage%2Fmd5)来缩短你的地址。

## 添加本地搜索

该功能依赖`hexo-generator-searchdb`插件，使用命令`npm install hexo-generator-searchdb --save`来进行安装，然后的末尾，加入以下代码即可。

```yaml
search:
  path: search.xml
  field: post
  format: html
  limit: 10000
```

然后开启主题配置文件`_config.theme.yml`中开启本地搜索：

```yaml
# Local Search
# Dependencies: https://github.com/next-theme/hexo-generator-searchdb
local_search:
  enable: true
  # If auto, trigger search by changing input.
  # If manual, trigger search by pressing enter key or search button.
  trigger: auto
  # Show top n results per article, show all results by setting to -1
  top_n_per_article: 1
  # Unescape html strings to the readable one.
  unescape: false
  # Preload the search data when the page loads.
  preload: false
```

## 添加萌萌哒看板娘

查看效果，请移步[我的个人博客](https://houwhu.github.io/)

我们这里用CDN的方式接入，简单方便，大神已经为我们写了一个可以说话，会换装的看板娘并开源，我们用起来也是非常的方便。

### Fork看板娘项目

首先访问 [live2d-widget](https://github.com/stevenjoezhang/live2d-widget) 的 Github 仓库，点击右上角 `Fork` 该项目到自己的仓库：

### 向next中添加看板娘

在 `/themes/hexo-theme-next/layout/_layout.njk` 文件，在最后添加下面这行代码：

```html
<script src="https://cdn.jsdelivr.net/gh/xxx/live2d-widget/autoload.js"></script>
```

> 注意： 请把cdn链接中的xxx换成你自己的GitHub用户名

### 开启看板娘

```yaml
# 自定义看板娘
live2d:
  enable: true
```

然后重新生成部署博客，就看到一个萌萌哒的看板娘出现在了我们博客的左下角。

### 定制看板娘

我们用CDN的方式部署到了我们博客中，我们怎么修改自己的看板娘呢？

#### clone项目到本地

我们前面已经`fork`看板娘项目到自己的仓库了，注意我们这里克隆就是从自己的仓库克隆看板娘项目：

```js
git clone https://github.com/xxx/live2d-widget.git
```

#### 修改文件

看板娘项目中几个文件的作用：

+ `autoload.js`：自动加载看板娘；

- `waifu.css`：看板娘样式；
- `waifu-tips.js`：看板娘说话的脚本；
- `waifu-tips.json`：看板娘说话的内容；

#### 修改加载看板娘的路径

在 `autoload.js` 的开头定义了加载看板娘的路径，注意这里需要使用绝对路径：

```js
//注意：live2d_path参数应使用绝对路径
const live2d_path = "https://cdn.jsdelivr.net/gh/Mculover666/live2d-widget/";
//const live2d_path = "/live2d-widget/";
```

#### 修改样式

`waifu.css`中可以修改看板宁的位置。

修改完成后保存代码，commit push到远程仓库。

#### 发布新版本

我们是使用了Github免费的CDN服务，所以还需要发布一个新的版本：

在我们的代码库找到`release`操作，点击`Draft a new release`，输入新的版本号，点击 `publish release`,修改我们引入的cdn链接，在你的看板娘库名后面添加版本号。

```js
<script src="https://cdn.jsdelivr.net/gh/xxxx/live2d-widget@1.0.0/autoload.js"></script>
```

重新部署博客

```js
hexo clean
hexo g -d
```

## 插件

可以看到我们前面很多配置其实都是依赖了其他的插件，hexo还有很多好玩的插件，可以增强和美化我们的博客，官方目前提供的插件已经多达几百个了，大家可以去 [插件](https://hexo.io/plugins/)去安装配置。