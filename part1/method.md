# 定义
方法是与对象实例绑定的特殊函数，是面向对象编程的基本概念

* 方法的receive类型可以是基础类型或指针类型，这会关系到调用对象实例时是否被复制
* 可以使用实例值或指针调用方法，编译器会根据方法receive类型自动在基础类型和指针类型间转换
* 不能使用多级指针调用方法

# 如何选则方法的receive类型？
* 要修改实例状态，用*T
* 无须修改状态的小对象或固定值，建议用T
* 大对象建议用*T，以减少复制成本
* 引用类型、字符串、函数等指针包装对象，直接用T
* 若包含Mutex等同步对象，用*T，避免因复制造成锁操作无效
* 其他无法确定的情况，用*T

# 方法集

<font face="微软雅黑">类型有一个与之相关的方法集（method set ）,*这决定了它是否实现某个接口*</font>
* 类型T方法集包含所有receiver T 方法
* 类型 \*T方法集包含所有receiver T + *T方法
+ 匿名嵌入S，T方法集包含所有receiver S 方法
+ 匿名嵌入\*S，T方法集包含所有receiver S+ *S 方法
+ 匿名嵌入S或\*S,\*T方法集包含所有receiver S+ *S 方法