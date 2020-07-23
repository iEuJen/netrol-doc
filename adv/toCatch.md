# ToCatch

> toCatch(code: number, exec: Function)

对 http 状态码进行捕获处理的函数。

如果你需要根据后端返回的状态码，在前端进行某些操作，那么你可以考虑导入 toCath 函数

### 使用范例

```javascript
import { toCatch } from 'netrol'

toCatch(404, () => {
  // 当 http 状态码为 404 的时候，进行一些操作
})
```

被 toCatch 捕获的请求，将 reject 一个 ErrorType.STOP 的错误。如果状态码不在 200 到 300 之间，且没有定义 toCatch，则会 reject 一个 ErrorType.STATUS 的错误。

报错具体详情，可查看 [ErrorType](./errorType.md) 一节。