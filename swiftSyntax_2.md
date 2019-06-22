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
Similar to lambda/arrow functions.
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
Closure methods
```swift
var highScores = [123,0,2]

// Existing function with closures
var ascendingSort = highScores.sorted { (firstValue, secondValue) -> Bool in
  return firstValue < secondValue
}

// Using custom closures with functions
// This function takes a closure as a parameter
// The closure is declared to take in a string array as parameter and has no output
func myFunction(closure: ([String]) -> Void) {
  closure(highScores)
}

// We then declare the contents of the closure & function later on
myFunction { (items) in
  for item in items {
    print(item)
  }
}
```
This is done when we want to declare the method before deciding its function. We are able to access the closure content from **outside the function.**

Using closures as an output
```swift
func myFunction(list:[String]) -> ()-> Void {  // Returns closure as output
  let r: () -> Void = {
    for item in list {
      print(item)
    }
  }
  return r
}

// Think of it as a blueprint for creating functions
var closureReturn = myFunction(aList) 
closureReturn()
```
By using typealiasing, we can simplify closures.
```swift
// Type Alias
typealias person = (name: String, age: Int, gender: String)
var Bob: person = ("Bob", 24, "Male")

// Using typealiasing inside function
func gotOlder(p:person)-> person {
  let newp: person = (p.name, p.age+10, p.gender)
  return p
}

var newBob = gotOlder(p:Bob)

// Type alias as a function parameter
typealias arrayClosure = ([String])-> Void)

func myFunction(list:arrayClosure) {
  // insert code here
}
```

## 5. Objects

#### 5.1 Standard Object structure
```swift
class Adventurer {
  var name: String
  let maxHealth: Int
  var specialMove: String?
  
  int(name: String, maxHP: Int) {
    self.name = name
    self.maxHealth = maxHP
  }
```
#### 5.2 Convenience init
```swift
// Convenience init uses original init
  convenience init(name: String) {
    self.init(name:name,maxHP:100)
  }
```
#### 5.3 Object methods
```swift
  func printStats() {
    print("Character Name: \(self.name)\nMax HP: \(self.maxHP)")
  }
```
Classes use referencing, hence if we include ```var player1 = player2```, we actually have a single object instance only, but 2 references to the same object. Hence, changes to either references will change the same object.

#### 5.4 Access Control  
Swift, like Java, provides access control such as public, fileprivate .etc   
Swift has ```get``` and ```set``` keywords to replace manual get, set methods. Great!
```swift
fileprivate var health: Int
var Health: Int {
  get { return health }
  set {
    if (newValue <= 100) {
      health = newValue
    }
  }
}
```
So accessing these methods from outside:
```swift
var hp = Bob.Health     // Get Method
Bob.Health = 50         // Set Method
```

#### 5.4 Static/ Class Variables
Both variables belong to the class, not object instances.  
E.G. ```Adventurer.maxPopulation```
```swift
// Static variables are fixed 
static var maxPopulation = 10

// Class variables can be overwritten in subclasses
class var race: String {
  return "Human"
}
```

#### 5.5 Subclass
There is also method overriding, but it's intuitive so I won't cover it here.
```swift
class Warrior: Adventurer {
  var classDesc: String
  
  override class var race: String {
    return "Warrior"
  }
  
  init(name: String, desc: String) {
    self.classDesc = desc               // IMPORTANT: Subclass methods need to be declared before super init
    super.init(name: name, maxHP: 150)
  }
}
```

## 6. Struct
Structs are basic classes that do not require inheritance and the sorts.  
Structs use pass by value (aka makes copies) instead of referencing. Refer to class section for referencing.

#### 6.1 Intro
```swift
struct Box {
  let color: String
  
  /*
  init(color: String) {
    self.color = color
  }
  */
  
  mutating func changeColor(c:String) {
    self.color = c
  }
}

// Structs come with a default init method
// Introducing a new init method will disable default init method
var redBox = Box(color: "Red")
```

#### 6.2 Optional Chaining
Optional chaining is like: if this optional x exists, check its property y
```swift
struct Item {
  var desc: String
  var previousOwner: Owner?
}

struct Owner {
  var name: String
}

// Creating optional chain
var rareDagger = Item(desc: "Dark markings.", previousOwner: nil)

if let owner = rareDagger.previousOwner?.name {
  print("This item used to be owned by \(owner)")
} else {
  print("Unknown item history.")
}
```










