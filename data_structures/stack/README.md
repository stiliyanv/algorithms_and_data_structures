# Stack

**Stack** is a data structure that serves as a collection of elements, with a few principal operations:
- **push** - adds an element to the collection
- **pop** - removes the most recently added element that was not yet removed
- **peek** - give access to the top without modifying the stack

## Implementation

```swift
struct Stack<T> {
    private var array: [T] = []
    
    public var isEmpty: Bool {
        return array.isEmpty
    }
    
    public var count: Int {
        return array.count
    }
    
    public mutating func push(_ element: T) {
        array.append(element)
    }
    
    public mutating func pop() -> T? {
        array.popLast()
    }
    
    public func peek() -> T? {
        array.last
    }
}
```

## Usage

```swift
var myStack = Stack<Int>()

myStack.push(5) // [5]
myStack.push(4) // [5, 4]
myStack.push(7) // [5, 4, 7]
myStack.push(11) // [5, 4, 7, 11]
myStack.push(6) // [5, 4, 7, 11, 6]

myStack.count // 5
myStack.isEmpty // false

myStack.peek() // 6

myStack.pop() // 6
myStack.pop() // 11
myStack.pop() // 7
myStack.pop() // 4
myStack.pop() // 5

myStack.count // 0
myStack.isEmpty // true
```