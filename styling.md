### Adding classes

```
 <div TagName="div" class="@CssClass()"></div>
 private string CssClass()
        => isTest ? "alert-dismissible" : string.Empty);
```
### setting class property on element 
```
<div class=@(collapseNavMenu ? "collapse" : null) onclick=@ToggleNavMenu>
@functions {
    bool collapseNavMenu = true;

    void ToggleNavMenu()
    {
        collapseNavMenu = !collapseNavMenu;
    }
}
```
