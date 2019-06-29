# Table Views
Most of this content is from raywenderlich.com

A table view controller is used to add a table view and cells into an app.

#### 1. Create a new Table View Controller
We need a table view controller, both inside the storyboard as well as the Cocoa Touch class file.  
**CMD-N and create a new Cocoa Touch class** to create a swift file for the controller. As for the storyboard, we can just add a table view controller object.
```swift
class TVC: UITableViewController {
//...
}
```

When we are working in the storyboard, remember to link the table view controller to your custom class.  

A table view needs to know:
- number of cells
- number of sections?
- cell (which needs a reuse identifier)

Reuse identifier allows us to have different cells in a single table.  This can be added in the attributes inspector
along with other things like checkmark.

We need 2 methods for inside our table view controller:
