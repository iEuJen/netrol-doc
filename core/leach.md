# Leach

### 接口响应数据过滤器

> leach\[apiname\](response: object): any

你可以把 leach 理解为一个响应拦截器。它的确也是做了和[响应拦截器](./interceptor.md)相同的事情。
不同的是，响应拦截器会对每一个接口进行拦截，而 leach 只针对特定 api 对象进行拦截。
使用方式和 apis 相似，不同的是 apis\[apiname\] 是一个对象或者字符串，而 leach\[apiname\] 是一个方法。

```javascript
// netrol/leach
export default {
  apiname (response) {
    // 将响应数据上的 body（后端返回的数据）返回
    return response.body
  }
}
```

#### response 对象

response 对象是 leach 上定义的方法所接收的一个回调参数，对象属性包括：

- body

  后端接口返回的数据

- status

  http 状态码

- statusText

  http 响应状态对应的文本信息

- xhr

  XMLHttpRequest 实例对象


leach 定义的方法是 Netrol promise 链执行的最后一个阶段。
也就是说，在 leach\[apiname\] 方法里面返回的值，将作为调用 request 请求函数 promise resolve 的结果。

### 使用范例

```javascript
// netrol/leach.js
export default {
  apiname (res) {
    // 执行一些操作
    return // ... 返回结果
  }
}

// netrol/index.js
import Netrol from 'netrol'
import leach from './leach.js'

export default Netrol.create({
  leach,
  // ...其他配置
})
```