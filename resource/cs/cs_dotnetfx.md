## .NET 术语
.NET is a ```free```, ```open-source development platform``` for building many kinds of apps.  
https://docs.microsoft.com/en-us/dotnet/standard/glossary 


## SDK vs Runtime
Install a ```runtime``` on a machine that you want to prepare for running .NET apps.   
Install the ```SDK``` on a machine that you want to use for development. When you download the SDK, you automatically get the runtimes with it.  
下载地址：https://dotnet.microsoft.com/download/dotnet 

## CLR
The .NET CLR is a ```cross-platform runtime``` that includes support for Windows, macOS, and Linux.   
The CLR handles memory allocation and management.   
The CLR is also a ```virtual machine``` that not only executes apps but also generates and compiles code using a just-in-time (JIT) compiler.

## AOT vs JIT
1. AOT: head-of-time
2. JIT:Just-In-Time  
Higher-level .NET languages, such as C#, compile down to a hardware-agnostic instruction set, which is called Intermediate Language (IL).   
When an app runs, the JIT compiler translates IL to machine code that the processor understands. 

## implementations of .NET ?
Implementations of .NET include the:
1. .NET Framework,
2. .NET 5 (and .NET Core)
3. Mono

There is an API specification common to multiple implementations of .NET that's called ```.NET Standard```.

## ASP.NET MVC 和 ASP.NET WebApi的区别？

## ASP.NET MVC ModelBinder?

## ASP.NET MVC Filter?

## ASP.NET MVC 路由?

## ASP.NET MVC Razor模板引擎?

## 依赖注入框架 和 生命周期?

## HttpModule 和 HttpHandler 区别？

## ASP.NET MVC 请求流程 和 生命周期？