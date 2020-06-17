# Apis

### 接口管理对象

Netrol采用集中式管理的方式，将后端接口存放到 apis 对象中，并将其作为 options 的属性，传递给 create 方法。
后续请求函数便通过 apis\[apiname\] 调用对应的接口。

```javascript
// @/netrol/apis.js
export default {
  apiname: {
    method: 'post',
    url: '/apiurl'
  },
  apiname2: '/apiurl2'
}
```

在项目中调用

```javascript
// 从 netrol/index 中引入请求函数
// 这里假设你的项目是通过 netrol-cli 创建的
// 并且 @ 别名为 src 目录（使用vue-cli开发过项目的朋友应该很熟悉）
import request from '@/netrol/index'
// 在项目中调用
request('apiname'，{ id: 1 })
.then(res => {})

request('apiname2')
.then(res => {})
```

从示例代码中我们知道，apis\[apiname\] 既可以是一个对象，也可以是一个字符串。

当 apis\[apiname\] 为一个对象时，netrol 将就 apis\[apiname\].url 发起一个 apis\[apiname\].method 的 http 请求。

当 apis\[apiname\] 为一个字符串时，这个字符串必须是一个接口 url。那么 netrol 将使用 [config](config.md) 中的 defaultMethod（默认为 get ） 作为 http 请求的 Request Method，发起一个 http 请求。

### apis[apiname].headers

apis\[apiname\] 除了可以设置 method 和 url 之外，还可以设置 headers 作为 http 请求的请求头。

```javascript
// @/netrol/apis.js
export default {
  apiname: {
    method: 'post',
    url: '/apiurl',
    headers: {
      'token': 'teshudeqingqiutou'
    }
  },
}
```

### 使用范例

```javascript
// netrol/apis.js
export default {
  apiname: {
    method: 'post',
    url: '/apiurl',
  },
}

// netrol/index.js
import Netrol from 'netrol'
import apis from './apis.js'

export default Netrol.create({
  apis,
  // ...其他配置
})
```