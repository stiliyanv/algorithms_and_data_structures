# Merge Sort

**Merge Sort** is a sorting algorithm based on **divide and conquer** idea. It divides an unsorted list recursively in two halves until it can no more be divided and then merge the smaller lists into new list in sorted order.

For example: if you have `[7, 1, 5, 21, 3, 13]`, and you want to sort the array, **Merge Sort** will help you produce efficiently `[1, 3, 5, 7, 13, 21]`.

## Implementation

The implementation below uses **Recursion** and it is based on two steps: first **split** the arrays and then **merge** the arrays in sorted order.

```swift
// Split Arrays
func mergeSort(_ array: [Int]) -> [Int] {
    
    guard array.count > 1 else {
        return array
    }
    
    let leftArray = Array(array[0..<array.count/2])
    let rightArray = Array(array[array.count/2..<array.count])
    
    return merge(left: mergeSort(leftArray), right: mergeSort(rightArray))
}

// Merge Arrays
func merge(left: [Int], right: [Int]) -> [Int] {
    
    var mergedArray = [Int]()
    var left = left
    var right = right
    
    while left.count > 0 && right.count > 0 {
        if left.first! < right.first! {
            mergedArray.append(left.removeFirst())
        } else {
            mergedArray.append(right.removeFirst())
        }
    }
    
    return mergedArray + left + right
}
```

**Parameters**	
- `array`: array to be sorted.

**Returns**
- `array` with sorted elements.

## Usage

If you execute the following code:

```swift
let array1 = [27, 73, 18, 41, 99, 48, 84, 58, 71, 99]
let array2 = [17, 16, 14, 8, 8, 6, 12]
let array3 = [3, 3, 42, 33, 31, 39, 38, 12, 20, 23, 3, 8, 27, 24, 7]
let array4 = [17, 2, 23, 12, 21]
let array5 = [427, 123, 383, 690, 617, 352, 451, 524, 393, 517]

print(mergeSort(array1)) // [18, 27, 41, 48, 58, 71, 73, 84, 99, 99]
print(mergeSort(array2)) // [6, 8, 8, 12, 14, 16, 17]
print(mergeSort(array3)) // [3, 3, 3, 7, 8, 12, 20, 23, 24, 27, 31, 33, 38, 39, 42]
print(mergeSort(array4)) // [2, 12, 17, 21, 23]
print(mergeSort(array5)) // [123, 352, 383, 393, 427, 451, 517, 524, 617, 690]
```