# TransformData

Netrol 默认使用 JSON 字符串与后端进行交互。
但如果你的后端要求使用其他数据类型，一般是 FormData。
那么你就可以考虑使用 transformData 这一配置项了。

### 说明

transformData 是 Netrol.create 配置选项上的一个方法，其接收一个来自 request 函数的参数。
你需要在方法内对数据进行定制处理，并返回。返回的数据将作为请求数据传递给后端。

##### 在模块中使用
如果 [module](./module.md) 上也定义了此方法，那么将优先调用 module 上定义的方法。
如果 module 没有定义此方法，则调用 Netrol.create 上定义的方法。

### 使用范例

```javascript
// netrol/index.js
import Netrol from 'netrol'

export default Netrol.create({
  transformData (data) {
    console.log(data) // { msg: '测试数据' }
    // ... 对 data 进行处理
    return data
  }
})

// 在你的项目中
import request from '@/netrol/index.js'
request('apiname', { 
  msg: '测试数据' 
})
```