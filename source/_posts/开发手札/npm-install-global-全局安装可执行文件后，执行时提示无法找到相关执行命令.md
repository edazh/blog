---
title: npm install --global xxx 全局安装可执行文件后，执行时提示无法找到相关执行命令
date: 2023-12-26 00:27:14
tags: ['前端', 'mpm']
categories: 开发手札
---

一般情况下是因为 nodejs 的全局可执行文件夹未配置在 PATH 中，其中一种方式为编辑 ~/.bash_prodile 文件，添加到 PATH 中即可：

```bash
# 查看 nodejs 全局可执行文件目录
npm bin -g
# output: /usr/local/lib/node/bin

# 编辑 ~/.bash_profile
vi ~/.bash_profile

#将 nodejs 全局可执行文件目录添加到 PATH 中
# 添加前
PATH=$PATH:$HOME/.local/bin:$HOME/bin

# 添加后
PATH=$PATH:$HOME/.local/bin:$HOME/bin:/usr/local/lib/node/bin

# 使配置生效
source ~/.bash_profile
```
