# swiftCheatSheet Part 3

- Swift Enumerations

## 7. Swift Enumerations
Swift enums allow you to put related values together into a group that you can use and access.  
Like switch statement, each value in an enum is considered a different case.

#### 7.1 Intro to Enums
Switch statements can use dot notation for referring to enums.
```swift
enum GameState {
  case Completed
  case Initializing
  case LoadingData
  case Restarting
}

// Alternative method
enum Gate State { case Completed, Initalizing, LoadingData }

var currentState = GameState.Completed // Completed

switch currentState {
case .Completed:
  print("Completed state.")
case .Initializing
  print("Initializing state.")
case .LoadingData
  print("Loading state.")
@unknown default:
  print("Unknwon game state.")
}
```
#### 7.2 Enums with Raw Value
```swift
// Raw values
enum NonPlayableCharacters:String {
  case Villager = "Common"
  case Blacksmoth = "Uncommon"
  case Merchant = "Rare"
}

var blacksmith = NonPlayableCharacters.Blacksmith
print(blacksmith.rawValue)  // "Uncommon"
```
We can use enums functions as well
```swift
enum PlayerState {
  case Alive
  case KO(level: Int)
  case Unknown(error:String)
  
  func evaluateCase() {
    switch self {
    case .Alive:
      print("Still kicking!")
    case .KO(let restartLevel):
      print("Sorry, back to level \(restartLevel)")
    case .Unknown(let message):
      print(message)
    default:
      print("Unknown state encountered...")
    }
  }
}

PlayerState.KO(level: 1).evaluateCase()   // "Sorry, back to level 1 for you"
```

## 8. Protocols
THIS IS JUST AN INTERFACE (Java). There's no limit of multi-inheritance.

```swift
// Declare a protocol
protocol Collectable {
  var name: String { get } // read-only
  var price: Int { get set } // read-write
  
  init(withName: String, startingPrice: Int)
  func collect() -> Bool
  
}

protocol Usable {
  func use() -> Void
}

// Protocol adoption
class ITem: Collectable, Usable {
  var name: String
  var price: Int
  
  required init(withName: String, startingPrice: Int) {
    // Init code
  }
  
  func collect() -> Bool {
    // function code
  }
  
  func use() {
    // function code
  }
}
```
