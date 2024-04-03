### CLR via C#
http://sd.blackball.lv/library/CLR_via_CSharp_(Jeffrey_Richter_4th_Edition).pdf

### C# 历史
https://docs.microsoft.com/en-us/dotnet/csharp/whats-new/csharp-version-history

### C# 基础概念
https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/language-specification/introduction

### C# 关键字？
https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/  

比如new关键字，在不同地方的使用意义也不同。

### Stackoverflow上针对C#的高票提问？
https://stackoverflow.com/questions/tagged/c%23?tab=Votes

### BCL 和 FCL 的区别？
1. The Base Class Library (BCL) is literally that, the base. It contains basic, fundamental types like System.String and System.DateTime.
2. The Framework Class Library (FCL) is the wider library that contains the totality: ASP.NET, WinForms, the XML stack, ADO.NET and more. You could say that the FCL includes the BCL.

https://stackoverflow.com/questions/807880/bcl-base-class-library-vs-fcl-framework-class-library

### CLR架构和执行过程？
![CLRArch](https://media.geeksforgeeks.org/wp-content/uploads/20190422170556/Architecture-of-Common-Language-RuntimeCLR.png)  
![CLR](https://flylib.com/books/4/253/1/html/2/images/0131472275/graphics/01fig03.gif)

### C# 有哪些类型？
1. 值类型
2. 引用类型

C#内置的类型有：https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types

### 值类型和引用类型的区别？
![value&reference](http://net-informations.com/faq/general/img/reference-type.png)

### 单例 和 静态类 的区别是什么？
The big difference between a singleton and a bunch of static methods is that singletons can implement interfaces (or derive from useful base classes, although that's less common, in my experience), so you can pass around the singleton as if it were "just another" implementation.

1. A singleton allows access to a single created instance - that instance (or rather, a reference to that instance) can be passed as a parameter to other methods, and treated as a normal object.
2. A static class allows only static methods.  

更多阅读： https://stackoverflow.com/questions/519520/difference-between-static-class-and-singleton-pattern  
扩展spring singleton bean:https://stackoverflow.com/questions/21828664/why-spring-bean-is-singleton-scope

### 写一个单例看看？
```
public sealed class Singleton
{
    private Singleton(){}
    private static readonly Lazy<Singleton> lazy = new Lazy<Singleton>(() => new Singleton());
    public static Singleton Instance { get { return lazy.Value; } }
}
```
https://csharpindepth.com/articles/singleton

### 什么时候用Lazy？
更多阅读：https://stackoverflow.com/questions/6847721/when-should-i-use-lazyt

### 堆和栈的区别？
1. The stack is the memory set aside as scratch space for a thread of execution.
2. The heap is memory set aside for dynamic allocation.  
更多阅读：https://stackoverflow.com/questions/79923/what-and-where-are-the-stack-and-heap

### 什么是装箱和拆箱？如何避免？
1. 值类型 to 引用类型，装箱  
![boxing](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/types/media/boxing-and-unboxing/boxing-operation-i-o-variables.gif)
2. 引用类型 to 值类型，拆箱  
![boxing](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/types/media/boxing-and-unboxing/unboxing-conversion-operation.gif)

举例子：ArrayList接受object，放入int的时候，就需要装箱。  

使用泛型可以避免装箱。

### C# 参数是值传递还是引用传递？
1. 值传递（pass by value）是指在调用函数时`将实际参数复制一份`传递到函数中，这样在函数中如果对参数进行修改，将`不会`影响到实际参数。
2. 引用传递（pass by reference）是指在调用函数时`将实际参数的地址`直接传递到函数中，那么在函数中对参数所进行的修改，将`影响`到实际参数。

注意：对于应用类型，是把实参`对象引用的地址`当做值传递给了形式参数。  
更多阅读：https://stackoverflow.com/questions/40480/is-java-pass-by-reference-or-pass-by-value/40523#40523  
https://www.zhihu.com/question/31203609/answer/576030121

### Why does C# always use callvirt?
https://docs.microsoft.com/zh-cn/archive/blogs/ericgu/why-does-c-always-use-callvirt  
https://medium.com/@joni2nja/c-emits-callvirt-for-non-virtual-method-1b3d8f58ea79  
C# almost always emit a callvirt when calling a method, even on a non-virtual method.   
callvirt has the advantage of doing an implicit null-check, so that the NullReferenceException will be thrown when you call a method on a null object.   
If the compiler ‘knows’ that the object won’t be null, it can optimize away to use call instead.   
The performance impact is so small that we should not really care about it.  

### string 和 String 什么关系？使用哪个？
编译器直接支持的数据类型就是基元类型。  
string是基元类型，String是FCL存在的类型，基元类型直接映射到FCL的类型。  
比如int，直接映射System.Int32。  
C#语言规范建议最好使用关键字。

### ref 和 out区别？
ref tells the compiler that the object is initialized before entering the function,  
while out tells the compiler that the object will be initialized inside the function.

So while ref is two-ways, out is out-only.

更多阅读：https://stackoverflow.com/questions/388464/whats-the-difference-between-the-ref-and-out-keywords

### readonly 和 const区别？
1. const must be initialized at declaration time
2. readonly can be initialized on the constructor  

Just to add, readonly for reference types only makes the reference read only not the values. For example:
```
public class Const_V_Readonly
{
  public const int I_CONST_VALUE = 2;
  public readonly char[] I_RO_VALUE = new Char[]{'a', 'b', 'c'};

  public UpdateReadonly()
  {
     I_RO_VALUE[0] = 'V'; //perfectly legal and will update the value
     I_RO_VALUE = new char[]{'V'}; //will cause compiler error
  }
}
```
更多阅读：https://stackoverflow.com/questions/55984/what-is-the-difference-between-const-and-readonly-in-c

### Overloading 和 overriding 的区别？
1. Overloading is when you have multiple methods in the same scope, with the same name but different signatures.  
2. Overriding is a principle that allows you to change the functionality of a method in a child class.  

更多阅读：https://stackoverflow.com/questions/673721/overloading-and-overriding

### override 和 new 的区别？
1. The override modifier may be used on virtual methods and must be used on abstract methods.   
This indicates for the compiler to use the last defined implementation of a method.   
```Even if the method is called on a reference to the base class it will use the implementation overriding it. ```
2. The new modifier instructs the compiler to use your child class implementation instead of the parent class implementation.   
Any code that is not referencing your class but the parent class will use the parent class implementation.

更多阅读： https://stackoverflow.com/questions/1399127/difference-between-new-and-override

### == 和 Equals()区别？
1. When == is used on an expression of type object, it'll resolve to System.Object.ReferenceEquals.
2. Equals is just a virtual method and behaves as such, so the overridden version will be used (which, for string type compares the contents).  
对于`string`类型，都是比较内容。  
更多阅读：https://stackoverflow.com/questions/814878/c-sharp-difference-between-and-equals 

### 为什么重写Equals()，同时要重写GetHashCode()？
1. 为什么有GetHashCode虚方法？  
FCL设计者认为，如果能将任何对象的任何实例放在哈希表集合中，能带来好多好处。所以为Object提供了GetHashCode虚方法，能获得任意对象的int32哈希码。
  
2. Hashtable、Dictionary等集合的实现中，要求两个对象必须具有相同的哈希码才视作相等。   
    a. 向集合添加键值对，首先要获取对象的哈希码，该哈希码指出键值存储到哪个桶里。  
    （https://referencesource.microsoft.com/#mscorlib/system/collections/generic/dictionary.cs,334）  
    b. 集合查找键时，会获取指定键对象的哈希码，该哈希码标识了现在要以顺序方式搜索的哈希桶，将在其中查找。  
    (https://referencesource.microsoft.com/#mscorlib/system/collections/generic/dictionary.cs,297)  

来自《CLR via C#》 P126  
更多阅读：https://codingsight.com/the-origin-of-gethashcode-in-net/  
https://stackoverflow.com/questions/2265503/why-do-i-need-to-override-the-equals-and-hashcode-methods-in-java


### Dictionary和Hashtable有什么区别？Why is Dictionary preferred over Hashtable in C#?
1. 概念上，a Dictionary is a hash table.  
2. 为什么常用Dictionary<TKey, TValue>，因为它是泛型  
3. Dictionary<TKey, TValue>的实现就是copy Hashtable的，见：https://referencesource.microsoft.com/#mscorlib/system/collections/hashtable.cs  
更多阅读：https://stackoverflow.com/questions/301371/why-is-dictionary-preferred-over-hashtable-in-c

### dynamic有啥用?
1. C# 4.0 引入
2. to tell the compiler that a variable's type can change or that it is not known until runtime
3. when you are using a dynamic variable, you are giving up compiler type checking
4. being able to reuse variables for different types of data
更多阅读：https://stackoverflow.com/questions/2690623/what-is-the-dynamic-type-in-c-sharp-4-0-used-for

### 访问修饰符有哪些？默认是什么？
```public```: The type or member can be accessed by any other code in the same assembly or another assembly that references it.  
```private```: The type or member can be accessed only by code in the same class or struct.  
```protected```: The type or member can be accessed only by code in the same class, or in a class that is derived from that class.  
```internal```: The type or member can be accessed by any code in the same assembly, but not from another assembly.  
```protected internal```: The type or member can be accessed by any code in the assembly in which it's declared, or from within a derived class in another assembly.  
```private protected```: The type or member can be accessed only within its declaring assembly, by code in the same class or in a type that is derived from that class.  

注意：  
1. 类/结构体默认是```internal```    
2. 类/结构体成员默认是```private```    
https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/access-modifiers

### C# 迭代器？
传统遍历即通过集合类实现IEnumerable、IEnumerator或IEnumerable<T>、IEnumerator<T>接口来支持遍历。
1. IEnumerable 声明式接口，声明实现该接口的 类是可以枚举的。
2. IEnumerator 实现式接口，IEnumerator对象说明如何实现枚举器。

迭代器是C#2.0中的新功能。它使类或结构支持foreach迭代，而不必"显式"实现IEnumerable或IEnumerator接口。只要简单的使用yield关键字，由JIT编译器编译成实现IEnumerable 或IEnumerator接口的对象。
更多阅读：https://stackoverflow.com/questions/39476/what-is-the-yield-keyword-used-for-in-c

### C# 接口？
An interface contains definitions for a group of related functionalities that a non-abstract class or a struct must implement.   
An interface may define static methods, which must have an implementation.   
Beginning with C# 8.0, an interface may define a default implementation for members. 
An interface may not declare instance data such as fields, auto-implemented properties, or property-like events.  

### C# 接口和抽象类的区别？
接口表达 ```can do```  
抽象类表达 ```is a```

### C# 扩展方法？
> Extension methods enable you to "add" methods to existing types without creating a new derived type, recompiling, or otherwise modifying the original type. 
> Extension methods are static methods, but they're called as if they were instance methods on the extended type.
特点：
1. Extension methods are defined as `static methods` but are called by using instance method syntax.
2. Their first parameter specifies which type the method operates on. The parameter is preceded by the `this` modifier.
3. Extension methods are `only in scope` when you explicitly import the namespace into your source code with a using directive.

### C# 泛型？
算法通用，简单来说就是定义好算法，但是不设定该算法要操作的数据类型，该算法可以广泛应用于不同类型对象。  
1. 源代码保护：使用泛型算法的开发人员不需要访问算法源代码。
2. 类型安全： 编译检查
3. 更清晰的代码： 减少了类型转换，使代码更容易编写和维护。
4. 更佳的性能：没有泛型的时候，要想写一个通用的算法，所有成员必须定义成object类型。    
使用算法的时候，如果是值类型，就要进行装箱操作。    
装箱要在托管堆上进行内存分配，造成垃圾回收，从而损害程序性能。  
使用泛型的话，不需要装箱，提高代码的运行速度。  

### C# 泛型的协变与逆变？
1. 逆变： 泛型类型参数可以从```一个类```改为它的某个```派生类```，用```in```标记，只能出现在```输入```位置，比如作为方法的参数。  
2. 协变： 泛型类型参数可以从```一个类```改为它的某个```基类```，用```out```标记，只能出现在```输出```位置，比如作为方法的返回类型。

### C# 委托？
委托提供延迟绑定机制
> Delegates provide a late binding mechanism in .NET.  
> Late Binding means that you create an algorithm where the caller also supplies at least one method that implements part of the algorithm.

### C# 事件？
https://docs.microsoft.com/en-us/dotnet/csharp/events-overview

### delegates 和 events 的区别？
1. An Event declaration adds a layer of abstraction and protection on the delegate instance.   
This protection prevents clients of the delegate from resetting the delegate and its invocation list and only allows adding or removing targets from the invocation list.

2. 从语义上来说，也不是一个概念  

更多阅读：https://stackoverflow.com/questions/29155/what-are-the-differences-between-delegates-and-events

### C# LINQ？
将查询功能直接集成到C#语言中的技术的名称  
> Language-Integrated Query (LINQ) is the name for a set of technologies based on the integration of query capabilities directly into the C# language. 

### 什么是Lambda表达式？
1. use a lambda expression to create an anonymous function.
2. Any lambda expression can be converted to a delegate type.

### C# 表达式树？
> Expression Trees provide richer interaction with the arguments that are functions
> An Expression Tree is a data structure that defines code. 
> They are based on the same structures that a compiler uses to analyze code and generate the compiled output.

### 序列化？
> Serialization is the process of converting an object into a stream of bytes to store the object or transmit it to memory, a database, or a file.  
> Its main purpose is to save the state of an object in order to be able to recreate it when needed.   
> The reverse process is called deserialization.  

![Serialization](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/serialization/media/index/serialization-process.gif)

### 深拷贝vs浅拷贝？
1. 浅拷贝  
对于值类型和String类型成员，浅拷贝会在副本中重新创建成员；  
对于引用类型，对象和副本对象引用同一个内存地址，当在对象或者副本对象修改引用成员后，引用类型的成员就发生变化。  
浅拷贝通过系统提供的System.ICloneable方法实现，新建类是继承ICloneable接口，并实现Clone方法。  
3. 深拷贝  
不管是值类型还是引用类型，对象和副本对象修改成员属性都只会改变各自对象的值，两个对象是完全独立的实体。  
更多阅读：https://stackoverflow.com/questions/78536/deep-cloning-objects/78612#78612

### C# GC?
![GC](https://failingfast.io/assets/images/super-gc/diag11.png)  
算法：  
1. 引用计数算法，无法处理循坏引用的问题，导致无法回收
2. 引用追踪算法

过程：  
1. GC开始回收的时候，暂停进程中的所有线程。
2. 开始标记：遍历堆中所有的对象，将同步索引字段中一位设置为0（意思是都该删除）。  
然后CLR检查所有活动根（根就是所有引用类型的变量），查看引用了哪些对象。  
如果根包含null，忽略。  
任何根如果引用了堆上的对象，CLR会标记那个对象，将该对象的同步索引中的位设为1 。
一个对象被标记后，CLR会检查该对象中的根，标记它们引用的对象，如果对象标记过，就不再检查这个对象的字段了。（这样就避免循环引用而产生死循环）
3. 标记完之后，堆中的对象，要么可达（标记过，存在引用），要么不可达（未标记，不存在引用）。
4. 压缩阶段：CLR压缩所有幸存下来的对象，使它们占用连续的内存空间。移动了之后，根还是用的原来的地址，执行的时候岂不是出错了？所以，CLR还要从每个根减去所引用的对象在内存中偏移的字节数。
5. 压缩完之后，新分配的对象就在最后幸存的对象之后。

代：  
大量研究证明，1. 对象越新，生存期越短 2.对象越老，生存期越长 3. 回收堆的一部分，比回收整个堆快  
1. 第一次新分配到堆的对象，是第0代对象。第0代CLR会设置一个大小，新分配对象超了预算，就启动回收一次。
2. 回收一次之后，幸存的就是第一代，第0代又腾空了，新对象就可以加入了。
3. 当第0代再次超了预算，又一次垃圾回收开始了，开始前还会检查第一代占用的内存。（性能测试表明，对第0代垃圾回收不会超过1ms）
4. 多次回收第0代后，第1代也在增长（不断加入幸存的对象）。当第0代再次回收时候，发现第1代也超了预算了，于是这次两代都进行回收。第1代幸存的进入第2代，第0代幸存的进入第1代。

触发条件：
1. 调用GC.Collect
2. CLR 内部的win32函数报告低内存
3. CLR 卸载AppDomain
4. CLR 正在关闭

其他：
1. 大于等于85000字节，认为是大对象
2. 大对象总在第2代
3. 不压缩大对象

https://failingfast.io/a-super-simplified-explanation-of-net-garbage-collection/


### 强引用 vs 弱引用？
1. The garbage collector cannot collect an object in use by an application while the application's code can reach that object. The application is said to have a strong reference to the object.
2. A weak reference permits the garbage collector to collect the object while still allowing the application to access the object.

什么时候使用弱引用？  
Weak references are useful for objects that use a lot of memory, but can be recreated easily if they are reclaimed by garbage collection.  

https://docs.microsoft.com/en-us/dotnet/standard/garbage-collection/weak-references

### C# Idispose ?
https://stackoverflow.com/questions/538060/proper-use-of-the-idisposable-interface/538238#538238

### lock 的本质是什么？
本质就是语法糖，实际调用```Monitor.Enter()``` 和 ```Monitor.Exit()```  
java中对应的是```synchronized```关键字  
https://stackoverflow.com/questions/6029804/how-does-lock-work-exactly

### What does .ConfigureAwait(false) do?
By default, when you use async/await, it will resume on the original thread that started the request. However, if another long-running process currently has taken over that thread, you will be stuck waiting for it to complete. To avoid this issue, you can use a method called ConfigureAwait with a false parameter. When you do, this tells the Task that it can resume itself on any thread that is available instead of waiting for the thread that originally created it. This will speed up responses and avoid many deadlocks.  

However, there is a small loss here. When you resume on another thread, the thread synchronization context is lost. The biggest loss here is that you would lose any Culture or Language settings, along with things like HttpContext.Current from the original thread, though this is no longer a problem in .NET Core. Thus, if you don’t need translations or access to any HttpContext type settings, you are safe to make this call. NOTE: If you need language/culture, you can always store the current values before an await and then re-apply it after the await on the new thread.
https://www.skylinetechnologies.com/Blog/Skyline-Blog/December_2018/async-await-configureawait  

不过在asp.net core中没有synchronization context了，所以你写不写.ConfigureAwait(false)都没啥用了。  
https://blog.stephencleary.com/2017/03/aspnetcore-synchronization-context.html

### 异步死锁？
https://blog.stephencleary.com/2012/07/dont-block-on-async-code.html

### 什么时候使用Task.Yield()?
https://blog.csdn.net/java666668888/article/details/104007066

### C# 异步编程模型？
基于任务的异步编程模型 Task-based Asynchronous Pattern (TAP).  
The core of async programming is the ```Task``` and ```Task<T>``` objects, which model asynchronous operations.   
They are supported by the ```async``` and ```await``` keywords.

For I/O-bound code, you await an operation that returns a ```Task``` or ```Task<T>``` inside of an async method.  
For CPU-bound code, you await an operation that is started on a background thread with the ```Task.Run``` method.  
异步编程建议：https://docs.microsoft.com/en-us/dotnet/csharp/async#important-info-and-advice
