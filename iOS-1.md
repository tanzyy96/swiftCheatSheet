# iOS-1 Tips, tricks and other notes!

## Content Page
- Outlet Collections
- First Responders


#### [1. Outlet Collections](https://www.youtube.com/watch?v=NEf0uUIKPIo&list=PLY1P2_piiWEaKH2ySjNl0QyVv_xroGvFR&index=6)
First, a quick syntax reminder: ! is used for force unwrapping optionals.  
New Syntax: ```as``` is used for upcasting and downcasting.  
    
Outlet Collections serve as an array of outlets that may want to share a similar function.
```swift
IBOutlet var optionButtons: [UIButton]!

override func viewDidLoad() {
	super.viewDidLoad()
	
	for button in optionButtons {
		onClick(sender:button)
	}
}

```
Here, ```onClick``` is a written function that takes the the button as the parameter and is shared amongst multiple buttons.

#### 2. First Responders
First Responder is the object that's currently receiving events. So if we want a view controller to trigger the keyboard immediately:
```swift
override func viewDidLoad() {
	super.viewDidLoad()
	textField.becomeFirstResponder()
}
```
This loads the keyboard immediately and brings the text field into focus. On the other hand, if we want to lose focus or hide the keyboard when, let's say on a button tap:
```swift
@IBAction func buttonTap(_ sender: Any) {
	textField.resignFirstResponder()
}
```
If you want to hide keyboard when user taps anywhere on the screen:
```swift
override func touchesBegan(_ touches: Set<UITouch>, with event: UIEvent?) {
	textField.resignFirstResponder()
}
```
If you want to hide keyboard when user hits return:
```swift
func textFieldShouldReturn(_ textField: UITextField) -> Bool {
	view.endEditing(true)
	return false
}
```
The boolean value determines if we want a line break enabled. This method requires a delegate, so
1. class ViewController: UITextFieldDelegate
2. textField.delegate = self (inside viewdidLoad() )
