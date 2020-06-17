# TimeoutHander

对超时的请求进行处理的函数。需要设置 [options.config.timeout](./config.md) 不为0。

### 使用范例

```javascript
import { timeoutHander } from 'netrol'
timeoutHander((info) => {
  console.log(info)
})
```

timeoutHander 的回调函数接收一个 info 详情对象作为参数。其具体属性如下：

- apiName `string` apis 定义的接口名称
- data `any` 传递给后端的数据
- method `string` http 请求方法
- timeout `number` 超时时间
- url `string` http 请求的 url

超时的请求将 reject 一个 ErrorType.TIMEOUT 的错误。
报错具体详情，可查看 [ErrorType](./errorType.md) 一节。