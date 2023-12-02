---
title: "Github Page + Hugo"
date: 2023-12-02T21:19:07+08:00
draft: false
---


## 部署实操
1. hugo安装`brew install hugo`
2. 本地hugo项目构建
   1. 创建hugo项目`hugo new site zorro-blog`
   2. 下载theme，可以到官网选择`[https://themes.gohugo.io/](https://themes.gohugo.io/)`，每个theme的介绍中会有本theme的安装和使用方法，这里使用theme [next](https://themes.gohugo.io/themes/hugo-theme-next/)
      1. `git submodule add git@github.com:hugo-next/hugo-theme-next.git themes/hugo-theme-next`
      2. `cp themes/hugo-theme-next/exampleSite/config.yaml .`
      3. `mv config.toml config.toml.backup`
   3. 本地启动项目
      1. `hugo server -t hugo-theme-next  --config config.yaml`通过回显的本地地址查看效果
   4. 构建静态页面
      1. `hugo -t hugo-theme-next  --config config.yaml`
      2. 将构建的结果从public目录移动到docs目录`mkdir -p docs; cp -r public/* docs`
3. 创建git仓库&使用github page

![image.png](/img/github-page-+-hugo/new-git-repo.jpg)

4. 提交本地项目到远端
   1. `git init`
   2. `git remote add origin git@github.com:zengzilu/zengzilu.git`
   3. 全部提交到远端，add commit push 
5. 设置github page配置

![image.png](/img/github-page-+-hugo/github-page-setting.png)


