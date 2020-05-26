## vue-cli3 安装创建项目以及目录结构

###### **安装脚手架cli3.0**

全局安装:

```shell 
$ npm install -g @vue/cli 
  or
$ yarn global add @vue/cli
```

查看版本/是否安装成功 vue -V



##### **创建项目**

在想要的件夹下面创建项目 

```shell
$ vue create my-project
```

项目配置选项

```shell
TypeScript 支持使用 TypeScript 书写源码
Progressive Web App (PWA) Support PWA 支持。
Router 支持 vue-router 。
Vuex 支持 vuex 。
CSS Pre-processors 支持 CSS 预处理器。
Linter / Formatter 支持代码风格检查和格式化。
Unit Testing 支持单元测试。
E2E Testing 支持 E2E 测试。

```



##### 启动

1. cd my-project // 进入到项目根目录

2. npm run serve // 启动项目



#### **目录结构**

```js
module.exports = {
    // 部署应用时的基本 URL
    baseUrl: process.env.NODE_ENV === 'production' ? '192.168.60.110:8080' : '192.168.60.110:8080',
 
    // build时构建文件的目录 构建时传入 --no-clean 可关闭该行为
    outputDir: 'dist',
 
    // build时放置生成的静态资源 (js、css、img、fonts) 的 (相对于 outputDir 的) 目录
    assetsDir: '',
 
    // 指定生成的 index.html 的输出路径 (相对于 outputDir)。也可以是一个绝对路径。
    indexPath: 'index.html',
 
    // 默认在生成的静态资源文件名中包含hash以控制缓存
    filenameHashing: true,
 
    // 构建多页面应用，页面的配置
    pages: {
        index: {
            // page 的入口
            entry: 'src/index/main.js',
            // 模板来源
            template: 'public/index.html',
            // 在 dist/index.html 的输出
            filename: 'index.html',
            // 当使用 title 选项时，
            // template 中的 title 标签需要是 <title><%= htmlWebpackPlugin.options.title %></title>
            title: 'Index Page',
            // 在这个页面中包含的块，默认情况下会包含
            // 提取出来的通用 chunk 和 vendor chunk。
            chunks: ['chunk-vendors', 'chunk-common', 'index']
        },
        // 当使用只有入口的字符串格式时，
        // 模板会被推导为 `public/subpage.html`
        // 并且如果找不到的话，就回退到 `public/index.html`。
        // 输出文件名会被推导为 `subpage.html`。
        subpage: 'src/subpage/main.js'
    },
 
    // 是否在开发环境下通过 eslint-loader 在每次保存时 lint 代码 (在生产构建时禁用 eslint-loader)
    lintOnSave: process.env.NODE_ENV !== 'production',
 
    // 是否使用包含运行时编译器的 Vue 构建版本
    runtimeCompiler: false,
 
    // Babel 显式转译列表
    transpileDependencies: [],
 
    // 如果你不需要生产环境的 source map，可以将其设置为 false 以加速生产环境构建
    productionSourceMap: true,
 
    // 设置生成的 HTML 中 <link rel="stylesheet"> 和 <script> 标签的 crossorigin 属性（注：仅影响构建时注入的标签）
    crossorigin: '',
 
    // 在生成的 HTML 中的 <link rel="stylesheet"> 和 <script> 标签上启用 Subresource Integrity (SRI)
    integrity: false,
 
    // 如果这个值是一个对象，则会通过 webpack-merge 合并到最终的配置中
    // 如果你需要基于环境有条件地配置行为，或者想要直接修改配置，那就换成一个函数 (该函数会在环境变量被设置之后懒执行)。该方法的第一个参数会收到已经解析好的配置。在函数内，你可以直接修改配置，或者返回一个将会被合并的对象
    configureWebpack: {},
 
    // 对内部的 webpack 配置（比如修改、增加Loader选项）(链式操作)
    chainWebpack: () =>{
 
    },
 
    // css的处理
    css: {
        // 当为true时，css文件名可省略 module 默认为 false
        modules: true,
        // 是否将组件中的 CSS 提取至一个独立的 CSS 文件中,当作为一个库构建时，你也可以将其设置为 false 免得用户自己导入 CSS
        // 默认生产环境下是 true，开发环境下是 false
        extract: false,
        // 是否为 CSS 开启 source map。设置为 true 之后可能会影响构建的性能
        sourceMap: false,
        //向 CSS 相关的 loader 传递选项(支持 css-loader postcss-loader sass-loader less-loader stylus-loader)
        loaderOptions: {
            css: {},
            less: {}
        }
    },
 
    // 所有 webpack-dev-server 的选项都支持
    devServer: {},
 
    // 是否为 Babel 或 TypeScript 使用 thread-loader
    parallel: require('os').cpus().length > 1,
 
    // 向 PWA 插件传递选项
    pwa: {},
 
    // 可以用来传递任何第三方插件选项
    pluginOptions: {}
}



// devServer && proxy

// Type: string | Object
// 如果你的前端应用和后端 API 服务器没有运行在同一个主机上，你需要在开发环境下将 API 请求代理到 API 服务器。这个问题可以通过 vue.config.js 中的 devServer.proxy 选项来配置。
//devServer.proxy 可以是一个指向开发环境 API 服务器的字符串：

devServer: {
        host: '0.0.0.0',
        port: 9092,
        open: true,
        hotOnly: true, // 热更新
        proxy: {
            '/': { // 本地mock服务器
                target: 'http://localhost:3000',
                changeOrigin: true,
                ws: false
            }
        } // 设置代理
    },

```
