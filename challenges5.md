# whichMissing
#### I give you a scrambled list of n unique integers between 0 and n. Tell me what number is missing.

#### Example input/output

> which_missing_1([2, 5, 0, 3, 4, 1, 8, 7]) // = 6
> which_missing_2([2, 5, 0, 3, 4, 1, 8, 7]) // = 6
> which_missing_3([2, 5, 0, 3, 4, 1, 8, 7]) // = 6

```JavaScript
function whichMissing(arr) {
  let sum = (arr.length + 1) * (arr.length/2);
  let actual_sum = arr.reduce(function(a, b) {
    return a + b;
  });

  return sum - actual_sum;
}
```
Time complexity: O(n) <br>
Space complexity: O(1)
