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

#### 4. Button
```swift
// 1. Initialise button
let button = UIButton()
button.frame = CGRect(x: 10, y: 200, width: 100, height: 30)

// 2. Default title color is white!
button.setTitleColor(.blue, for: .normal)
button.setTitle("Tap Here", for: .normal)
button.addTarget(self, action: #selector(buttonWasTapped), for: .touchUpInside)

// 3. Button Function
@obj func buttonWasTapped() {
	label.text = "Hello!"
}
```

#### 5. Table View
```swift
class AppDelegate: UIResponder, UIApplicationDelegate {
	// 1. Root object that contains the view 
	var window: UIWindow?
	
	func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions:
	[UIApplication.LaunchOptionsKey: Any]?) -> Bool {
		// 2. Insert navigation controller with table view inside
		let table = TableViewController()
		let navigation = UINavigationController(rootViewController: table)
		window?.rootViewController = navigation
		
		return true
	}
```
```swift
class TableViewController: UITableViewContoller {
	
	let cellID = "cell"
	let detailView = ViewController()
	
	override func viewDidLoad() {
		super.viewDidLoad()
		
		...
		// 1. Register tableViewCell with reuse identifier
		tableView.register(UITableViewCell.self, forCellReuseIdentifier: cellID)
	}
	
	...
	
	override func tableView(_ tableView: UITableView, didSelectRowAt indexPath: IndexPath) {
		// 2. This is for pushing selected row data to the DetailViewController
		let selectedItem = items[indexPath.row]
		detailView.textView.text = selectedItem
		navigationController?,pushViewController(detailView, animated: true)
	}
```
```swift
class ViewController: UIViewController {
	let textView = UITextView()
	...
	override func viewDidLoad() {
		super.viewdidLoad()
		...
		layoutTextView()
	}
	
	func layoutTextView() {
		view.addSubview(textView)
		textView.translatesAutoresizingMaskIntoConstraints = false
		... constraint stuff...
	}
```









