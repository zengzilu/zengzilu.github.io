---
title: "Github Page + Hugo"
date: 2023-12-02T21:19:07+08:00
draft: false
---

使用github page + hugo完成博客搭建，无需购买任何服务。github作为存储，hugo将md渲染为静态页面，加上github page完成静态博客

## 部署实操
1. hugo安装`brew install hugo`
2. 本地hugo项目构建
   1. 创建hugo项目`hugo new site zorro-blog`
   2. 下载theme，可以到[官网](https://themes.gohugo.io/)选择，每个theme的介绍中会有本theme的安装和使用方法，这里使用theme [next](https://themes.gohugo.io/themes/hugo-theme-next/)
      1. `git submodule add git@github.com:hugo-next/hugo-theme-next.git themes/hugo-theme-next`
      2. `cp themes/hugo-theme-next/exampleSite/config.yaml .`
      3. `mv config.toml config.toml.backup`
   3. 本地启动项目
      1. `hugo server -t hugo-theme-next  --config config.yaml`通过回显的本地地址查看效果
   4. 构建静态页面
      1. `hugo -t hugo-theme-next  --config config.yaml`
      2. 将构建的结果从public目录移动到docs目录`mkdir -p docs; cp -r public/* docs`
3. 创建git仓库&使用github page

![image.png](../../img/github-page-+-hugo/new-git-repo.jpg)

4. 提交本地项目到远端
   1. `git init`
   2. `git remote add origin git@github.com:zengzilu/zengzilu.git`
   3. 全部提交到远端，add commit push 
5. 设置github page配置

![image.png](../../img/github-page-+-hugo/github-page-setting.png)


## 附加项

### 评论配置

评论是有状态的，设计到存储问题，无法在纯静态的页面完成功能。需要借助外部服务完成，此处推荐一个完全免费的方案vercel + waline + leanCloud。
leanCloud是一个云上数据库，waline是一个评论管理服务。vercel是一个servless服务商。  

开启评论的步骤是
1. 注册leanCloud，创建数据库 [部署参考](https://waline.js.org/guide/get-started/)
2. 注册vercel，将waline部署到vercel并配置存储到leanCloud [部署参考](https://waline.js.org/guide/get-started/#vercel-%E9%83%A8%E7%BD%B2-%E6%9C%8D%E5%8A%A1%E7%AB%AF)
3. 将hugo theme next的评论开启，并配置接入方式为waline
安装 waline插件 `npm install @waline/hexo-next`
![comment-enable.jpg](../../img/github-page-+-hugo/comment-enable.jpg)
![comment-waline-setting.jpg](../../img/github-page-+-hugo/comment-waline-settings.jpg)



   


