# ErrorType

netrol 对执行过程的错误，进行了分类设计，让我们在使用的情况中可以更好地处理 reject 的错误。

### error.ErrorType

ErrorType 主要的类型如下：

- STOP 为 0，promise链终止(为了不执行 then 方法中或者 await 后的程序)
- FAIL 为 1，一般错误
- THROTTLE 为 2，触发节流
- STATUS 为 3，服务器状态码错误
- TIMEOUT 为 4，超时错误
- CANCELED 为 5，请求被取消

### error.toJSON

将 error 转为一个 json 对象的方法

### 使用范例

```javascript
async function demo () {
  try {
    let res = await request('apiname')
  } catch (err) {
    console.log(err.type) // number
    console.log(err.ErrorType)
    // {
    //   STOP: 0,
    //   FAIL: 1,
    //   THROTTLE: 2,
    //   STATUS: 3,
    //   TIMEOUT: 4,
    //   CANCELED: 5
    // }
    console.log(err.toJSON()) // object
  }
}

request('apiname')
.then(res)
.catch(err => {
  console.log(err.toJSON())
})
```