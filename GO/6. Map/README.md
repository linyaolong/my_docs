## 基本使用

### 1. 声明
```go
m := map[string]int{"one":1, "two":2, "three":3}
m1 := map[string]int{}
m1["one"] = 1
m2 := make(map[string]int, 10 /*容量大小*/)
```
> 为什么不初始化len
>> map无法初始化0值
- 无法用cap(map) 获取容量大小

### 2. 元素访问
当map的键不存在时，读取会得到默认0值，无法通过nil判断元素是否存在
```go
m := map[int]int{}
t.Log(m[1])     // ==0
m[2] = 0
t.Log(m[2])     // ==0
```

判断键是否存在
```go
m := map[int]int{}
if v, ok := m[1]; ok {      // val,bool
    t.Log("exit:", v)
} else {
    t.Log("not exit")
}
```

### 3. 遍历
```go
m := map[string]int{"one":1, "two":2, "three":3}
for k, v := range m {
    t.Log(k, v)
}
```
### 4. 删除
```go
m := map[string]int{"one":1, "two":2}
delete(m, "one")
```

## 其他用法

### 1. 实现工厂
map的value可以是一个方法
```go
m := map[int]func(op int)int{}
m[1] = func(op int) int { return op }
m[2] = func(op int) int { return op * op }
m[3] = func(op int) int { return op * op * op }
t.Log(m[1](2), m[2](2), m[3](2))        // 2 4 8
```

### 2. 实现set
内置集合没有set实现，可以用map[int]bool实现
```go
ms := map[int]bool
// 增加元素
ms[1] = true
// 判断元素存在
if ms[1] {}
// 删除元素
delete(ms, 1)
// 元素个数
len(ms)
```