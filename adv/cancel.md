# Cancel

> cancel(name: string): boolean

netrol 支持取消特定 api 的请求。只需要在调用 cancel 函数的时候，传递对应的 apiname。

### 使用范例

```javascript
import { cancel } from 'netrol'
cancel('apiname')
cancel('moduleA.apiname')
```

执行 cancel 函数将返回一个 boolean 值。true 表示取消成功。false 则可能请求已经完成，或者 apiname 不存在。

被取消的请求，将 reject 一个 ErrorType.CANCELED 的错误。

报错具体详情，可查看 [ErrorType](./errorType.md) 一节。