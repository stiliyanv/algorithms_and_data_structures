# Binary Search

**Binary Search** is a search algorithm that finds the position of a target value within a **sorted array**.

For example: if you have the following array: `[0, 1, 3, 4, 5, 8, 9, 10, 12, 15, 17, 19, 20, 23, 27, 28, 31]`, and you want to find the index of the value `9`, **Binary Search** will help you finding that its index is `6`.

## Implementation

```swift
func binarySearch(searchValue: Int, array: [Int]) -> Int? {
    
    var leftIndex = 0
    var rightIndex = array.count - 1
    
    while leftIndex <= rightIndex {
        
        let middleIndex = (leftIndex + rightIndex) / 2
        let middleValue = array[middleIndex]
        
        if middleValue == searchValue {
            return middleIndex
        } else if middleValue > searchValue {
            rightIndex = middleIndex - 1
        } else if middleValue < searchValue {
            leftIndex = middleIndex + 1
        }
    }
    
    return -1
}
```

**Parameters**
- `searchValue`: An element to search for in the collection.
- `array`: Sorted array, where the element will be searched.

**Returns**
- The index where element is found. If element is not found in the collection, returns `-1`.

## Usage

```swift
var array = [0, 1, 3, 4, 5, 8, 9, 10, 12, 15, 17, 19, 20, 23, 27, 28, 31]

print(binarySearch(searchValue: 9, array: array)!)  // 6
print(binarySearch(searchValue: 14, array: array)!) // -1
print(binarySearch(searchValue: 17, array: array)!) // 10
print(binarySearch(searchValue: 31, array: array)!) // 16
print(binarySearch(searchValue: 99, array: array)!) // -1

```