## 空接口与断言

1. 空接口可以表示任何类型（类似c++ 的void *）
2. 通过断言将空接口转换为指定类型

```go
// 采用断言式的类型转换

func DoSomething(p interface {}) {
	if i,ok := p.(int); ok{ // ok=true时转换成功
		fmt.Println("int", i)
		return
	}
	if s,ok := p.(string); ok {
		fmt.Println("string", s)
		return
	}
	fmt.Println("unknow type")
}

func DoSomething(p interface {}) {
	switch v := p.(type) {
		case int :
			fmt.Println("int", v)
		case string:
			fmt.Println("string", v)
		default:
			fmt.Println("unknow type")
	}
}
```

> go 里经常用第二个值表示成功与否，自己定义方法时也要符合这样的习惯

## 接口最佳实践

1. 使用小的接口定义，很多接口只包含一个方法

对实现者来说负担更轻，不需要实现大接口的所有方法
```go
type Reader interface {
	Read(p []byte) (n int, err error)
}

type Writer interface {
	Write(p []byte) (n, int, err error)
}
```

2. 较大的接口定义，由多个小接口定义组合而成

```go
type ReadWriter interface {
	Reader
	Writer
}
```

3. 只依赖必要功能的最小接口

便于更多的地方复用