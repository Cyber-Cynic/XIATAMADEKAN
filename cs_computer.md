### CPU流水线？
![pipeline](https://simplecore-ger.intel.com/techdecoded/wp-content/uploads/sites/11/figure-2-3.png)

https://techdecoded.intel.io/resources/understanding-the-instruction-pipeline/#gs.wjwsjh

### CPU高速缓存？
![cache](https://www.hardwaretimes.com/wp-content/uploads/2020/01/skylake-cache-design.png)  

https://www.hardwaretimes.com/difference-between-l1-l2-and-l3-cache-what-is-cpu-cache/

### MESI协议？
CPU缓存一致性协议。  
MESI 协议的由来呢，来自于我们对 Cache Line 的四个不同的标记，分别是：  
M：代表已修改（Modified）  
E：代表独占（Exclusive）  
S：代表共享（Shared）  
I：代表已失效（Invalidated）  

https://blog.csdn.net/qyf__123/article/details/100904595


### 局部性原理？
访问局部性（英语：Locality of reference）指的是在计算机科学领域中应用程序在访问内存的时候，倾向于访问内存中较为靠近的值。

访问局部性一般分为两种种基本形式，一种是时间局部性，另一种是空间局部性。  
1. 时间局部性指的是，程序在运行时，最近刚刚被引用过的一个内存位置容易再次被引用，比如在调取一个函数的时候，前不久才调取过的本地参数容易再度被调取使用。
2. 空间局部性指的是，最近引用过的内存位置以及其周边的内存位置容易再次被使用。空间局部性比较常见于循环中，比如在一个数列中，如果第3个元素在上一个循环中使用，则本次循环中极有可能会使用第4个元素。

局部性是出现在计算机系统中的一种```可预测```行为。系统的这种强访问局部性，可以被用来在处理器内核的指令流水线中进行性能优化，如缓存，内存预读取以及```分支预测```。

### CPU乱序执行？
避免因为获取下一条程序指令所引起的处理器等待，取而代之的处理下一条可以立即执行的指令。

### CPU分支预测？
分支预测器猜测条件表达式两路分支中哪一路最可能发生，然后推测执行这一路的指令，来避免流水线停顿造成的时间浪费。

### 内存屏障？
内存屏障（英语：Memory barrier），也称内存栅栏，内存栅障，屏障指令等，是一类```同步屏障```指令，它使得 CPU 或编译器在对内存进行操作的时候, 严格按照一定的顺序来执行, 也就是说在memory barrier 之前的指令和memory barrier之后的指令不会由于系统优化等原因而导致乱序。

>同步屏障(Barrier)是并行计算中的一种同步方法。对于一群进程或线程，程序中的一个同步屏障意味着任何线程/进程执行到此后必须等待，直到所有线程/进程都到达此点才可继续执行下文。

### 编译器优化技术？
常见：
1. 公共子表达式消除
2. 数组边界检查消除
3. 方法内联
4. 逃逸分析  

https://zhuanlan.zhihu.com/p/94551728  
