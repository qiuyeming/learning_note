# 测试
+ 测试命令（go test）忽略已“_”或“.”开头的测试文件
+ 正常编译操作（go build/install）会忽略测试文件

	go test ./.. 测试当前包和所有子包

# T 类型控制测试结果和行为
方法|说明|相关
---|---|---
Fail|失败：继续执行当前测试函数
FailNow|失败：立即终止执行当前测试函数|Failed
SkipNoe|跳过：停止执行当前测试函数|Skip,Skipf,Skipped
Log|输出错误信息，仅失败或-v时输出|Logf
Parallel|与有同样设置的测试函数并行执行
Error|Fail+Log|Errorf
Fatal|FailNow+Log|Fatalf


## t.Parallel() 是同时运行多个测试函数
示例： A和B并行运行测试
```
func TestA(t *testing.T)  {
	t.Parallel()
}
func TestB(t *testing.T)  {
	t.Parallel()
}
```
# 常见测试参数
参数|说明|示例
---|----|----
-args|命令行参数
-v|输入详细信息
-parallel|并发执行，默认值为GOMAXPROCS | -parallel 2
-run|指定测试函数，正则表达式 | -run "Add"
-timeout |全部测试累计时间超时会引发PANIC，默认为10ms| -timeout 1m30s
-count|重复测试次数|默认为1

# table driven模式
todo
# test main 模式
todo
```
	func TestMain(m *testing.M){
	}
```

# example 
例代码是为了导入帮助文档，通过对比输出结果stdout和内部output 注释是否一致来判断是否成功.(所以不能使用内置print/println)


```
func ExampleAdd() {
	fmt.Println(add(1,2))
	fmt.Println(add(2,2))
	//Output
	//3
	//4

}
```
如果没有output注释，该示例函数不会被执行