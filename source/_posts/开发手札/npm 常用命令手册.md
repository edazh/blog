---
title: npm 常用命令手册
date: 2023-12-24 23:59
tags: ['前端', 'mpm']
categories: 开发手札
---

## 常用命令

### npm view

- 功能：查询 npm 包的信息
- 别名：`info`,` show`, `v`

#### 使用方式

```bash
npm view [<package-spec>] [<field>[.subfield]...]

npm view @dcloudio/uni-app dist-tags
```

<!-- more -->

#### 例子

查看 vue 包信息

```bash
# 如果未指定版本，则默认为 "latest"。
npm view vue
```

查看 vue 包依赖 `dependencies`

```bash
npm view vue dependencies
```

可以指定多个字段，并且将一个接一个地打印。还可以指定输出格式为 json，方便程序读取。

```bash
# 查看最新发布的 tags，并以 json 格式输出
npm view vue dist-tags --json

# 查看所有字段，并以 json 格式输出
npm view vue --json

# 查看子级字段 latest.version，方便命令行程序读取
npm view vue dist-tags.latest
```
