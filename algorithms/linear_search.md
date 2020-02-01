# Linear Search

**Linear Search** is a search algorithm for finding an element within an array. It sequentially checks each element of the array until it finds an element that matches the target value.

For example: if you have the following array: `[0, 1, 3, 4, 5, 8, 9, 10, 12, 15, 17, 19, 20, 23, 27, 28, 31]`, and you want to find the index of the value `9`, **Linear Search** will help you finding that its index is `6`.

## Implementation

```swift
func linearSearch(searchValue: Int, array: [Int]) -> Int? {
    
    for (index, number) in array.enumerated() {
        if searchValue == number {
            return index
        }
    }
    
    return -1
}
```

> Note: The above code is designed to search for `Int` in an array of integers, but this could be adjusted for different data types.

**Parameters**
- `searchValue`: An element to search for in the collection.
- `array`: Array, where the element will be searched.

**Returns**
- The index where element is found. If element is not found in the collection, returns `-1`.

## Usage

```swift
var array = [0, 1, 3, 4, 5, 8, 9, 10, 12, 15, 17, 19, 20, 23, 27, 28, 31]

print(linearSearch(searchValue: 9, array: array)!) // 6
print(linearSearch(searchValue: 14, array: array)!) // -1
print(linearSearch(searchValue: 17, array: array)!) // 10
print(linearSearch(searchValue: 31, array: array)!) // 16
print(linearSearch(searchValue: 99, array: array)!) // -1

```