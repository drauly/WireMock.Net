# WireMock.Net
A C# .NET version based on [mock4net](https://github.com/alexvictoor/mock4net) which mimics the functionality from the JAVA based http://WireMock.org

[![Build status](https://ci.appveyor.com/api/projects/status/b3n6q3ygbww4lyls?svg=true)](https://ci.appveyor.com/project/StefH/wiremock-net)
[![Coverage Status](https://coveralls.io/repos/github/WireMock-Net/WireMock.Net/badge.svg?branch=master)](https://coveralls.io/github/WireMock-Net/WireMock.Net?branch=master)
[![GitHub issues](https://img.shields.io/github/issues/WireMock-Net/WireMock.Net.svg)](https://github.com/WireMock-Net/WireMock.Net/issues)
[![GitHub stars](https://img.shields.io/github/stars/WireMock-Net/WireMock.Net.svg)](https://github.com/WireMock-Net/WireMock.Net/stargazers)

| Name | NuGet |
| ---- | ----- |
| WireMock.Net | [![NuGet Badge](https://buildstats.info/nuget/WireMock.Net)](https://www.nuget.org/packages/WireMock.Net) |
| WireMock.Net.StandAlone | [![NuGet Badge](https://buildstats.info/nuget/WireMock.Net.StandAlone)](https://www.nuget.org/packages/WireMock.Net.StandAlone) |

### Frameworks
The following frameworks are supported:
- net 4.5.2 and up
- net 4.6 and up
- netstandard 1.3
- netstandard 2.0

## Build info
To build you need:
- Microsoft .NET Framework 4.5.2 Developer Pack (https://www.microsoft.com/en-us/download/details.aspx?id=42637)
- Microsoft .NET Framework 4.6 Targeting Pack (https://www.microsoft.com/en-us/download/confirmation.aspx?id=48136)
- Microsoft .NET Framework 4.6.2 Developer Pack (https://www.microsoft.com/en-us/download/confirmation.aspx?id=53321)
- .NET Core 2.0 (https://www.microsoft.com/net/core)


## Stubbing
A core feature of WireMock.Net is the ability to return canned/predefined HTTP responses for requests matching criteria, see [Wiki : Stubbing & Request Matching](https://github.com/WireMock-Net/WireMock.Net/wiki/Stubbing-and-Request-Matching).

## Using WireMock in UnitTest framework
You can use your favorite test framework and use WireMock within your tests, see
[Wiki : UnitTesting](https://github.com/StefH/WireMock.Net/wiki/Using-WireMock-in-UnitTests).

## Admin API Reference
The WireMock admin API provides functionality to define the mappings via a http interface, see [Wiki : Admin API Reference](https://github.com/StefH/WireMock.Net/wiki/Admin-API-Reference).

## WireMock as a standalone process
This is quite straight forward to launch a mock server within a console application, see [Wiki : standalone](https://github.com/StefH/WireMock.Net/wiki/WireMock-as-a-standalone-process).

### SSL
You can start a standalone mock server listening for HTTPS requests. To do so, there is just a flag to set when creating the server:
```csharp
var server1 = FluentMockServer.Start(port: 8443, ssl: true);

// or like this

var server2 = FluentMockServer.Start(new FluentMockServerSettings
{
    Urls = new[] { "http://localhost:9091", "https://localhost:9443" }
});
```

- In case when using **net 4.5.2** or **net 4.6**, you need a certificate registered on your box, properly associated with your application and the port number that will be used. This is not really specific to WireMock.Net, not very straightforward and hence the following stackoverflow thread might come handy: [Httplistener with https support](http://stackoverflow.com/questions/11403333/httplistener-with-https-support).

- When using **netstandard**, WireMock.Net uses a self signed certificate (which can be overriden if you like) to host https urls.
