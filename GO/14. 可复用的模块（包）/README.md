## package

1. 基本复用模块单元

以首字母大写来表明可被包外代码访问

包的import路径要从src以后的路径写起

2. 代码的package可以和所在的目录不一致

3. 同意目录里的go代码的package要保持一致

## init方法

1. 在main被执行前，所有依赖的package的init方法都会被执行

2. 不同包的init函数按照包导入的依赖关系决定执行顺序

3. 每个包可以有多个init函数

4. 包的每个源文件也可以有多个init函数

## 导入远程包

1. 通过go get获取远程依赖

```shell
go get -u [url]
```

2. import package

```go
import "github.com/"
import cm "github.com/"// package别名
```

3. 提交

直接以代码所在路径提交，不提交src