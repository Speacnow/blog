---
title: hexo与typora图片路径引用方式保持一致
typora-copy-images-to: hexo与typora图片路径引用方式保持一致
date: 2022-03-11 15:29:07
tags: [hexo,next]
categories: hexo
description: 
---
hexo的变态引入图片方式就不用多说了吧，typora作为当前最优雅和流行markdown的编辑器，他们的图片路径引用方式不统一，这就导致了我想在本地直接看md文件，但是发布到hexo中有需要手动改变图片引用路径。
经过一番探索，完美解决
# 设置typora 
偏好设置 --> 图像 --> 插入图片时..
选择复制到指定路径 选择./${filename}
# 设置hexo
1. 添加库：npm install --save-dev hexo-typora-image
npm 官网 https://www.npmjs.com/package/hexo-typora-image?activeTab=readme
2. 设置post.md的 front matter模板
<...>
typora-copy-images-to: {{ title }}
3. 设置_config.yml 
post_asset_folder: true
4. 解决首页不加载图片的问题
marked:
  prependRoot: true
  postAsset: true
5. 控制首页想显示什么（基于next）
https://theme-next.js.org/docs/theme-settings/posts
方法一:在想在首页显示的内容后面添加`<!-- more --> `
方法二：使用description ,但是没办法使用图片