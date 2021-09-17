## Dotnet Core的项目结构变化
https://www.cnblogs.com/tiger-wang/p/14267942.html

## ASP.NET 5 基本原理
https://docs.microsoft.com/en-us/aspnet/core/fundamentals/?view=aspnetcore-5.0&tabs=windows

## ASP.NET 5 项目
1. 访问入口  
```Program--->Main--->IHostBuilder.Build().Run()```

2. Create IHostBuilder
```
Host.CreateDefaultBuilder(args).ConfigureWebHostDefaults(webBuilder =>{
      webBuilder.UseStartup<Startup>();
});
```

3. Startup: 
```
// This method gets called by the runtime. Use this method to add services to the container.
public void ConfigureServices(IServiceCollection services)
```
```
// This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
```

4. 配置文件  
项目根目录下 appsettings.json 
The default ```JsonConfigurationProvider``` loads configuration in the following order:  
a. ```appsettings.json```  
b. ```appsettings.Environment.json```: For example, the appsettings.Production.json and appsettings.Development.json files.   
The environment version of the file is loaded based on the IHostingEnvironment.EnvironmentName.   
c. appsettings.Environment.json values override keys in appsettings.json.  

读取配置示例
```
public class TestModel : PageModel
{
    // requires using Microsoft.Extensions.Configuration;
    private readonly IConfiguration Configuration;

    public TestModel(IConfiguration configuration)
    {
        Configuration = configuration;
    }

    public ContentResult OnGet()
    {
        var myKeyValue = Configuration["MyKey"];
        var title = Configuration["Position:Title"];
        var name = Configuration["Position:Name"];
        var defaultLogLevel = Configuration["Logging:LogLevel:Default"];


        return Content($"MyKey value: {myKeyValue} \n" +
                       $"Title: {title} \n" +
                       $"Name: {name} \n" +
                       $"Default Log Level: {defaultLogLevel}");
    }
}
```

## ASP.NET Core中怎么使用HttpContext.Current？
HttpContext.Current doesn't exist anymore in ASP.NET Core but there's a new IHttpContextAccessor that you can inject in your dependencies and use to retrieve the current HttpContext:
```
public class MyComponent : IMyComponent
{
    private readonly IHttpContextAccessor _contextAccessor;

    public MyComponent(IHttpContextAccessor contextAccessor)
    {
        _contextAccessor = contextAccessor;
    }

    public string GetDataFromSession()
    {
        return _contextAccessor.HttpContext.Session.GetString(*KEY*);
    }
}
```
https://stackoverflow.com/questions/31243068/access-the-current-httpcontext-in-asp-net-core

## ConfigureAwait(false) relevant in ASP.NET Core?
ConfigureAwait only has effects on code running in the context of a SynchronizationContext which ASP.NET Core doesn't have (ASP.NET "Legacy" does).  
General purpose code should still use it because it might be running with a SynchronizationContext.  
https://stackoverflow.com/questions/42053135/configureawaitfalse-relevant-in-asp-net-core

