---
colorSchema: 'dark'
highlighter: shiki
fonts:
  mono: Input Mono
---

# 前端升级的论述

下面所提出的观点都是个人的一些拙见，如有不妥及时提出。

<div class="abs-tr !mx-5 !my-8 flex flex-col">
 公司内部使用
</div>

<div class="abs-bl !mx-14 my-12 flex flex-col">
  <div class="mb-3 uppercase tracking-widest font-500">
  Elone Hoo
  </div>
  <div class="text-md opacity-50">Hangzhou, China 2022</div>
</div>

<style>
p {
  @apply text-xl;
}
</style>

---
layout: center
class: text-center
---

# 包管理工具 pnpm

对单个源码仓库中包含多个软件包的支持
---

# 什么是 pnpm ？
速度快、节省磁盘空间的软件包管理器

<div class="grid grid-cols-2 gap-x-4">

```markdown
# npm or yarn

- 磁盘管理的冗余问题
- 下载依赖不注重 hash ，导致速度过慢
- 不支持 monorepo
```

```markdown
# pnpm

- 基于内容寻址而产生的高效的磁盘管理
- 下载依赖以 hash 为主，速度快
- 天生支持 monorepo
```

</div>

---

# 迁移难度
无缝迁移，难度系数 🌟

1. 新建一个 <code>.npmrc</code> 文件
2. 删除 `node_modules` 文件夹
3. 运行 `pnpm install`

---
layout: center
class: text-center
---

# 易于拆分的 monorepo
目前后端的代码形式的前端实现

---

# 什么是 monorepo
粗浅的介绍一下

monorepo 可以理解为我们目前的后端的架构，我们在写 [maven 依赖](https://search.maven.org/) 这些依赖都是根据每一个项目去单独定制的，并不是同意的，我们需要针对每一个逻辑去进行修改和开发。

monorepo 也是如此，我们还可以对于我们所封装的组件直接进行发布到 npm 仓库去进行统一的管理。在日后我们可以将很多东西拆分变成单独且唯一的组件去进行管理，这样我们就不用每一次新的项目，是将老的项目复制粘贴，而是去下载所需要的依赖。

monorepo 的好处是我们可以对于每一个仓库去提供唯一的文档，在发布包的时候我们可以将文档一同部署，减少了团队之间对于组件使用的沟通成本。

---
layout: center
class: text-center
---

# 快如闪电的 Vite
现代前端工具链，为开发提供极速响应

---

# 什么是 Vite
粗浅的介绍一下

- 类似 vue-cli 的熟悉体验

- 基于原生 ESM 的极速热更新

- 基于 esbuild 的依赖预打包

- 兼容 Rollup 的插件机制

- 内置 SSR 支持

---

# 为什么选 Vite
简单的阐述一下 webpack 和 vite

现在的前端已经完全支持了 ESM 的方式，所以 webpack 将会慢慢的退出历史的舞台，因为 webpack 是庞大的，是缓慢的，是衰老的。

而 Vite 是一个快的，年轻的，轻便的前端构建工具，并且 Vite 生态的迁移战争已经结束了，我们有了 [d.ts](https://github.com/elonehoo/vite-plugin-type-ts) ｜ [dist css](https://github.com/elonehoo/vite-plugin-dist-css) ... 这些开箱即用的插件，方便我们的开发。

同时 Vue2.7 和 Vue3.0 天然支持 Vite。

---
layout: center
class: text-center
---

# Vue2.7 Or Vue3.2
这是一个选择题，这两个版本没有太大的差异，只有开发效率和开发速度的差异

---
layout: center
class: text-center
---

# 更多单文件组件编译阶段的优化
新增的新功能

 [`<script setup>`](https://cn.vuejs.org/guide/extras/composition-api-faq.html) 

[`<style>` 动态变量注入](https://cn.vuejs.org/api/sfc-css-features.html#v-bind-in-css)

---

# 什么是 组件式 API ？ 
在 Vue 2.7/3 中引入的一种新的编写 Vue 组件的方式。

<div class="grid grid-cols-2 gap-x-4">

```html
<script>
export default {
  data() {
    return {
      dark: false
    }
  },
  computed: {
    light() {
      return !this.dark
    }
  },
  methods: {
    toggleDark() {
      this.dark = !this.dark
    }
  }
}
</script>
```

```html
<script setup>
import { ref, computed } from 'vue'
const dark = ref(false)
const light = computed(() => !dark.value)
</script>
```

</div>

---
clicks: 6
---

# 为什么引入组合式 API ？

<div class="grid grid-cols-2 gap-x-4 gap-y-4">

###### 对象式 API 存在的问题

###### 组合式 API 提供的能力

<v-clicks at="1">

- 不利于复用
- 潜在命名冲突
- 上下文丢失
- 有限的类型支持
- 按 API 类型组织

</v-clicks>

<v-clicks at="1">

- 极易复用 (原生 JS 函数)
- 可灵活组合 (生命周期钩子可多次使用)
- 提供更好的上下文支持
- 更好的 TypeScript 类型支持
- 按功能/逻辑组织
- 可独立于 Vue 组件使用

</v-clicks>

</div>

---
layout: center
class: text-center
---

# Thank you!
可以在我的网站 [elonehoo.xyz](https://elonehoo.xyz/) 中了解
