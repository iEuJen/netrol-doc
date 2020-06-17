# Module

由于对 api 使用了集中式管理，这样会导致 apis 和 leach 会集中到一个比较大的对象。
当 api 非常多的时候，apis 和 leach 对象可能会变得非常臃肿。

于是，Netrol 提供模块功能的支持。这样我们就可以对接口根据需要分割成多个模块：

### 使用范例

module 上 [apis](./apis.md)，[leach](./leach.md)，[config](./config.md)，[transformData](./transformData.md) 的使用同 Netrol.create 完全一致

##### 模块 moduleA

```javascript
// netrol/module/moduleA.js
export default {
  apis: { ... },
  leach: { ... },
  config: { ... },
  transformData (data) { ... }
}
```

##### 模块 moduleB

```javascript
// netrol/module/moduleB.js
export default {
  apis: { ... },
  leach: { ... },
  config: { ... },
  transformData (data) { ... }
}
```

#### Netrol.create

```javascript
// netrol/index.js
import Netrol from 'netrol'
import moduleA from './module/moduleA.js'
import moduleB from './module/moduleB.js'

export default Netrol.create({
  //...其他配置
  module: {
    moduleA,
    moduleB
  },
})
```

#### 调用 request

```javascript
// 你的项目
import request from '@/netrol/index.js'
request('moduleA.apiname') // 调用模块 moduleA 的接口
request('moduleB.apiname', {}) // 调用模块 moduleB 的接口
```