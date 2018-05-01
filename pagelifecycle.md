## Lifecycle methods
OnInitAsync and OnInit execute code after the component has been initialized. To perform an asynchronous operation, use OnInitAsync and use the await keyword:

```
protected override async Task OnInitAsync()
{
    await ...
}
```
For a synchronous operation, use OnInit:
```
protected override void OnInit()
{
    ...
}
```
OnParametersSetAsync and OnParametersSet are called when a component has received parameters from its parent and the values are assigned to properties. These methods are executed after OnInit during component initialization.
```
protected override async Task OnParametersSetAsync()
{
    await ...
}
protected override void OnParametersSet()
{
    ...
}
```
SetParameters can be overridden to execute code before parameters are set:
```
public override void SetParameters(ParameterCollection parameters)
{
    ...

    base.SetParameters(parameters);
}
```
If base.SetParameters isn't invoked, the custom code can interpret the incoming parameters value in any way required. For example, the incoming parameters aren't required to be assigned to the properties on the class.

ShouldRender can be overridden to suppress refreshing of the UI. If the implementation returns true, the UI is refreshed. Even if ShouldRender is overridden, the component is always initially rendered.
```
protected override bool ShouldRender()
{
    var renderUI = true;

    return renderUI;
}
```
