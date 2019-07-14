# AlertControllers

### 1. UIAlertController
To build an alert:
1. UIAlertController()
2. addAction
3. present(ac,animated: true)

```swift
let ac = UIAlertController(title: "FINAL", message: "Final Score \(score)", preferredStyle: .alert)
ac.addAction(UIAlertAction(title:"Continue", style: .default, handler: askQuestion))
present(ac, animated: true)
```
UIAlertController is the initial popup. You can set a title, a message and it's preferred style. For style, we can either go for ```.alert``` or ```.actionsheet```, the latter which allows for option choosing.
  
UIAlertAction is for providing buttons, which also comes with its set style ```.default```, ```.destructive``` and ```.cancel```. The handler refers to a function that gets triggered when you click the alert actio button.

present() is simply when you want to present your alert.

### 2. addTextField
```swift
    @objc func filterPetitions() {
        let ac = UIAlertController(title: "Filter", message: "Searching for certain petitions?", preferredStyle: .alert)
        ac.addTextField()
        
        let submitAction = UIAlertAction(title: "Submit", style: .default) { [weak self, weak ac] action in
            guard let answer = ac?.textFields?[0].text else { return }
            self?.filter(answer)
        }
        
        ac.addAction(submitAction)
        present(ac, animated: true)
```
I still don't quite get the closure on line 26, but in due time! filter() is another function inside the view controller. The \[0] after ```textFields?``` is because the return object is actually a dictionary of things like frame, text, gestureRecognizers etc. We only want to access text!
