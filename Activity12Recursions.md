# Activity 12 Recursions

## 1. The following function prints every other number from a low number to a high number. For example, if low is 0 and high is 10, it would print:
```
0
2
4
6
8
10
```

## Identify the base case in the function:
```
def print_every_other(low, high) 
    return if low > high
    puts low
    print_every_other(low + 2, high)
end
```
The base case is the condition that stops the function. In this case it's the statement "return if low > high". This allows the loop to exit once method function has been called with a low value greater than its high value.

## 2. My kid was playing with my computer and changed my factorial function so that it computes factorial based on (n - 2) instead of (n - 1). Predict what will happen when we run factorial(10) using this function:
```
def factorial(n)
    return 1 if n == 1
    return n * factorial(n - 2)
end
```

If we were to pass this function a value of 10 we would first see:
```
10 * factorial(8)
10 * 8 * factorial (6)
```
But eventually we would see:

```
10 * 8 * 6 * 4 * 2 * factorial(0)
...
```
We would go past the base case where factorial(1) would return a value of 1. This would result in an eventual stack overflow.

## 3. Following is a function in which we pass in two numbers called low and high. The function returns the sum of all the numbers from low to high. For example, if low is 1, and high is 10, the function will return the sum of all numbers from 1 to 10, which is 55. However, our code is missing the base case, and will run indefinitely! Fix the code by adding the correct base case:
```
def sum(low, high)
    return high + sum(low, high - 1)
end
```
We would want to add a base case where high and low are equal so that high doesn't continue to become values lesser than low. Once low reaches high we only want to add the value of low.

```
def sum(low, high)
  return low if(low == high)
  return high + sum(low, high - 1)
end
```
## 4. Here is an array containing both numbers as well as other arrays, which in turn contain numbers and arrays:
```
array=[ 1, 
        2, 
        3,
        [4, 5, 6],
        7,
        [8,
          [9, 10, 11,
            [12, 13, 14]
          ] 
        ],
        [15, 16, 17, 18, 19,
          [20, 21, 22,
            [23, 24, 25,
              [26, 27, 29]
            ], 30, 31 
          ], 32
        ], 33 
      ]
```
## Write a recursive function that prints all the numbers (and just numbers).

```
def printNumbers(array, index)
  //base case: end of array
  return array if (index == length(arr)

  if (array[index] is an array)
  {
    printNumbers(array[index], 0)
  }
  

```

``` C++

#include <iostream>
#include <vector>

// Node structure to represent either an integer or a nested array
struct Node {
    //fields
    bool isNumber;
    int value;
    std::vector<Node> children;

    // Constructor for a number
    Node(int val) : isNumber(true), value(val) {}

    // Constructor for a nested array
    Node(const std::vector<Node>& elems) : isNumber(false), children(elems) {}

};

// Print number function
void printNumbers(const std::vector<Node>& arr, std::size_t index) {
    //Base case: when the index has reached the size of the array
    if (index == arr.size()) {
        return;
    }

    //If current element is an integer, print
    if (arr[index].isNumber) {
        std::cout << arr[index].value << std::endl;
    }
    
    // If element is an array, recurse into
    else {
        printNumbers(arr[index].children, 0);
    }

    //Recurse the function and advance the index 
    printNumbers(arr, index + 1);
    
}

int main() {
    std::vector<Node> array = {
        Node(1),
        Node(2),
        Node(3),
        Node({Node(4), Node(5), Node(6)}),
        Node(7),
        Node({
            Node(8),
            Node({
                Node(9), Node(10), Node(11),
                Node({Node(12), Node(13), Node(14)})
            })
        })
    };
    printNumbers(array, 0);

    return 0;
}
```







