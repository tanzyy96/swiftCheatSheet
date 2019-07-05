# Navigation Controller

### 1. Introduction to Navigation View

Navigation Controllers allow us to have a systemetic iOS UX interface design that simplifies transitions between views.
  
1. Select VC and embed in Navigation Controller
2. To customise titles
  - For direct VC, simply click the Navigation bar to edit text
  - For indirect VC, click the View Controller button and edit the title
  - We can prefer large titles; if we want to set certain views to NOT have large titles:
  ```swift
  override func viewDidLoad() {
    super.viewDidLoad()
    self.navigationItem.largeTitleDisplayMode = .never
  }
 ```

### 2. Passing Data inside Navigation Controller
To pass data from one view controller to another, we have 3 main tasks:
1. Set up a property inside detailViewController (aka the secondary VC) to receive the data
2. Load the detail view controller from our storyboard
3. Set the detailViewController.property to receive the data
4. Push the new detailViewController

In the example, we are doing it with a didSelectRow, but it works for button as well.
```swift
override func tableView(_ tableView: UITableView, didSelectRowAt indexPath: IndexPath) {
  // 2.
  if let vc = storyboard?.instantiateViewController(withIdentifier: "detailVC") as? DetailViewController {
    // 3. Set property
    vc.selectedImage = pictures[indexPath.row]
    // 4. Push it onto Navigation controller
    navigationController?.pushViewController(vc, animation: true)
  }
}
```
