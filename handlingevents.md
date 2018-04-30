Events

onclick
```
<button onclick="@IncrementCount">increment</button>
 public int Items { get; set; }
        protected void IncrementCount()
        {
            Items++;
        }
```       
Invoking actions
```
 public Action OnDismiss { get; set; }
  void Dismiss()
    {        
        OnDismiss?.Invoke();     
    }
