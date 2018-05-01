## Events

The list of supported event arguments is:

UIEventArgs
UIChangeEventArgs
UIKeyboardEventArgs
UIMouseEventArgs

### onclick
```
<button onclick="@IncrementCount">increment</button>
 public int Items { get; set; }
        protected void IncrementCount()
        {
            Items++;
        }
```   

### conditional event handling
```
 <input type="checkbox" bind="@handleClicks" />
<button onclick="@((handleClicks ? (Action)IncrementCount : null))">Click me</button>
 @functions {
    int currentCount = 0;
    bool handleClicks = true;

    void IncrementCount()
    {
        currentCount++;
    }

    public void Reset()
    {
        currentCount = 0;
        StateHasChanged();
    }
}
```
### Invoking actions
```
 public Action OnDismiss { get; set; }
  void Dismiss()
    {        
        OnDismiss?.Invoke();     
    }
