# Linked List

A **Linked List** is a collection of nodes, each node containing data, and pointers to the previous and next node in the collection. This differs from say, an array, in that a Linked List’s data is not ordered by a node’s physical placement in memory but instead which other nodes it is connected to.

> The following implementation is of **doubly linked list**. The main difference between **singly linked list** and **doubly linked list** is the ability to traverse. In a **single linked list**, node only points towards next node, and there is no pointer to previous node, which means you can not traverse back on a singly linked list.

### The code

```swift
// Node of a linked list
public class Node<T> {
    
    var value: T
    var next: Node<T>?
    weak var previous: Node<T>?
    
    init(value: T) {
        self.value = value
    }
}

// Linked list
public class LinkedList<T> {
    
    private var head: Node<T>?
    private var tail: Node<T>?
    
    public var isEmpty: Bool {
        return head == nil
    }
    
    public var first: Node<T>? {
        return head
    }
    
    public var last: Node<T>? {
        return tail
    }
    
    public func append(value: T) {
        let newNode = Node(value: value)
        if let tailNode = tail {
            newNode.previous = tailNode
            tailNode.next = newNode
        } else {
            head = newNode
        }
        tail = newNode
    }
    
    public func nodeAt(index: Int) -> Node<T>? {
        if index >= 0 {
            var node = head
            var i = index
            while node != nil {
                if i == 0 {
                    return node
                }
                i -= 1
                node = node!.next
            }
        }
        return nil
    }
    
    public func remove(node: Node<T>) -> T {
        let prev = node.previous
        let next = node.next
        
        if let prev = prev {
            prev.next = next
        } else {
            head = next
        }
        next?.previous = prev
        
        if next == nil {
            tail = prev
        }
        
        node.previous = nil
        node.next = nil
        
        return node.value
    }
    
    public var description: String {
        var text = "["
        var node = head
        
        while node != nil {
            text += "\(node!.value)"
            node = node!.next
            if node != nil {
                text += ", "
            }
        }
        
        return text + "]"
    }
    
    public var count: Int {
        guard var node = head else {
            return 0
        }
        
        var count = 1
        while let next = node.next {
            node = next
            count += 1
        }
        return count
    }
    
    public func removeAll() {
        head = nil
        tail = nil
    }
}
```

**Example**

```swift
let numbers = LinkedList<Int>()

numbers.append(value: 2)
numbers.append(value: 4)
numbers.append(value: 6)

print(numbers.isEmpty)     // false
print(numbers.description) // [2, 4, 6]
print(numbers.count)       // 3

numbers.append(value: 8)
numbers.append(value: 10)
numbers.append(value: 12)

numbers.remove(node: numbers.nodeAt(index: 1)!)

print(numbers.description) // [2, 6, 8, 10, 12]

print(numbers.nodeAt(index: 0)!.value) // 2
print(numbers.nodeAt(index: 3)!.value) // 10

numbers.removeAll()

print(numbers.isEmpty)     // true
print(numbers.description) // []
print(numbers.count)       // 0
```

### Resources

- [Linked list - Wikipedia](https://en.wikipedia.org/wiki/Linked_list)
- [Doubly linked list - Wikipedia](https://en.wikipedia.org/wiki/Doubly_linked_list)