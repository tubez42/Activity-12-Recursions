# Activity 13 Space Constraints

## 1. Following is the 'Word Builder' algorithm. Describe its space complexity in terms of Big O.

``` Javascript
function wordBuilder(array) { 
		let collection = [];
		for(let i = 0; i < array.length; i++) { 
				for(let j = 0; j < array.length; j++) {
						if (i !== j) {
								collection.push(array[i] + array[j]);
						}
				}
		}
		return collection; 
}

```
The wordBuilder function wraps through the array of length n, n<sup>2</sup> times. In each iteration we can be storing a new string to the collection each
time. So the extra memory needed grows at a rate of O(n<sup>2</sup>).
<hr>

## 2. Following is a function that reverses an array. Describe its space complexity in terms of Big O:
``` Javascript
function reverse(array) { 
		let newArray = [];
		for (let i = array.length - 1; i >= 0; i--) { 
				newArray.push(array[i]);
		}
		return newArray;
}

```
In the reverse() function we are taking an array as an argument, creating a new blank array and then populating it with the contents of the first.
If the first array has a length of n, this means that in creating a new array we are using n addtional space. The space complexity for the function is then
O(n). 
<hr>

## 3. Create a new function to reverse an array that takes up just O(1) extra space.

If instead of creating an entirely new array to create the array in reverse we just modify the exisiting array by using a a temporary variable we only need to use the extra unit of memory. I wrote it in C++ along with a main() in order to test it.

``` C++
#include <iostream>

/*  updates the array from left to right to put it in reverese */
void reverseArray(int array[], int size) {
    int left = 0;
    int right = size - 1;

    while (left < right) {
        int temp = array[left];
        array[left] = array[right];
        array[right] = temp;

        left++;
        right--;
    }
}

int main() {
    int array[] = {1 , 2 ,3 ,4, 5};
    int size = sizeof(array) / sizeof(array[0]);

    reverseArray(array, size);

    std::cout << "Reverse array: ";

    for (int i = 0; i < size; i++){
        std::cout << array[i] << " ";
    }

    return 0;
}
```
<img width="296" height="48" alt="image" src="https://github.com/user-attachments/assets/e59d1286-011d-4afd-99ef-e5a4e121448c" />

<hr>

## 4. Following are three different implementations of a function that accepts an array of numbers and returns an array containing those numbers multiplied by 2. For example, if the input is [5, 4, 3, 2, 1], the output will be [10, 8, 6, 4, 2].

```Javascript
function doubleArray1(array) { 
	let newArray = [];

	for(let i = 0; i < array.length; i++) { 
		newArray.push(array[i] * 2);
	}
	return newArray; 
}


function doubleArray2(array) {
	for(let i = 0; i < array.length; i++) {
  	array[i] *= 2;
  }
	return array; 
}


function doubleArray3(array, index=0) { 
	if (index >= array.length) { return; }
  array[index] *= 2;
  doubleArray3(array, index + 1);
	return array; 
}
```











