# swiftCheatSheet

CMD-RClick to access documentation quickly.
## 1.1 Variables
Use : for assigning types  
Use ```let``` for constants and ```var``` for variables
```swift
// Swift allows for implicit and explicit type inference
var myVar: String = "There it is!"

// Constants
let cons = 5

// Type conversion
var value = 5.36
value_int = Int(value) // 5
value_string = String(value)
```
#### 1.1.1 Strings
This is called string interpolation. Accepts numbers, booleans and so on.
```swift
var sentence1 = "Yes" + " there"
var sentence1 += "is!"

let name = "Tanzy", age = "5"
var sentence2 = "Hi my name is \(name) and my age is \(age)."
```

String methods:
```swift
Bool i = sentence2.isEmpty  // false
var j = sentence2.count
bool k = sentence.contains("i") // true, case-sensitive

sentence2.append(" Thanks.")
sentence2.remove(index) // also have removeFirst, removeLast, removeAll
sentence.split(' ') // returns array like Python
```

#### 1.1.2 Boolean
!, &&, ||
```swift
var val: Bool = true
true && true // true
false||true // true
```

#### 1.1.3 Optionals
Optional variables tell the compiler that the variable is either storing a value or storing nothing, which is really useful when you need placeholders for potentially unknown values.
```swift
var item: String?="pickaxe"
var age: Int?  // nil

// Forced unwrapping: unwrapping the optional without checking if it contains an actual variable. 
// Unwrapping a nil variable will cause error. This is discouraged.
print(item!)


