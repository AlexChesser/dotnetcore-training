# Creating a new project

`dotnet new mvc --name Training.MVC`

# what's new in an MVC project (when compared to the API)?

* in `ConfigureServices` we now use `services.AddControllersWithViews();` (as opposed to `services.AddControllers()`)
* in `Configure`:
    - `app.UseStaticFiles();` is new which wets up the `wwwroot` folder as the place files are served from
    - a default route is added 
* in the `Controllers` - notice that we now derive from `Controller` instead of `ControllerBase` this is because the latter has built in support for `VIEWS` [read the documentation](https://docs.microsoft.com/en-us/aspnet/core/web-api/?view=aspnetcore-3.1)
* there is now a `views` folder where web partials live

# understading how the web-request lifecycle works

![](../img/middleware-pipeline.svg) [source](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/middleware/?view=aspnetcore-3.1)

when a request comes into the website the instruction set travels DOWN the middleware chain. Each piece of middleware has the opportunity to act on the user's request. Some examples:     

* a user makes a valid request to the URL http://localhost:5000/favicon.ico
     1. when the request reaches the `HttpsRedirection` middleware, a response is generated which sends the user's browser to https://localhost:5001/favicon.ico and a new request begins automatically
     2. the new request can now get further down the pipeline to `StaticFiles` where the webserver does manage to detect a file in the `wwwroot` folder named `favicon.ico` the file is returned to the browser and the request is complete
* a user makes a request for the URL https://localhost:5001/home/privacy
     1. the user's request travels down the pipeline. When it reaches the `StaticFiles` middleware, since a file with the name `/home/privacy` is not found in the `wwwroot` folder the request continues to the `Routing` middleware. 
     2. the **routing** middleware determines that there IS a **home** controller and it has a **privacy** action. This matches the pattern that was established on line 53 of [Startup.cs](Training.MVC/Startup.cs) `pattern: "{controller=Home}/{action=Index}/{id?}");`
     3. a NEW instance of the HOME controller is `injected`, our host environment (the webserver), runs through a list of the dependencies that are required and passes them to the controller automatically.
     4. The this new home controller then executes the Constructor function `HomeController(ILogger<HomeController> logger)` and then the `Privacy` function.
     5. The framework then looks for a text file within VIEWS which matches the name of the method we're running. In this case `Views/Home/Privacy.cshtml` this then returns the VIEW back to the browser.

## the anatomy of a view
1. The framework has a built-in rule that all views run through `_ViewStart.cshtml` this sets the default layout to the file `Views/Shared/_Layout.cshtml` 
2. Effectively, the entrypoint for any given WEBPAGE starts in `Views/Shared/_Layout.cshtml` 
3. The content of the CURRENT VIEW in will appear at the point within the Layout where the `@RenderBody()` command appears.


    

    


