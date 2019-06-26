# iOS-1 Tips, tricks and other notes!

## Content Page
- Outlet Collections


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

