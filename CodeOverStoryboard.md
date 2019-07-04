# CodeOverStoryboard!!!
Here is where we see how we can do things in storyboard usiong pure Swift code! This is commonly tested in job interviews.

1. Adding a label
2. AutoLayout
3. Font

#### 1. Adding a label
```swift
override func viewDidLoad() {
	super.viewDidLoad()
	// 1. Create the label object
	let label = UILabel()
	
	// 2. Create a rectangle frame for the label object
	label.frame = CGRect(x: 50, y: 50, width: 200, height: 50)
	label.text = "Hello World!"
	
	// 3. Add this label object to the main view as a subview
	view.addSubview(label)
}
```
#### 2. Autolayout
```swift
override func viewDidLoad() {
	super.viewDidLoad()
	// 1. Create the label object
	let label = UILabel()
	
	// 2. Disable auto constraints
	label.translatesAutoresizingMaskIntoConstraints = false
	label.text = "Hello World!"
	
	// 3. Add this label object to the main view as a subview
	view.addSubview(label)
	
	// 4. Add constraints and make them active
	label.leadingAnchor.constraint(equalTo: view.leadingAnchor, constant: 50).isActive = true
	label.trailingAnchor.constraint(equalTo: view.trailingAnchor, constant: -50).isActive = true
	label.topAnchor.constraint(equalTo: view.safeAreaLayoutGuide.topAnchor, constant: 100).isActive = true
	label.heightAnchor.constraint(equalToConstant: 150).isActive = true
}
```
#### 3. Font
```swift
label.font = UIFont.systemFont(ofSize: 150) // 1. Set Font size
label.minimumScaleFactor = 0.2							// 2. 0.2 means font is minmally 30
label.adjustsFontSizeToFitWidth = true			// 3. Allows auto resizing of font
```
The nice thing about this font is that it resizes as we change from landscape to portait.
