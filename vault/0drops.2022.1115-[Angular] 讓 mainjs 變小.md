---
id: 3nppj8b00bsdzmbhem8ppe9
title: '1115-[Angular] 讓 mainjs 變小'
desc: ''
updated: 1668650675126
created: 1668496095203
tags:
  - PROG.Angular
---

## 讓 main.js 變小

1. 將 main.js 內的元件抽出去變成 lazyload 的。
2. 使用 esm 讓 angular 幫忙 tree-shake，最終只會包含你有使用的部分。

## 視覺化工具

主要是參考這篇文章:

[How To Analyze Angular App Bundle Sizes with webpack Bundle Analyzer or source-map-explorer by Alligator.io](https://www.digitalocean.com/community/tutorials/angular-bundle-size)