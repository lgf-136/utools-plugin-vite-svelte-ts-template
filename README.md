# Svelte + TS + Vite

This template should help get you started developing with Svelte and TypeScript in Vite.

## Recommended IDE Setup

[VS Code](https://code.visualstudio.com/) + [Svelte](https://marketplace.visualstudio.com/items?itemName=svelte.svelte-vscode).

## Need an official Svelte framework?

Check out [SvelteKit](https://github.com/sveltejs/kit#readme), which is also powered by Vite. Deploy anywhere with its serverless-first approach and adapt to various platforms, with out of the box support for TypeScript, SCSS, and Less, and easily-added support for mdsvex, GraphQL, PostCSS, Tailwind CSS, and more.

## Technical considerations

**Why use this over SvelteKit?**

- It brings its own routing solution which might not be preferable for some users.
- It is first and foremost a framework that just happens to use Vite under the hood, not a Vite app.
  `vite dev` and `vite build` wouldn't work in a SvelteKit environment, for example.

This template contains as little as possible to get started with Vite + TypeScript + Svelte, while taking into account the developer experience with regards to HMR and intellisense. It demonstrates capabilities on par with the other `create-vite` templates and is a good starting point for beginners dipping their toes into a Vite + Svelte project.

Should you later need the extended capabilities and extensibility provided by SvelteKit, the template has been structured similarly to SvelteKit so that it is easy to migrate.

**Why `global.d.ts` instead of `compilerOptions.types` inside `jsconfig.json` or `tsconfig.json`?**

Setting `compilerOptions.types` shuts out all other types not explicitly listed in the configuration. Using triple-slash references keeps the default TypeScript setting of accepting type information from the entire workspace, while also adding `svelte` and `vite/client` type information.

**Why include `.vscode/extensions.json`?**

Other templates indirectly recommend extensions via the README, but this file allows VS Code to prompt the user to install the recommended extension upon opening the project.

**Why enable `allowJs` in the TS template?**

While `allowJs: false` would indeed prevent the use of `.js` files in the project, it does not prevent the use of JavaScript syntax in `.svelte` files. In addition, it would force `checkJs: false`, bringing the worst of both worlds: not being able to guarantee the entire codebase is TypeScript, and also having worse typechecking for the existing JavaScript. In addition, there are valid use cases in which a mixed codebase may be relevant.

**Why is HMR not preserving my local component state?**

HMR state preservation comes with a number of gotchas! It has been disabled by default in both `svelte-hmr` and `@sveltejs/vite-plugin-svelte` due to its often surprising behavior. You can read the details [here](https://github.com/rixo/svelte-hmr#svelte-hmr).

If you have state that's important to retain within a component, consider creating an external store which would not be replaced by HMR.

```ts
// store.ts
// An extremely simple external store
import { writable } from 'svelte/store'
export default writable(0)
```

[Vite 世界指南（带你从 0 到 1 深入学习 vite）](https://www.bilibili.com/video/BV1GN4y1M7P5?p=7&spm_id_from=pageDriver&vd_source=6cecd1f17a6c0ef08a944dd92199a516)

https://blog.csdn.net/mouday/article/details/126336560
https://www.bilibili.com/video/BV1Pd4y1S7Mp/?spm_id_from=333.788.recommend_more_video.2&vd_source=6cecd1f17a6c0ef08a944dd92199a516

npm i -D postcss postcss-cli postcss.parts browserslist autoprefixer postcss-preset-env stylelint stylelint-config-standard stylelint-config-prettier postcss-pxtorem

npm i -D postcss postcss-cli browserslist autoprefixer postcss-preset-env stylelint stylelint-config-standard stylelint-config-prettier postcss-pxtorem less sass mockjs vite-plugin-html vite-plugin-mock vite-plugin-utools

npm i -D postcss postcss-cli browserslist autoprefixer postcss-preset-env stylelint stylelint-config-standard stylelint-config-prettier postcss-pxtorem less sass mockjs vite-plugin-html vite-plugin-mock vite-plugin-utools @types/node utools-api-types

npx postcss main.css -o dist.css
npx postcss main.css -o dist.css -u autoprefixer
npx postcss main.css -o dist.css -u autoprefixer --no-map

https://github.com/uTools-Labs/utools-api-types

uTools API 代码提示
第一步

npm install utools-api-types --save-dev
第二步 配置 tsconfig.json

{
"compilerOptions": {
"types": [
"utools-api-types"
]
}
}
API 代码示例
// 默认浏览器打开网页
window.utools.shellOpenExternal('https://u.tools')

// 在资源管理器中显示文件
window.utools.shellShowItemInFolder('d:\\test')

// ubrowser 网页自动化
window.utools.ubrowser.goto('https://cn.bing.com')
.value('#sb_form_q', 'uTools')
.click('#sb_form_go')
.run({ width: 1000, height: 600 })

// 获取当前浏览器 URL
window.utools.getCurrentBrowserUrl()

// 值键对方式存储数据
window.utools.dbStorage.setItem('key', 'value')

// 执行截图
window.utools.screenCapture((imagebase64) => {
// 截图完的回调
})

// 执行取色
window.utools.screenColorPick(({ hex, rgb }) => {
// 取色完的回调
})
