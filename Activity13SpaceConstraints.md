# Activity 13 Space Constraints

## 1. Following is the 'Word Builder' algorithm. Describe its space complexity in terms of Big O.

``` C++
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
``` C++
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

