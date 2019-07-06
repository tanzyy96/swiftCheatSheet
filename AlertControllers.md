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
