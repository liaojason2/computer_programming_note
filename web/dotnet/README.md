# dotnet

## .NET Upgrade Assistant
The [.NET Upgrade Assistant](https://learn.microsoft.com/dotnet/core/porting/upgrade-assistant-overview) is a command-line tool that helps developers upgrade their .NET Framework or older .NET Core applications to the latest version of .NET. It automates many of the steps involved in the upgrade process, making it easier and faster to modernize applications.
[What is GitHub Copilot app modernization - upgrade for .NET?](https://learn.microsoft.com/en-us/dotnet/core/porting/github-copilot-app-modernization-overview#supported-project-types)

## .NET

- [Install .NET Framework for developers](https://learn.microsoft.com/en-us/dotnet/framework/install/guide-for-developers)

### Yarp

- [No connection could be made because the target machine actively refused it DC](https://learn.microsoft.com/en-us/answers/questions/626063/no-connection-could-be-made-because-the-target-mac)

### JSON

- [JsonSerializer Class](https://learn.microsoft.com/en-us/dotnet/api/system.text.json.jsonserializer?view=net-9.0)

### Bootstrap

- [Static files in ASP.NET Core](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/static-files?view=aspnetcore-9.0)
- [Building Beautiful, Responsive Sites with Bootstrap](https://aspnetcore.readthedocs.io/en/stable/client-side/bootstrap.html#basic-templates-and-features)

### SQL

- [Microsoft.Data.Sqlite](https://learn.microsoft.com/en-us/dotnet/standard/data/sqlite/?tabs=net-cli)

## Session
- [ASP.NET Core Session State](https://learn.microsoft.com/aspnet/core/fundamentals/app-state?view=aspnetcore-7.0)
- [HttpContext.Session Property](https://learn.microsoft.com/en-us/dotnet/api/system.web.httpcontext.session?view=netframework-4.8.1&viewFallbackFrom=net-8.0)

```C#
// Set session value
// string
HttpContext.Session.SetString("Key", "Value");
HttpContext.Session.SetString("user", "Jason");

var value = HttpContext.Session.GetString("user");

// int
HttpContext.Session.SetInt32("Key", "Value");
HttpContext.Session.SetInt32("age", 30);

var user = HttpContext.Session.GetInt32("age");

// List
var items = new List<string> { "item1", "item2", "item3" };
HttpContext.Session.SetString("items", JsonSerializer.Serialize(items));

var itemsString = HttpContext.Session.GetString("items");
List<string> items = JsonSerializer.Deserialize<List<string>>(itemsString);
```