# Using Multiple Views

### 1. Tabbed App

A tabbed app works like many of our modern apps today, where we have a bottom bar with multiple tabs to access different storyboards. For now, we know we can do several things:

1. Add more view controllers ( aka tabs )
2. Customise tab icons and badges ( aka notification count )

To add a new View Controller, first add the object from the object library. Then, we can link the storyboard through the + button via the ```Connections Inspector``` under ```Triggered Segues```. Just drag and drop on the new View Controller. The name can be custoimized by clicking on the tab bar in the respective view controller and changing the title of the ```Bar Item```.

### 2. Transition between Views

When we want to transit from one View Controller to another, we **R-CLICK & drag** to the new VC via a button. We can then select one of the Action Segue methods.

#### 2.1 Select Row -> Transition to New View

1. Connect View Controller to DetailController( aka new view ) via R-Click & drag from the bar above the view.
2. Set the Segue Method.
3. Set a segue identifier.
4a. In ViewController.swift, customize ```didSelectRowAt``` function to have ```self.performSegue(withIdentifier: "showDetail", sender: nil)
4b. If we wish to pass data, make sure we have the data in a variable here e.g.
```swift
selectedText = data[0][indexPath.row]
```
5. In our DetailController aka receiver, create a optional var to receive the data e.g.
```swift
var detailText: String?
```
**6. Sending Method: We use ```prepare``` method to send the data from inside ViewController.swift**
```swift
override func prepare(for segue: UIStoryboardSegue, sender: Any?) {
  let detail = segue.destination as! DetailController
  detail.detailText = selectedText
}
```
This is where we attach the data to the segue.

**7. Receiving Method: We use ```viewWillAppear``` to receive the data from inside DetailController.swift**
```swift
override func viewWillAppear(_ animated: Bool) {
  super.viewWillAppear(animated)
  if let t = detailText {
    label.text = t
  }
}
```
