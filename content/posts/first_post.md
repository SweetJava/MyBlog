---
title: "First_post"
date: 2021-05-05T16:45:37+08:00
draft: false
---

注意
在构建网站时, 你可以使用 --theme 选项设置主题. 但是, 我建议你修改配置文件 (config.toml) 将本主题设置为默认主题.
2.4 创建你的第一篇文章
以下是创建第一篇文章的方法:

1
hugo new posts/first_post.md
通过添加一些示例内容并替换文件开头的标题, 你可以随意编辑文章.

注意
默认情况下, 所有文章和页面均作为草稿创建. 如果想要渲染这些页面, 请从元数据中删除属性 draft: true, 设置属性 draft: false 或者为 hugo 命令添加 -D/--buildDrafts 参数.
2.5 在本地启动网站
使用以下命令启动网站:

1
hugo serve
去查看 http://localhost:1313.
