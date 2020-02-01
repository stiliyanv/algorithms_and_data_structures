# Queue

**Queue** is a data structure that serves as a collection of elements, with a few principal operations:
- **enqueue** - adds an element to the collection
- **dequeue** - removes the most oldest added element that was not yet removed
- **peek** -  gets the element at the front of the queue without removing it

## Implementation

```swift
struct Queue<T> {
    private var list = [T]()
    
    public var isEmpty: Bool {
        list.isEmpty
    }
    
    mutating func enqueue(_ element: T) {
        list.append(element)
    }
    
    mutating func dequeue() -> T? {
        if !list.isEmpty {
            return list.removeFirst()
        } else {
            return nil
        }
    }
    
    func peek() -> T? {
        if !list.isEmpty {
            return list[0]
        } else {
            return nil
        }
    }
}
```

## Usage

```swift
var myQueue = Queue<Int>()

myQueue.isEmpty // true

myQueue.enqueue(3) // [3]
myQueue.enqueue(11) // [3, 11]
myQueue.enqueue(9) // [3, 11, 9]
myQueue.enqueue(1) // [3, 11, 9, 1]
myQueue.enqueue(27) // [3, 11, 9, 1, 27]

myQueue.peek() // 3

myQueue.isEmpty // false

myQueue.dequeue() // [11, 9, 1, 27]
myQueue.dequeue() // [9, 1, 27]

myQueue.peek() // 9
```