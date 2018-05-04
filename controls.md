### Button
```
  <button onclick="@IncrementCount">increment</button>
   public int Items { get; set; }
        protected void IncrementCount()
        {
            Items++;
        }
```

### Select binding
```
 public enum Importance
    {
        None,
        Trivial,
        Regular,
        Important,
        Critical
    };
 public string SelectedOption { get; set; } = "Trivial";

   <select id="select-box" class="form-control" bind="SelectedOption">
                @foreach (var item in Enum.GetValues(typeof(WebApplication1.Pages.Importance)))
                {
                    <option value="@item.ToString()">@item.ToString()</option>

                }
    </select>
```            
### select onchange event
```
public Action<string> OnSomeEvent { get; set; }
public List<Customer> Customers { get; set; }
 <select class="form-control" onchange="@CustomerChanged">
                @foreach (var item in Customers)
                {
                    <option value="@item.Id">@item.Name</option>

                }
  </select>
 protected void CustomerChanged(UIChangeEventArgs e)
        {
            Console.WriteLine("Customer changed " + e.Value);
            OnSomeEvent?.Invoke(e.Value.ToString());
        }
```
### checkbox
```
<input type="checkbox" bind="@IsChecked" />chk1
<br />
<input type="checkbox" bind="@IsChecked" />chk2

<div style="@DivStyle()">this is some content, visible only when checkbox is checked</div>

@functions{

    public string DivStyle() {
        return (IsChecked) ? "display:block" : "display:none";     
    }
    public bool IsChecked { get; set; }

}
```
