## 错误机制

1. 没有异常机制

2. error类型实现了error接口

```go
type error interface {
	Error() string
}
```

3. 可以通过errors.New快速创建错误实例

```go
errors.New("err msg:")
```

## 最佳实践

1. 定义不同的错误变量，以便于判断错误类型

```go
var LessThanTwoError = errors.New("n must be greater than 2")
var GreaterThanThunderError = errors.New("n must be less than 100")
...

func Compare(n int) ([]int, error) {
	if n < 2 {
		return nil,	LessThanTwoError
	}
	if n > 100 {
		return nil, GreaterThanThunderError
	}
}
```

> 避免在代码里写字符串，调用者不方便根据字符串匹配来判断错误类型

2. 及早失败，避免嵌套

## panic

1. 用于不可恢复的错误
2. 退出前会执行defer指定的内容

## os.Exit

1. os.Exit退出时不会执行defer指定的函数
2. os.Exit退出时不输出当前调用栈信息

## recover

panic退出前会执行derfer，在defer里执行recover

recover返回panic传进去的错误，可以针对错误做一些恢复

```go
defer func() {
	if err := recover(); err != nil {
		// 恢复错误
		log.Error("recovered panic", err)
	}
}
```
