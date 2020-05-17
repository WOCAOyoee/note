#### 安装axios依赖

```shell
$	npm i axios --save
```
> 在项目根目录下新建 ($ mkdir network) 文件夹,再在network里新建 ($ touch http.js) 文件

```shell
	$ mkdir network

	$ cd network

	$ touch http.js

	$ vi http.js

	>>>
```

`http.js`

```js
import axios from 'axios';

export function request(config){
	return new Promise((resolve,reject) => {
		const instance = axios.create({
		baseURL: 'http://yoees.com/api',
		timeout: 8000
		})
		instance(config)
		.then(res => {
			resolve(res)
		})
		.catch(err => {
			reject(err)
		})
	})
}
//	↓↓↓↓↓↓↓↓↓↓
//	甚至直接return res数据
export function request(config){
	const instance = axios.create({
		baceURL: 'http://yoees.com/apis',
		timeout: 5000
	})
	return instance(config)
}
```

> vue单文件组件中使用:

`.vue`

```vue
import request from './network/http.js'

```

