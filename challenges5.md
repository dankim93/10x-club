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

# k_closest_stars
#### Consider a coordinate system for the Milky Way, in which Earth is at (0,0,0). Model stars as points, and assume distances are in light years. The Milky Way consists of approximately 10^12 stars, and their coordinates are stored in a file. How would you compute the k stars which are closest to Earth?

#### Example input/output

> k_closest_stars([(10,20,30), (30,10,10), ...], 5) // = [(xxx), (xxx), (xxx), (xxx), (xxx)]

```JavaScript
function k_closest_stars(stars, k) {
  let heap = new BinaryMaxHeap(function(star1, star2) {
    var distance1 = Math.sqrt(star1[0]**2 + star1[1]**2 + star1[2]**2);
    var distance2 = Math.sqrt(star2[0]**2 + star2[1]**2 + star2[2]**2);
    if (distance1 > distance2) {
      return 1;
    } else if (distance1 < distance2) {
      return -1;
    } else {
      return 0;
    }
  });

  for(let i = 0; i < k; i++) {
    heap.push(stars[i]);
  }

  for(i = k; i < stars.length; i++) {
    heap.push(stars[i]);
    heap.extract();
  }

  let k_closest = [];
  while(heap.length > 0) {
    k_closest.push(heap.extract());
  }

  return k_closest;
}
```
Time complexity: O(nlogk) iteration through stars & heapify <br>
Space complexity: O(1)
