Button
```
  <button onclick="@IncrementCount">increment</button>
   public int Items { get; set; }
        protected void IncrementCount()
        {
            Items++;
        }
```

Select
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
onchange
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
