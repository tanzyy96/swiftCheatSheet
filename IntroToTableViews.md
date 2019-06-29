# Table Views
Most of this content is from raywenderlich.com

A table view controller is used to add a table view and cells into an app.

### 0. Table View Controller VS Table View
Alternatively to using a table view controller, we can choose to add a table view and table view cells. Just remember, when we create the Cocoa Touch class file (.swift), we need to link the storyboard objects to the files by setting their class. *If we miss this step, we cannot link outlets to the swift file.*

### 1. Create a new Table View Controller
We need a table view controller, both inside the storyboard as well as the Cocoa Touch class file.  
**CMD-N and create a new Cocoa Touch class** to create a swift file for the controller. As for the storyboard, we can just add a table view controller object.
```swift
class TVC: UITableViewController {
//...
}
```

### 2. Working with the Table View Controller
When we are working in the storyboard, remember to link the table view controller to your custom class.  

A table view needs to know:
- number of cells
- number of sections?
- cell (which needs a reuse identifier)

**Reuse identifier** allows us to have different types of cell in a single table.  This can be added in the attributes inspector
along with other things like checkmark.

We need 2 methods for inside our table view controller:
```swift
class TVC: UITableViewController {
  
  override func viewDidLoad() {
    super.viewDidLoad()
  }
  
  override func tableView(_ tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
    // TODO: return stuff
    return 1
  }
  
  override func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
    // TODO: return cell
    let cell = tableView.dequeueReusableCell(withIdentifier:"myCell", for: indexPath)
    return cell
  }
```
If you have a swift file for cell configuration, remember to cast the cell to the appropriate class type using ```as! tableCell```.  

Alternatively we can create an **extension** to house our 2 functions for tableView.
```swift
extension tableViewController: UITableViewDataSource, UITableViewDelegate {
  // insert 2 functions here
}
```
This extension acts as an inheritance from **protocols** for us to override these existing methods. If we are going to use extension, we need to include the following:
```swift
// ...
  class TVC: UITableViewController {
    
    // 1. Link this from the storyboard using Opt-drag
    @IBOutlet weak var tableView: UITableView!
    
    override func viewDidLaod() {
      super.DidLoad()
      
      // 2. Enter this, else you can also link this in the storyboard
      tableView.delegate = self
      tableView.datasource = self

### 3. IndexPaths
IndexPath contains **row** and **section** numbers. Generally used for accessing nested arrays.

### 4. Navigation Controller
We can embed table view controller inside a navigation controller. This helps us navigate to another page when we click on a cell.
    
    
    
    
    
    
    
