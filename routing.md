Multiple route templates can be applied to a component. The following component responds to requests for /BlazorRoute and /DifferentBlazorRoute:

Optional parameters aren't supported
```=
@page "/BlazorRoute"
@page "/DifferentBlazorRoute"

<h1>Blazor routing</h1>
```
### Route parameters
```
@page "/RouteParameter"
@page "/RouteParameter/{text}"

<h1>Blazor is @Text!</h1>

@functions {
    public string Text { get; set; } = "fantastic";
}
```

### Typed route parameters
```
@page "/RouteParameter"
@page "/RouteParameter/{Text:string}"
@page "/RouteParameter/{Val:int}"
<h1>Blazor is @Text!</h1>

@functions {
    public string Text { get; set; };
    public int Val { get; set; };
}
```
