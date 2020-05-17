## 1. 添加 `--exec babel-node` 至 scripts 启动命令
ps:注意需要中dev 与 start 中同时添加

```json
{
  "name": "nuxt-learn",
  "version": "1.0.0",
  "description": "My lovely Nuxt.js project",
  "author": "wqzhai",
  "private": true,
  "scripts": {
    "dev": "cross-env NODE_ENV=development nodemon server/index.js --watch server --exec babel-node",
    "build": "nuxt build",
    "start": "cross-env NODE_ENV=production node server/index.js --exec babel-node",
    "generate": "nuxt generate"
  },
  "dependencies": {
    "@nuxtjs/axios": "^5.0.0",
    "babel-cli": "^6.26.0",
    "babel-core": "^6.26.3",
    "babel-preset-es2015": "^6.24.1",
    "babel-preset-stage-0": "^6.24.1",
    "cross-env": "^5.2.0",
    "element-ui": "^2.4.6",
    "koa": "^2.5.2",
    "nuxt": "^2.0.0"
  },
  "devDependencies": {
    "nodemon": "^1.11.0"
  }
}
```

## 2. npm安装依赖
```shell
	npm i babel-cli babel-core babel preset-es2015
```
## 3.在根路径创建.babelrc文件，写入配置

```shell
 touch .babelrc
```
 3.2
```
	{
		"presets": ['es2015']
	}
```

## 4.重新启动项目

```shell
	npm run dev  |  npm run build | npm start
```
 > 即可愉快的使用esm语法了.


