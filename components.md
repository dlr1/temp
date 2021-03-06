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
### creating component dynamically
nicer APIs to build RenderFragments in the future, but for now 
```
@CreateDynamicComponent();

@functions {
    RenderFragment CreateDynamicComponent() => builder =>
    {
        builder.OpenComponent(0, typeof(SurveyPrompt));
        builder.AddAttribute(1, "Title", "Some title");
        builder.CloseComponent();
    };
}
```

### Handling events from child components

child component
```
@page "/comp1"
<button onclick="@clicked">click me</button>

　
@functions{
[Parameter]
private Action<int> OnMyEvent{get;set;}
int val;
    private void clicked()
    {
		val++;
        Console.WriteLine(val);
		OnMyEvent?.Invoke(val);
    }
}
```
parent component
```
@page "/"

<mycomp OnMyEvent="@((Action<int>)myevent)"></mycomp>
<mycomp OnMyEvent="@(e => { myevent(e); })"></mycomp>
@functions{
private void myevent(int value){
Console.WriteLine(value);
}
}
```
