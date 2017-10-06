---
title:  "Higher order functions in swift"
date:   2017-09-29
author: Pushpraj Chaudhary
categories:
- blog
tags:
- iOS
---

# **MAP**

```Map``` function returns  an array containing the results of transform function on each item.

Take a example to understand.

```swift
let itemArray = [1.1,2.2,3.3,4.4,5.5,6.6]
let square = itemArray.map({
  (value: Double) -> Double in
  return value * value
})
print(square)
```
// output = [1.21, 4.84, 10.88, 19.36, 30.25, 43.55]

The closure has a single argument: (value: Double) and returns a Double after performing operation. Also since map has a single argument which is a closure we do not need the ( and ) and

**in** keyword separates the argument from the body of the closure


***Shorthand syntax***
```swift
let square = itemArray.map{$0 * $0}
let square1 = itemArray.map {value in value * value}
```
With a single line closure we can even omit the return.

Map operation is not limited to Arrays you can use it with dictionary.
Mapping a dictionary over the collection has arguments that are a string and a Double from the types of the key and  a value on which operation is applied.

```swift
let itemDict = ["pushpraj":175.0,"sagar":165.0,”ankit":160.0]
let cmToMeter = itemDict.map { name, centi in centi / 100 }
print(cmToMeter)
```
// output = [1.75, 1.65, 1.6]

Map is also applicable on set, set can different type of values.

```swift
>let itemSet: Set = [4.5,6,8]
let resultingSet = itemSet.map {$0 * 3}
print(resultingSet)
```
//output = [24.0, 18.0, 13.5]

In above example there is set of Double and Integer value, after applying map function resulting set have Double type values.


# **REDUCE**

```Reduce``` function compute a set of values down to a single value.

Take a example to understand.

```swift
let itemArray = [10,20,30,40,50,60]*
let Sum = itemArray.reduce(0, { result, element in
    result + element
})
```
// output = 210


***Shorthand syntax***
```swift
let sum = itemArray.reduce(0){$0 + $1}
let sum1 = itemArray.reduce(0,+)
let sum2 = itemArray.reduce(0,{$0 + $1})
```
It takes two parameters: a starting value i.e 0 in parenthesis, and a function which takes a running total i.e $0 and an element of the array as parameters I.e $1 in above example, and returns a new running total in sum.

It also works with string using ```+``` operator.

```swift
let itemArray = ["abcd","pqrs","mnop"]
let resultString = itemArray.reduce(0, { result, element in
    result + element
})
print(resultString)
```
//output = abcdpqrsmnop


***Shorthand syntax***
```swift
let resultString = itemArray.reduce("", +)
```

Take another example, calculate the average.
```swift
let itemArray = [7.0, 3.0, 9.0]
let average = itemArray.reduce(0.0) { $0 + ($1 / Double(values.count)) }
print(average)
```
//output = 6.0

In above example, first one is the result of the previous reduction, i.e. $0. The second one is the current item that’s being reduced, i.e. the input for the current iteration, denoted with $1.

Lets see what happen in actual.

```swift
let itemArray = [7.0, 3.0, 9.0]
let average = itemArray.reduce(0.0, { (result:Double, item:Double) -> Double in
    return result + (item / Double(values.count))
})
print(average)
```
//output = 6.0

there are two closure parameters, result and item, both of type Double and an initial value 0.0. and return type Double.


# **FILTER**

```Filter``` function apply condition on each element, and returns a collection of items that satisfy a condition. It’s like a if-else statement for each element, and only getting the ones that meet the condition.

Take a example to understand.
```swift
let itemArray = [9, 19, 16, 16, 49, 333, 222]
let onlyOdd = itemArray.filter({ (value:Int) -> Bool in
    return value % 2 != 0
})
print(onlyOdd)
```

//output = [9, 19, 49, 333]


***Shorthand syntax***
```swift
let onlyOdd = itemArray.filter { $0 % 2 != 0 }
```

//output = [9, 19, 49, 333]

Closure should return a boolean value, indicated with -> Bool. It provide one item from the array, and returns the result of that item i.e "value % 2 != 0".


# **FLATMAP**

Flatten a collection of collections, it removes nil/optionals from a collection.
In simple word, when you need to transform the contents of an array of arrays, into a linear array then use ```FlatMap```.

Take a example to understand.
```swift
let arrayOfArrays = [[1,2,3],[4,5],[6,7,8]]
let flatArray = arrayOfArrays.flatMap { $0 }
print(flatArray)
```

//output = [1, 2, 3, 4, 5, 6, 7, 8]

```swift
let itemArray = [1, 2, nil, 3, 4, nil, nil, 5, 6]
let resultArray = itemArray.flatMap { $0 }
print(resultArray)
```

//output = [1, 2, 3, 4, 5, 6]

But ```FlatMap``` shows optional including a nil element if we have nil in any collection of collections

Lets take an example to see the powerful use of ```FlatMap```

##### Example with Filter

```swift
let arrayOfArrays = [[1,2,3],[4,5,6],[7,8,9]]
let onlyEven = arrayOfArrays.flatMap {
  intArray in intArray.filter { $0 % 2 == 0 }
}
```
//output = [2, 4, 6, 8]

In above example ```FlatMap``` return an array of even integers contained in a collection of integer arrays by applying a ```Filter``` to each item in the subarrays.


***Shorthand syntax***
```swift
let onlyEven = arrayOfArrays.flatMap { $0.filter { $0 % 2 == 0 } }
```

##### Example with Reduce
```swift
let sum = arrayOfArrays.flatMap { $0.reduce(0, +) }
```

//output = [6, 15, 24]

To understand how the above output come:[[1+2+3], [4+5+6], [7+8+9]] = [6, 15, 24]

In above example ```FlatMap``` returns the individual sum of each of the array of collection by applying reduce to each of the subarrays.


##### Example with Map
```swift
let resultingArray = collections.flatMap {
  intArray in intArray.map { $0 * 5 }
}
```
//output = [1, 4, 9, 16, 25, 36, 49, 64, 81]

Above returns a flatten array that contains the squares of each element of subarrays by applying a map to each subarray.


***Shorthand syntax***
```swift
let resultingArray = collections.flatMap { $0.map { $0 * 5 } }
```
