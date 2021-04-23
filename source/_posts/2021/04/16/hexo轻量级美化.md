---
title: hexo轻量级美化
categories:
  - 工具
  - Hexo
tags:
  - Hexo
abbrlink: 1d687606
date: 2021-04-16 12:31:43
---

使用`NexT`主题对网站进行美化，拒绝无意义的插件，保留最干净的文档环境。

<!-- more -->

## _config.yaml 站点基础配置

### 网站信息

``` yaml
# 网站标题
title: Deven's NoteBook
subtitle: ''
description: ''
keywords:
# 作者
author: Deven Zhou
# 语言，从cn修改为zh-CN
language: zh-CN
# 时区，修改为上海
timezone: 'Asia/Shanghai'
```

### 链接信息

链接信息用于配置当前网站的URL及文档定位URL信息

```yaml
# 网站链接
url: https://devenzhou.github.io
# 文章链接规则
permalink: :year/:month/:day/:title/
permalink_defaults:
pretty_urls:
	# 是否移除index.html后缀
  trailing_index: true
  # 是否移除.html后缀
  trailing_html: true 
```

### 文章写作信息

以下信息用于规定文档的存储结构、高亮信息等。

```yaml
# 文章名称规则，建议根据日期进行管理
new_post_name: :year/:month/:day/:title.md
default_layout: post
titlecase: false
external_link:
  enable: true
  field: site
  exclude: ''
filename_case: 0
render_drafts: false
# 是否在创建文档的同时创建对应的静态资源文件夹
post_asset_folder: true
relative_link: false
future: true
highlight:
  enable: true
  line_number: true
  # 是否自动检测代码语言
  auto_detect: true
  tab_replace: ''
  wrap: true
  hljs: false
prismjs:
  enable: false
  preprocess: true
  line_number: true
  tab_replace: ''
```

### GitHub部署

> 如果您不是使用的GitHub Page，则可以跳过此章节。

#### 配置SSH免密登陆

