# ProgressListener

用于监听上传/下载进度的对象。

### progressListener.upload 上传监听器

> progressListener.upload(apiName: string, exec: Function)

上传监听器接受两个参数，第一个参数为要监听的 apiName，第二个参数为触发监听的方法。
exec 执行方法接收一个 evt 参数，用于判断监听类型，以及进度状态。

#### 使用范例

```javascript
import { progressListener } from 'netrol'
progressListener.upload('file', (evt) => {
  console.log(evt)
  /**
   * evt 对象
   * {
      type: string,
      event: ProgressEvent,
      status: number,
      statusText: string,
      ProgressStatus: object
      total: number
      loaded: number
   * }
   */
})
```

### progressListener.download 下载监听器

> progressListener.download(apiName: string, exec: Function)

下载监听器使用同上载监听器一样。接受两个参数，第一个参数为要监听的 apiName，第二个参数为触发监听的方法。
exec 执行方法接收一个 event 参数，用于判断监听类型，以及进度状态。

#### 使用范例

```javascript
import { progressListener } from 'netrol'
progressListener.download('file', (evt) => {
  console.log(evt)
  /**
   * evt 对象
   * {
      type: string,
      event: ProgressEvent,
      status: number,
      statusText: string,
      ProgressStatus: object
      total: number
      loaded: number
   * }
   */
})
```

### evt 对象

evt 是上传/下载监听器的回调参数，它包括以下属性

- type `string`, 监听类型，值为 upload/download
- event `ProgressEvent`, ProgressEvent 对象，是 xhr 响应事件的回调参数
- status `number`, 当前进度状态，其值与 ProgressStatus 枚举对象对应
- statusText `string`, 当前进度状态的文字描述
- ProgressStatus `object`, 进度状态的枚举，其包含：
  - FAIL = 0,
  - SUCCESS = 1,
  - PROGRESS = 2,
  - START = 3,
  - CANCEL = 4,
  - TIMEOUT = 5
- total `number`, 当 status === ProgressStatus.PROGRESS 才有的属性，为上传/下载文件的总大小，来自 evt.event.total
- loaded `number`, 当 status === ProgressStatus.PROGRESS 才有的属性，为已经上传/下载文件的大小，来自 evt.event.loaded