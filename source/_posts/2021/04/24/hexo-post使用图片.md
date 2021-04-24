---
title: hexo post使用图片
abbrlink: 61d095f6
date: 2021-04-24 13:38:48
categories:
- 工具
- Hexo
tags:
- Hexo
---

在编写 hexo 文章时，如果文章中引入了图片资源，我们可以通过以下几种方式进行引入：

1. 将图片存入CDN
2. 将图片存放在hexo静态资源文件夹
3. 将图片放入文章同名目录

<!-- more -->

## 将图片存入CDN

将图片放入CDN可以加快图片的加载速度，但是无疑会增加我们的工作量，因此，如果您已经有了自己的CDN服务，可以使用这种方式进行引用：

```markdown
![图片描述](https://你的CDN生成的链接)
```

## 将图片存放在hexo静态资源文件夹

资源（Asset）代表 source 文件夹中除了文章以外的所有文件，例如图片、CSS、JS 文件等。比方说，如果你的Hexo项目中只有少量图片，那最简单的方法就是将它们放在`source/images`文件夹中。然后通过类似于`![](/images/image.jpg)`的方法访问它们。

## 将图片放入文章同名目录

对于那些想要更有规律地提供图片和其他资源以及想要将他们的资源分布在各个文章上的人来说，Hexo也提供了更组织化的方式来管理资源。这个稍微有些复杂但是管理资源非常方便的功能可以通过将 config.yml 文件中的 post_asset_folder 选项设为 true 来打开。

```yaml
post_asset_folder: true
```

当资源文件管理功能打开后，Hexo将会在你每一次通过 `hexo new [layout] <title>` 命令创建新文章时自动创建一个文件夹。这个资源文件夹将会有与这个文章文件一样的名字。将所有与你的文章有关的资源放在这个关联文件夹中之后，你可以通过相对路径来引用它们，这样你就得到了一个更简单而且方便得多的工作流。

对于hexo版本3.1.0之前的版本，您可以使用以下占位符链接图片，而不应该使用markdown标记的方式:

``` yaml
{% asset_path slug %}
{% asset_img slug [title] %}
{% asset_link slug [title] %}
```

`slug`表示图片的相对路径, `[title]`表示图片名，这个是可选的。

但对于3.1.0以上的版本，你可以启动以下选项，并使用markdown语法引入图片

```yaml
post_asset_folder: true
marked:
  prependRoot: true
  postAsset: true
```