# Interceptor

用于设置请求和响应拦截器的对象。

### interceptor.request 设置请求拦截器

> interceptor.request( interceptor: (config: object) => object )

interceptor.request 传入一个函数作为请求拦截器，函数接收一个 config 对象，并可以对其进行一些修改，但最终必须将其返回。

config 的属性详细如下：

- apiName `string` apis 上定义的接口名
- data `any` 经过 transformData 处理的数据
- headers `object` 请求头
- method `string` 请求方法
- timeout `number` 超时时间
- url `string` 接口链接

#### 使用范例

```javascript
// 导入
import { interceptor } from 'netrol'
// 设置
interceptor.request((config) => {
  // 对 config 进行一些操作
  return config
})
```

### interceptor.response 设置响应拦截器

> interceptor.response( interceptor: (res: object) => void | object )

interceptor.response 传入一个函数作为响应拦截器，函数接收一个 res 对象，并可以对其进行一些修改。
返回结果将被 leach 接收到，如果不返回或者返回值为空，则 netrol 会退出 promise 链，并 reject 一次 type 为 'error.ErrorType.STOP'(0) 的 错误。

netrol [对错误返回进行了分类设计](./errorType.md)，因此建议需要对后端数据做判断的操作放在 interceptor.response 中进行。
当结果不想给 request 接受到的时候，可以直接返回一个空值。

res 的属性详细如下：

- body `any` 后端返回的数据
- status `number` http 状态码
- statusText `string` 响应状态对应的文本信息
- xhr `XMLHttpReques` XMLHttpRequest 实例对象

```javascript
// 导入
import { interceptor } from 'netrol'
// 设置
interceptor.response((res) => {
  // 对 res 进行一些操作
  return res
})
```