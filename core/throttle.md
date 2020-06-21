# Throttle

netrol 内置节流机制，相同 apiname 的接口在同一时间内无法多次触发，多次触发将 reject 一个 ErrorType.THROTTLE 的错误

报错具体详情，可查看 [ErrorType](./errorType.md) 一节。

这个机制在实际应用中不知道效果如何，如果这一机制在实际运作中不理想，可能会有所改变。