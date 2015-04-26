[![Build status](https://ci.appveyor.com/api/projects/status/xi8q5oxf5xc07e0d/branch/master?svg=true)](https://ci.appveyor.com/project/Spritely/recipes-mvc/branch/master)

# Spritely.Recipes.Mvc
Collection of simple pieces of reusable code (for ASP.NET MVC) designed such that dependencies aren't forced upon consumers of its packages. All packages come as source code and objects are marked internal so they aren't exposed from your build.

## Spritely.Recipes.Mvc.CatchAllRoute

Provides code to add a catch all route to MVC for single page applications (SPAs) so the client app can use non-hash urls via JavaScript pushState. After adding this recipe make the following changes to your MVC application:

1. Add the catch-all route to your route table:

```csharp
  // Where Home/Index are the HomeController and Index action which serves your JavaScript application
  RouteTable.Routes.Add("CatchAll", new CatchAllRoute("Home", "Index"));
```

2. Add the following 404 handler to your web.config so that anything handled by IIS has the same behavior:
```xml
  <httpErrors errorMode="Custom" existingResponse="Replace">
      <remove statusCode="404" />
      <error statusCode="404" responseMode="ExecuteURL" path="/Home/Index" />
  </httpErrors>
```
