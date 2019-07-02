# Table Views

A table view controller is used to add a table view and cells into an app.

### 0. Table View Controller VS Table View
Alternatively to using a table view controller, we can choose to add a table view and table view cells. Just remember, when we create the Cocoa Touch class file (.swift), we need to link the storyboard objects to the files by setting their class. *If we miss this step, we cannot link outlets to the swift file.*

### 1. Create a new Table View Controller/(TableView?)
To use a table view, we can either:
1. Create TableViewController & associated external class file
2. Create TableView & use existing ViewController.swift file 
  
**CMD-N and create a new Cocoa Touch class** to create a swift file for the controller. As for the storyboard, we can just add a table view controller object.

```swift
class TVC: UITableViewController {
//...
}
```

### 2. Working with Table View
When we are working in the storyboard, remember to link the table view controller to your custom class.  

A table view needs to know:
- number of cells
- number of sections?
- cell (which needs a reuse identifier)

We need 2 methods for inside our table view controller:
1. numberOfRows
2. cellForRowAt
```swift
class TVC: UITableViewController {
  
  override func viewDidLoad() {
    super.viewDidLoad()
  }
  
  override func tableView(_ tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
    // TODO: return stuff
    return data[section].count
  }
  
  override func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
    // TODO: return cell
    let cell = tableView.dequeueReusableCell(withIdentifier:"myCell", for: indexPath)
    return cell
  }
```
If we wish to have sections, we can use 3. numberOfSections
```swift
func numberOfSections(in tableView: UITableView) -> Int {
  // If this function is not configured, by default there will only be 1 section
  return data.count
}
```
DequeueReusableCell will be touched on later.  

#### 2.1 Attributes of Table View

**Reuse identifier** allows us to have different types of cell in a single table.  This can be added in the attributes inspector along with other things like checkmark.
  
**IndexPath** contains **row** and **section** numbers. Generally used for accessing nested arrays.

**Cell object casting:** If you have a swift file for cell configuration, remember to cast the cell to the appropriate class type using ```as! tableCell```.  

#### 2.2 tableView.dequeueReusableCell

This method is to help make our tableView loading more efficient by recycling the cells. Ensure withIdentifier parameter matches the **reuse identifier** that we gave the cell type originally.

#### 2.3 Loading Data into Table View
```swift
// ...
  class TVC: UITableViewController {
    
    // 0. For now, we will be loading data with this nested array
    let data: [[String]] = [["1","2","3"], ["a","b","c"]]
    
    // 1. Link this from the storyboard using Opt-drag
    @IBOutlet weak var tableView: UITableView!
    
    override func viewDidLaod() {
      super.DidLoad()
      
      // 2. Enter this, else you can also link this in the storyboard
      tableView.delegate = self
      tableView.datasource = self
    } 
```
We can use array access and indexPath to load our data dynamically.
```swift
func tableView(_ tableView: UITableView, cellForRowAt indexPath: indexPath: IndexPath) -> UITableViewCell {
	// Return a cell object
	let cell = tableView.dequeueReusableCell(withIdentifier: "myCell", for: indexPath) as! myCell
	cell.label.text = data[0][indexPath.row]
	return cell
}

func tableView(_ tableView UITableView, numberOfRowsInSection section: Int) -> Int {
	// Return number of rows
	return data[section].count
}
```
#### 2.4 Selecting rows
```swift 
func tableView(_ tableView: UITableView, didSelectRowAt indextPath: IndexPath) {
	// Certain function
}
```

### 3. Navigation Controller
We can embed table view controller inside a navigation controller. This helps us navigate to another page when we click on a cell.
    
    
    
    
    
    
    
