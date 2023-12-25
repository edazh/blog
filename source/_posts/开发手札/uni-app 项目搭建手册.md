---
title: uni-app 项目搭建手册
date: 2023-12-25 00:00
tags: ['前端', 'uni-app']
categories: 开发手札
---

## 使用 vue-cli 创建 uni-app

### 全局安装 vue-cli

```bash
npm install -g @vue/cli
```

### 使用正式版（对应 HBuilderX 最新正式版）

```bash
vue create -p dcloudio/uni-preset-vue my-project
```

### 使用 alpha 版（对应 HBuilderX 最新 alpha 版）

```bash
vue create -p dcloudio/uni-preset-vue#alpha my-alpha-project
```

## 使用 degit 创建 uni-app

### javascript 模板

创建以 javascript 开发的工程（如命令行创建失败，请直接访问  [gitee](https://gitee.com/dcloud/uni-preset-vue/repository/archive/vite.zip)  下载模板）

```bash
npx degit dcloudio/uni-preset-vue#vite my-vue3-project
```

```bash
npx degit dcloudio/uni-preset-vue#vite-alpha my-vue3-project
```

#### typescript 模板

创建以 typescript 开发的工程（如命令行创建失败，请直接访问  [gitee](https://gitee.com/dcloud/uni-preset-vue/repository/archive/vite-ts.zip)  下载模板）。

```bash
npx degit dcloudio/uni-preset-vue#vite-ts my-vue3-project
```

<!-- more -->

## 其他方式创建 uni-app

由于 `degit` 不支持 `gitee` 下载代码（猜测主要是 `gitee` 的人机验证策略阻止了匿名下载），所以需要通过其他方式下载 `gitee` 的 `uni-app` 模板代码。

### gitee 上 uni-app 可用的模板

| 模板名称/分支 | 备注                               | 仓库链接                                                               |
| ------------- | ---------------------------------- | ---------------------------------------------------------------------- |
| vite          | vite + vue3 + uni-app              | [vite](https://gitee.com/dcloud/uni-preset-vue/tree/vite/)             |
| vite-alpha    | vite + vue3 + uni-app alpha        | [vite-alpha](https://gitee.com/dcloud/uni-preset-vue/tree/vite-alpha/) |
| vite-ts       | vite + vue3 + uni-app + typescript | [vite-ts](https://gitee.com/dcloud/uni-preset-vue/tree/vite-ts/)       |

### 使用 git 下载模板代码包

```bash
git clone https://gitee.com/dcloud/uni-preset-vue.git --depth 1 -b [branch] [my-project-name]
```

例子：行云流水的一套操作

- 克隆 `vite-ts` 模板并指定参数 `depth 1` 以加快速度
- 将项目文件夹命名为`my-project`
- 然后删除项目内的 `.git`文件夹以销毁原仓库
- 创建自己的 Git 仓库，指定初始分支名为 `master`（新版 Git 建议使用 `main` 来命名主分支）
- 创建初始提交，提交信息为 `init`
- 使用 `vscode` 打开项目文件夹

```bash
git clone https://gitee.com/dcloud/uni-preset-vue.git \
 --depth 1 \
 -b vite-ts \
 my-project && \
 cd my-project && \
 rm -rf .git && \
 git init -b master && \
 git add -A && \
 git commit -m init && \
 code .
```

### 前往 gitee 网站下载指定分支的代码包

[uni-preset-vue: uni-app preset for vue - Gitee.com](https://gitee.com/dcloud/uni-preset-vue/tree/vite/)

## 更新依赖到指定版本

可以使用  [@dcloudio/uvm](https://www.npmjs.com/package/@dcloudio/uvm)  管理编译器的版本，此工具仅自动增加或更新 uni-app 编译器主要依赖，对于新增的编译命令（scripts）暂时不会自动处理，需手动参考新工程进行配置。

### 更新到最新正式版

```bash
npx @dcloudio/uvm@latest
```

### 更新到最新 Alpha 版

```bash
npx @dcloudio/uvm@latest alpha
```

### 更新到指定版本

#### 查看 uni-app tags

```bash
npm view @dcloudio/uni-app dist-tags
```

#### 更新到指定 tag 版本

例如 `vue3`，该版本是 `uni-app` 最新发布的 `tag: vue3` 的 `alpha` 版本。

```bash
npx @dcloudio/uvm@latest vue3
```

## 自定义模板

选择自定义模板时，需要填写 uni-app 模板地址，这个地址其实就是托管在云端的仓库地址。以 GitHub 为例，地址格式为  `userName/repositoryName`，如  `dcloudio/uni-template-picture`  就是下载图片模板。

更多支持的下载方式，请参考这个插件的说明：[download-git-repo](https://www.npmjs.com/package/download-git-repo)

### 国内特殊情况

模板项目存放于 Github，由于国内网络环境问题，可能下载失败。针对此问题可以尝试如下措施：

- 更换网络重试，比如使用 4g 网络
- 在设备或路由器的网络设置中增加 DNS（如：8.8.8.8）
- 在设备中增加固定的 hosts（如：140.82.113.4 github.com）

## 注意

- Vue3/Vite 版要求 node 版本`^14.18.0 || >=16.0.0`
- 如果使用 HBuilderX（3.6.7 以下版本）运行 Vue3/Vite 创建的最新的 cli 工程，需要在 HBuilderX 运行配置最底部设置 node 路径 为自己本机高版本 node 路径（注意需要重启 HBuilderX 才可以生效）
  - HBuilderX Mac 版本菜单栏左上角 HBuilderX->偏好设置->运行配置->node 路径
  - HBuilderX Windows 版本菜单栏 工具->设置->运行配置->node 路径
