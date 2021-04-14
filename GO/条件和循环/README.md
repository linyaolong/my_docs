### 循环

1. 仅支持`for`

```go
for j :=1 ; j <= 10; j++{

}
```

2. whie (n < 10)

```go
for n < 10 {

}
```

3. while (true)

```go
for {

}
```

### `if`条件

1. condition表达式必须为布尔值
```go
if condition {
    
} else {
    
}
```

2. 支持变量赋值
```go
if var declaration; condition {
    
}
```

### switch条件

1. 条件表达式不限制常量和整数
2. 单个case可以出现多个结果，用逗号分隔
3. 不需要break退出
```go
switch day := GetDay(); day {
case "Monday":
case "SATURDAY","Sunday":
default:
}
```

4. 可以不设定switch后的条件表达式，与多个if...else...逻辑作用相同
```go
switch {
    case 0 <= num && num < 4:
    case 4<=num && num < 7:
}
```