---
title: pinia 的安装与使用
date: 2023-12-24 23:59
tags: ['前端', 'pinia']
categories: 开发手札
---

## 安装

用你喜欢的包管理器安装  `pinia`：

```bash
yarn add pinia
# 或者使用 npm
npm install pinia
```

<!-- more -->

## defineStore

```js
import { defineStore } from 'pinia'

// 你可以对 `defineStore()` 的返回值进行任意命名，但最好使用 store 的名字，同时以 `use` 开头且以 `Store` 结尾。(比如 `useUserStore`，`useCartStore`，`useProductStore`)
// 第一个参数是你的应用中 Store 的唯一 ID。
export const useAlertsStore = defineStore('alerts', {
  // 其他配置...
})
```

## 在 uni-app 中使用 pinia

在  `main.js`  中编写以下代码：

```js
import { createSSRApp } from 'vue'
import * as Pinia from 'pinia'

export function createApp() {
  const app = createSSRApp(App)
  app.use(Pinia.createPinia())
  return {
    app,
    Pinia, // 此处必须将 Pinia 返回
  }
}
```

## 参考

- [Pinia | 官方文档](https://pinia.vuejs.org/zh/getting-started.html)
- [状态管理 Pinia | uni-app 官网](https://uniapp.dcloud.net.cn/tutorial/vue3-pinia.html#%E5%9F%BA%E6%9C%AC%E7%A4%BA%E4%BE%8B)
