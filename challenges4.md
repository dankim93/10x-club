# sum_rec
#### Write a function that takes an array of integers and returns their sum. Use recursion.+

#### Example input/output

> sum_rec([4,2,7]) // = 13 (recurse twice)

```JavaScript
function sum_rec(int) {
  if(int.length == 0) { return 0; }
  return int[0] + sum_rec(int.slice(1, int.length));
}
```


# weightedRandomIndex
#### Given an array, write a function that will return a random index of the array. The probability of an index being returned is weighted by the value at that index against the sum of the array values. For example, for the array [4, 6, 8], index 0 should be returned with 4 in 18 odds, index 1 should be returned with 6 in 18 odds, and index 2 should be return with 8 in 18 odds. Implement this in O(n) time.

#### Example input/output

> weightedRandomIndex([1,2,3]) // = 0 with 1/6 probability, 1 with 1/3 probability, 2 with 1/2 probability

```JavaScript
function weightedRandomIndex(arr) {
  let sum = arr.reduce(function(a, b) {
    return a + b;
  }, 0);
  let random = Math.floor(Math.random() * sum);

  let limit = 0;
  for(let i = 0; i < arr.length; i++) {
    limit += arr[i];
    if (random < limit) {
      return i;
    }
  }
}
```
