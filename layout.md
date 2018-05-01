The layout component must implement ILayoutComponent. ILayoutComponent adds a Body property to the component that contains the content to be rendered inside the layout.
The layout component uses the Body property to specify where the body content should be rendered using the Razor syntax @Body.

```
@implements ILayoutComponent

<header>
    <h1>ERP Master 3000</h1>
    @Body

<footer>
    &copy; by @CopyrightMessage
</footer>
</header>

@functions {
    public string CopyrightMessage { get; set; }
    public RenderFragment Body { get; set; }
    ...
}
```

### Use a layout in a component
```
@layout MasterLayout

@page "/master-data"

<h2>Master Data Management</h2>
...
```

Every folder of a Blazor app can optionally contain a template file named _ViewImports.cshtml. The compiler includes the directives specified in the view imports file in all of the Razor templates in the same folder and recursively in all of its subfolders. Therefore, a _ViewImports.cshtml file containing @layout MainLayout ensures that all of the components in a folder use the MainLayout layout. There's no need to repeatedly add @layout to all of the *.cshtml files.

### Nested layouts
<br/>
Blazor apps can consist of nested layouts. A component can reference a layout which in turn references another layout. For example, nesting layouts can be used to reflect a multi-level menu structure.
