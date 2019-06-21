# swiftCheatSheet

## 4. Functions

#### 4.1 Intro to Functions

```swift
func myFunction() -> String{
  print("yes")
  return("yes")
}

func returnInt(val:Int)->String{
  return val*2
}
```

#### 4.2 Overloading
Allows for polymorphism.
```swift
func add() {
  print("Adding...")
}

func add(num:Int) {
  print("Adding \(num)")
}
```

#### 4.3 Optional Return
```swift
// Optional return value
func setup() -> Bool? {
  return nil
}

if let checkOptional = setup() {
  print("Initialised value.")
} else {
  print("Nil value."
}
```
Getting multiple return values.
```swift
// Multiple return values
func setupMulti(val:Int)->(r1:Int, r2: String) {
  return (val, "Initialised.")
}

// Accessing multiple return values from one variable
var setupVar = setupMulti(5)
setupVar.r1 // 5
setupVar.r2 // "Initialised."
```
```swift
// Default values
func setup(val:Int = 3) {
  return val+2
}

var myValue = setuo() // default value used, returns 5
```

#### 4.4 Using Functions as Parameters *
Every function has a type, or unique signature. Function types can be used in Swift like any other type,
such as strings or integers.  

```swift

// Function types; Type Signature: (Int) -> Int
func times4(val:Int)->Int {
  return val*4
}

// Function as Parameter
func calculate(val:Int, bonusVal: (Int)->Int) {
  let sum = bonusVal(val)
}

calculate(10, times4) // using function as variable. 
```

#### 4.5 Closures
Similar to lambda expressions.
```swift
// Holds function type as return value
var closure: () -> () = {}
```
First () for parameter type, second () for output type, {} for innerworkings.
```swift
// Initializing closures
var compute: (Int) -> Int = { (base:Int) -> Int in
  return base * 4
}

// Simple closure formatting
var compute: (Int) -> Int = { base in
  return base * 4
}
```






