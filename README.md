# migrate-legacy-dotnet-webapp

Differentes exéprimentations permettant d'apprendre à gérer la modernisation d'applications dotnet legacy vers du dotnet core.
Several experiments to learn how to manage aspnet Framework legacy web applications (websites, webform or old mvc apps) to actual dotnet core technologies.

list of the several approaches :

1- implementing the [The Strangler Fig Pattern](https://docs.microsoft.com/azure/architecture/patterns/strangler-fig), using [YARP](https://microsoft.github.io/reverse-proxy/index.html) application reverse proxy as stated in the Microsoft blog article : https://devblogs.microsoft.com/dotnet/incremental-asp-net-to-asp-net-core-migration/
2- using the [Microsoft.AspNetCore.SystemWebAdapters](https://www.nuget.org/packages/Microsoft.AspNetCore.SystemWebAdapters) in the new application where to migrate legacy code whithout to break all usage of System.Web.dll legacy dotnet Framework assembly.
3- migrating WebSite to WebApp using VS2019 following this [Microsoft blog article](https://devblogs.microsoft.com/dotnet/converting-a-web-site-project-to-a-web-application-project/) and this [documentation](https://learn.microsoft.com/en-us/previous-versions/aa983476(v=vs.140)?redirectedfrom=MSDN).

Last peace to explore : migrating WebForm design to MVC. The only way I see for now is to combine approches #1 and #2 and rewrite most of the legacy.


