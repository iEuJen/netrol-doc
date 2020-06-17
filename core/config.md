# Config

对 http 请求一些属性进行自定义配置，可配置属性包括：

- baseUrl `string` 将自动加在 apis\[apiname\].url 前面的
- headers `object` 请求头
- timeout `number` 指定请求超时的毫秒数，默认为0，不设定超时
- defaultMethod `string` 当 apis\[apiname\] 为 string 时，或者 apis\[apiname\].method 不存在时，使用该参数作为 Request Method。

### 说明

config 即可以作为 `Netrol.create` 方法的 options 配置选项，也可以作为 [Module](./module.md) 的配置选项。

对应 module 如果没有配置此选项，则默认调用 `Netrol.create` 方法中配置。

当然，config 是一个可选项，如果你不做任何定制，将使用 Netrol 的一些默认配置。

### 使用范例

```javascript
// netrol/index.js
import Netrol from 'netrol'

export default Netrol.create({
  config: {
    baseUrl: 'http://www.ydn.com',
    // 请求头
    headers: {
      token: 'yourtoken'
    },
    timeout: 5000, // 5000 毫秒后取消请求
    defaultMethod: 'post', // 默认请求 post
  },
  // ...其他配置
})
```