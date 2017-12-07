1.GC就是垃圾回收.
2.减少GC最最最有效的办法, 就是减少垃圾的产生.
* 要减少垃圾, 常见的方法:
 *    对象池, pool.
 *    内存复用, 自己申请一大块内存, 然后手动管理, 实现循环利用. 经常以[]byte, buffer的形式存在.
 *    细致的设计, 尽量少new一些短生命周期的对象.
 *     减少内存复制, string和[]byte的一些细节.