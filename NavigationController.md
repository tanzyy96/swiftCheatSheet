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
