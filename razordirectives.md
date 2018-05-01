Directive | Description
--------- | -----------
@functions | Adds a C# code block to a component.
@implements | Implements an interface for the generated component class. Often used to create a component layout by implementing ILayoutComponent.
@inherits | Provides full control of the class that the component inherits.
@inject | Enables service injection from the service container. For more information, see Dependency injection into views.
@layout | Specifies a layout component. Layout components are used to avoid code duplication and inconsistency.
@page | Specifies that the component should handle requests directly. The @page directive can be specified with a route and optional parameters. Unlike Razor Pages, the @page directive doesn't need to be the first directive at the top of the file.
@using | Adds the C# using directive to the generated component class.
@addTagHelper | Use @addTagHelper to use a component in a different assembly than the app's assembly.
