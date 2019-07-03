# swiftCheatSheet Part 1

CMD-RClick to access documentation quickly.  
- Variables
  - Strings
  - Boolean
  - Optionals
- Collections
  - Arrays
  - Dictionaries
  - Sets
  - Tuples
- Control Flow
  - If-else
  - For-loops
  - While-loops
  - Switch Statement
  - Guard Statement
  
  
## 1. Variables
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
#### 1.1 Strings
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

#### 1.2 Boolean
!, &&, ||
```swift
var val: Bool = true
true && true // true
false||true // true
```

#### 1.3 Optionals
Optional variables tell the compiler that the variable is either storing a value or storing nothing, which is really useful when you need placeholders for potentially unknown values.
```swift
var item: String?="pickaxe"
var age: Int?  // nil

// Forced unwrapping: unwrapping the optional without checking if it contains an actual variable. 
// Unwrapping a nil variable will cause error. This is discouraged.
print(item!)
```
When unwrapping an optional, Swift provides a neat way to check if the variable is nil:
```swift
// Original 
if age != nil {
  return age
} else {
  return "Error!"
}

// Shortcut
return age ?? "Error!"
```

## 2. Collections

#### 2.1 Arrays
Initialisation:
```swift
// Creating array
var myArray: [String] = ["a","b","c"]
var myArray: Array<String> = Array<String>() // empty
```
Array methods:
```swift
// Array methods
myArray.count
myArray.isEmpty

// Accessing array elements
myArray[1] // a
myArray[1] = "yes" // ["yes","b","c"]

// Adding elements
var newArray = ["yes","no"]
newArray.append["maybe"]
newArray +=["maybe not"]
newArray.insert("sometimes",at: 2)

// Special methods. The last 2 have return values while the first two do not.
newArray.reverse()
newArray.sort()

evenNewerArray = newArray.reversed()
evenNewerArray = newArray.sorted()

evenNewerArray.contains("yes")
```
```swift
// 2D array
var 2DArray: [[String]] = [
  ['One','Two','Three'],
  ['Four','Five','Six','Seven'],
  ['Eight']
]

var four = 2DArray[1][0]
```

#### 2.2 Dictionaries
Initialisation:
```swift
// Creating dict with String keys and Int values
var dic: [String:Int] = ["Jack":10, "Lily":15, "Jason":12]
```
Dictionary methods:
```swift
// Accessing and modification
var jackAge = dic["Jack"]
dic["Jack"] = 12 // modification
dic["Jamie"] = 16 // adding new key-value pair

// Dictionary methods (important!!)
let allKeys = [String](dic.keys)
let allValues = [Int](dic.values)

var oldValue = dic.updateValue(30, forKey:"Jason") // pops 12

// Removing value
dic["Lily"] = nil
var lilyAge = dic.removeValue(forKey:"Lily")
```
```swift
// Nested dictionaries
var big_dic = [
  "2A":[
    "Jack": 12,
    "Jill": 13
    ],
  "2B":[
    "Nick" : 10,
    "Nathon" : 3
    ]
]
```
 
#### 2.3 Sets
```swift
// Declaring type of element is unnecessary, but declaring Set is a must.
var mySet: Set<String> = ["a","b","c"]
```
```swift
// Inserting and removing
mySet.insert("d")
mySet.remove("a")

// Other common methods
mySet.contains("f")
mySet.sorted()
```
```swift
// Set operations
var newSet: Set = ["c","z"]
var common = mySet.intersection(newSet)
var diff = mySet.symmetricDifference(newSet)
var all = mySet.union(newSet)
var sub = mySet.subtracting(newSet)
```
 
#### 2.4 Tuples
``` swift
// Basic Tuple
var myTuple: (String, Int, Bool) - ("Jim",12,true)
myTuple.0
myTuple.1
myTuple.2
 ```
 ```swift
// Naming Tuples
var (name, age, asleep) = myTuple
name
age
asleep
 
var myTuple: (name: "Linda", age:15, asleep:false)
myTuple.asleep = true
```

## 3. Control Flow

#### 3.1 If-else

```swift
if age > 10 || age < 20 {
  print(age)
 }
```
Unwrapping Optionals
 ```swift
 let itemFound: String?
 let itemLost: String?
 
 if let item = itemFound, let item2 = itemLost {
  print(itemFound + itemLost)
 } else {
  print("Nil.")
 }
 ```
 #### 3.2 For loop
 ```swift
 for item in list {
  print(item)
 }
 
 for key in dic.keys {
  print(key)
 }
 
 for (key,value) in dic {
  print("\(key): \(value)")
 }
 ```
 For for-loops using range:
 ```swift
 for index in 1...10 {
  print(index)
 }
 
 for index in 1..<10 {
  print(index)
 }
 
 for item in list[2...] {
  print(item)
 }
 
 for item in list[..<list.count] {
  print(item)
 }
```

#### 3.3 While loop
```swift
while x > 5 {
  print(x)
}

// Repeat-while loop. Just like do-while
repeat {
  print(x)
 } while x > 5
```

#### 3.4 Switch statement
```swift
switch value {
case 1 :
  print("value is 1.")
case 2:
  print("value is 2.")
default:
  print("unknown value.")

// complex switching
switch(x,y) {
case (5,10): 
  print(x + y)
case (let n, let m) where n+m>12:
  print(n*m)
default:
  print("unknown")
}
```

#### 3.5 Guard statement
guard -> else. 
```swift
for item in list {
  guard item.count<5 else {
    print(item)
    continue
  }
}
```  