进入[GitHub SSH管理](https://github.com/settings/keys)页面，添加`SSH keys`

#### 安装deploy插件

``` bash
# 进入hexo站点目录
$ cd hexo-site
# 安装git插件
$ npm install hexo-deployer-git --save
```

#### 配置自动部署

```yaml
deploy:
  type: git
  # 换成自己的github仓库地址
  repo: git@github.com:devenzhou/devenzhou.github.io.git
  # 分支
  branch: master
  message: 'update blob'
  # 提交修改的用户名及邮箱
  name: deven
  email: zttmax@126.com
```

## NexT主题

`NexT`是一个高品质且优雅的`Hexo`主题，我们使用该主题简单的美化站点。

### 安装

```bash
$ cd hexo-site
$ git clone https://github.com/next-theme/hexo-theme-next themes/next
```

### 修改Hexo配置文件

修改`_config.yaml`文件，指定主题为`next`

```yaml
theme: next
```

### 安装canvas-nest背景动画

#### Step1 &rarr;切换到Hexo目录

```bash
$ cd hexo-site
# 此文件夹下必须有`source`、`themes`以及一些其他文件
$ ls
scaffolds  source  themes  _config.yml  package.json
# 下载nest源码到next的lib文件夹下
$ git clone https://github.com/theme-next/theme-next-canvas-nest themes/next/source/lib/canvas-nest
```

#### Step2 &rarr;创建`footer.swig`文件

在`source/_data`目录下创建`footer_swig`文件，如果`_data`目录不存在，请手动创建。

`footer_swig`问价内容如下：

```html
<script color="0,0,255" opacity="0.5" zIndex="-1" count="99" src="/lib/canvas-nest/canvas-nest.min.js"></script>
```

#### Step3 &rarr;修改Next配置文件

修改`themes/next/_config.yaml`文件

```yaml
custom_file_path:
  #head: source/_data/head.njk
  #header: source/_data/header.njk
  #sidebar: source/_data/sidebar.njk
  #postMeta: source/_data/post-meta.njk
  #postBodyEnd: source/_data/post-body-end.njk
  #footer: source/_data/footer.njk
  # 指定刚刚创建的脚本
  footer: source/_data/footer.swig
  #bodyEnd: source/_data/body-end.njk
  #variable: source/_data/variables.styl
  #mixin: source/_data/mixins.styl
  #style: source/_data/styles.styl
```

### 内容透明度调整

在`source/_data`目录下创建`styles.styl`文件，追加以下内容：

```css
//博客内容透明化
//文章内容的透明度设置
.content-wrap {
  opacity: 0.9;
}
.content {
	border-radius: 20px; //文章背景设置圆角
	padding: 80px 30px 10px 30px;
	background:rgba(255, 255, 255, 0.2) none repeat scroll !important;
}

//侧边框的透明度设置
.sidebar {
  opacity: 0.9;
}

//菜单栏的透明度设置
.header-inner {
  background: rgba(255,255,255,0.9);
}

//搜索框（local-search）的透明度设置
.popup {
  opacity: 0.9;
}

.tag-cloud-tags{
	margin-top: 3%;
}
.tag-cloud a {
	-webkit-box-shadow: 0 1px 3px rgba(0,0,0,.12),
	0 1px 2px rgba(0, 0, 0, .24);
	-moz-box-shadow: 0 1px 3px rgba(0,0,0, .12),
	0 1px 2px rgba(0,0,0, .24);
	box-shadow: 0 1px 3px rgba(0, 0,0 .12),
	0 1px 2px rgba(0,0,0, .24);
	transition: .2s ease-out;
	padding: 2px 10px;
	margin: 8px;
	background: #eee;
	border-bottom: none;
	border-radius: 12px;
	box-shadow: 0 1px 3px #6f42c1, 0 1px 2px #d9534f;
	display: inline-block;
}
.tag-cloud a:hover{
	text-decoration: none;
	background: #64ceaa;
	color: #fff !important;
	-webkit-box-shadow: 0 8px 16px 0 rgba(0,0,0,.2),
	0 6px 20px 0 rgba(0, 0, 0, .19);
	-moz-box-shadow: 0 8px 16px 0 rgba(0,0,0, .2),
	0 6px 20px 0 rgba(0,0,0, .19);
	box-shadow: 0 8px 16px 0 rgba(0, 0,0 .2),
	0 6px 20px 0 rgba(0,0,0, .19);
}
```

同时在`source/_data`目录下创建`variables.styl`文件，内容如下：

```css
// 圆角设置
$border-radius-inner     = 20px 20px 20px 20px;
$border-radius           = 20px;
```

修改next配置文件`thmems/next/_config.yaml`

```yaml
custom_file_path:
  #head: source/_data/head.njk
  #header: source/_data/header.njk
  #sidebar: source/_data/sidebar.njk
  #postMeta: source/_data/post-meta.njk
  #postBodyEnd: source/_data/post-body-end.njk
  #footer: source/_data/footer.njk
  footer: source/_data/footer.swig
  #bodyEnd: source/_data/body-end.njk
  variable: source/_data/variables.styl
  #mixin: source/_data/mixins.styl
  style: source/_data/styles.styl
```

### 其他配置

以下所有配置均在`themes/next/_config.yaml`中

#### 风格

next支持`Muse`、`Mist`、`Pisces`和`Gemini`风格，根据自己的喜好调整。

```yaml
# Schemes
#scheme: Muse
#scheme: Mist
#scheme: Pisces
scheme: Gemini
```

#### icon

选择自己喜欢的图片放入`themes/next/source/images`文件夹内，并替换掉`small`、`medium`对应的值。

```yaml
favicon:
  small: /images/favicon-16x16-next.png
  medium: /images/favicon-32x32-next.png
  apple_touch_icon: /images/apple-touch-icon-next.png
  safari_pinned_tab: /images/logo.svg
  #android_manifest: /manifest.json
```

#### 菜单

新增Hexo页面

```bash
$ cd hexo-site
$ hexo new page 'about'
$ hexo new page 'tags'
$ hexo new page 'categories'
$ hexo new page 'archives'
```

执行以上命令后，会在`source`目录下产生对应名称的文件夹，修改对应文件夹下的`index.md`文件

```markdown
<!-- about/index.md -->
---
title: about页面名称
date: 2021-04-15 20:51:54
type: about
---
<!-- archives/index.md -->
---
title: archives页面名称
date: 2021-04-15 20:51:54
type: archives
---
<!-- categories/index.md -->
---
title: categories页面名称
date: 2021-04-15 20:51:54
type: categories
---
<!-- tags/index.md -->
---
title: tags页面名称
date: 2021-04-15 20:51:54
type: tags
---
```

修改`themes/next/_config.yaml`启动以上页面

```yaml
menu:
  home: / || fa fa-home
  about: /about/ || fa fa-user
  tags: /tags/ || fa fa-tags
  categories: /categories/ || fa fa-th
  archives: /archives/ || fa fa-archive
  #schedule: /schedule/ || fa fa-calendar
  #sitemap: /sitemap.xml || fa fa-sitemap
  #commonweal: /404/ || fa fa-heartbeat

# Enable / Disable menu icons / item badges.
menu_settings:
  icons: true
  badges: false
```

#### 头像

挑选一张头像图片放入`themes/next/source/images`文件夹，并修改url

```yaml
avatar:
  # 头像文件路径
  url: /images/avatar.gif
  # 是否使用圆形头像
  rounded: true
  # 是否启用头像转动
  rotated: false
```

#### tag图标

tag模型使用#作为前缀，可以修改配置启动tag图标

```yaml
tag_icon: true
```

#### 打赏

进入`支付宝`、`微信`获取收款码，存入`themes/next/source/images`并替换以下文件名称

```yaml
reward:
  wechatpay: /images/wechatpay.png
  alipay: /images/alipay.png
  #paypal: /images/paypal.png
  #bitcoin: /images/bitcoin.png
```



