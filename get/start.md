# 开始

当你使用 netrol-cli 创建项目之后，你可以在你项目中找到一个名为 netrol 的目录

### 目录结构

> apis.js

> index.js

> leach.js

### 演示

netrol-cli 会根据实际需要，将项目各个功能模块分文件存放，我们将这些功能模块进行汇总，做一个简单的实例，如下：

```javascript
// @/netrol/index.js
import Netrol from 'netrol'
export default Netrol.create({
  config: {
    baseUrl: 'http://yourwebsite.com'
  },
  apis: {
    apiname: {
      url: '/demo'
      method: 'post'
    } 
  },
  leach: {
    apiname (res) {
      return res
    }
  },
})
```

执行 Netrol.create 将创建一个 Netrol 实例，并返回一个请求函数（后面文档中出现的 request 函数指的就是这个）。

<font color="#dd0000">注意：</font>Netrol.create 在项目中只会创建一个实例，因此重复调用 Netrol.create 只有第一次调用时传递的 options 配置是有效的

在需要调用请求的地方导入 @/netrol/index.js

```javascript
// 导入请求函数
import request from '@/netrol/index.js'
// 调用对象api发起请求
request('apiname', { 
  data: '传递给后端的数据' 
})
.then(res => {
  // 响应的数据
  console.log(res)
})
```

从上面的例子中，我们可以了解到，要使用 Netrol 进行网络请求，需要调用 create 方法，并传递一个 options 对象作为配置选项。
其中包含config，apis，leach 以及其他属性。而它们中只有 apis 是必须的，其用于管理项目中所有接口的url。

下面列出 options 对象的所有属性：

### options

- [apis](../core/apis.md) `object`

  接口管理对象

- [leach](../core/leach.md) `object`

  接口响应数据过滤器

- [config](../core/config.md) `object`

  请求配置的自定义

- [module](../core/module.md) `object`

  接口模块分割

- [transformData](../core/transformData.md) `Function`

  请求数据转换函数