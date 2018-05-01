### Basic Component
```
public class ComponentBase : BlazorComponent
{
    // Blazor's dependency injection works even if using the
    // InjectAttribute in a component's base class.
    [Inject]
    protected IDataAccess DataRepository { get; set; }
    ...
}
```

### Base class inheritance for a "code-behind" experience
```
@page "/BlazorRocks"
@inherits BlazorRocksBase

<h1>@BlazorRocksText</h1>
```
```
using Microsoft.AspNetCore.Blazor.Components;

public class BlazorRocksBase : BlazorComponent
{
    public string BlazorRocksText { get; set; } = "Blazor rocks the browser!";
}
```
### communication between components

Render Fragment
```
<div class="panel panel-success">
    <div class="panel-heading">@Title</div>
    <div class="panel-body">@ChildContent</div>
</div>

@functions {
public string Title { get; set; }
public RenderFragment ChildContent { get; set; }
}
```
