### Add services to DI
After creating a new app, examine the Main method in Program.cs:

```
static void Main(string[] args)
{
    var serviceProvider = new BrowserServiceProvider(services =>
    {
        // Add custom services here
        services.AddSingleton<IDataAccess, DataAccess>();
    });

    new BrowserRenderer(serviceProvider).AddComponent<App>("app");
}
```
###  Method	Description
**Singleton**  - DI creates a single instance of the service. All components requiring this service receive a reference to this instance.<br/>
**Transient** -	Whenever a component requires this service, it receives a new instance of the service.<br>
**Scoped** - Blazor doesn't currently have the concept of DI scopes. Scoped behaves like Singleton. Therefore, prefer Singleton and avoid Scoped.

###  Default services
**IUriHelper** - Helpers for working with URIs and navigation state (singleton).<br>
**HttpClient** - Provides methods for sending HTTP requests and receiving HTTP responses from a resource identified by a URI (singleton). Note that this instance of HttpClient uses the browser for handling the HTTP traffic in the background. HttpClient.BaseAddress is automatically set to the base URI prefix of the app.

### Using Inject
```
@inject IDataAccess DataRepository

```

### Dependency injection in services
```
public class DataAccess : IDataAccess
{
    // The constructor receives an HttpClient via dependency
    // injection. HttpClient is a default service offered by Blazor.
    public Repository(HttpClient client)
    {
        ...
    }
    ...
}
```
### Getting stuff from IServiceProvider
```
@inject IServiceProvider Services

@functions {
    WeatherForecast[] forecasts;

    protected override async Task OnInitAsync()
    {
        var client = Services.GetRequiredService<HttpClient>();
        forecasts = await client.GetJsonAsync<WeatherForecast[]>("/sample-data/weather.json");
    }
}
```
