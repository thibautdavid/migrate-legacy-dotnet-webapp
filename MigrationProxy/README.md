# MigrationProxy using YARP

This solution is a simple POC of serving the legacy and new application through the new application using YARP to switch to legacy application when the feature does'nt exist on the new application.

Implements the [The Strangler Fig Pattern](https://docs.microsoft.com/azure/architecture/patterns/strangler-fig), using [YARP](https://microsoft.github.io/reverse-proxy/index.html) application reverse proxy as stated in the Microsoft blog article : https://devblogs.microsoft.com/dotnet/incremental-asp-net-to-asp-net-core-migration/.

## How it works

### Legacy application

No changes is required on the legacy application.
The only thing to think about is switching the DNS nae of the legacy applicationto the new application to avoid users to access directly to the legacy application wihtout going througth the proxy.

### New application

This application is an aspnet mvc (dotnet 6.0) application.

List of things to do to serve the legacy application througth YARP proxy:

1- install the YARP nuget package (https://www.nuget.org/packages/Yarp.ReverseProxy)

2- configure it in the appsettings.json on the targeted environement (see the file ./MigrationProxy.NewWebApp/appsettings.json). Take note of the legacy system url in the configuration.

3- setup the proxy in the application : look for `// YARP` commented lines in ./MigrationProxy.NewWebApp/program.cs

4- look at the `About` and `Contact` menu items in the `_Layout.cshtml`. Using `asp-is-disabled=true` enable to bypass the Razor routing system and let you speficy the url in the href tag. It allows to specify and legacy application url which will be handled by the YARP proxy, to serve the legacy page. 

And voila !
