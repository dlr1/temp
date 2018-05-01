To call JavaScript libraries or custom JavaScript/TypeScript code from .NET, the current approach is to register a named function with JavaScript/TypeScript. Place the registerFunction call in the index.html file or a JavaScript file (*.js) loaded by the index.html file. Place the inline JavaScript or <script> tag below <script type="blazor-boot"></script>, and the JavaScript/TypeScript loads at the correct time and only executes once.
```
Blazor.registerFunction('doPrompt', function(message) {
    return prompt(message);
});
```
Wrap the named function for calls from .NET:
```
public static bool DoPrompt(string message)
{
    return RegisteredFunction.Invoke<bool>("doPrompt", message);
}
```
