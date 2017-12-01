# digital_root

#### Write a method, digital_root(num). It should sum the digits of a positive integer. If it is greater than or equal to 10, sum the digits of the resulting number. Keep repeating until there is only one digit in the result, called the "digital root". Do not use string conversion within your method.

#### Example input/output

> digital_root(103) // = 4 (1+0+3=4)
> digital_root(999) // = 9 (9+9+9=27, 2+7=9)
> digital_root(728934) // = 6 (7+2+8+9+3+4=33, 3+3=6)

```JavaScript
function digital_root(num) {
  if (num < 10) { return num; }
  let sum = 0;

  while (num > 0) {
    sum += num % 10;
    num = Math.floor(num/10);
  }

  return digital_root(sum);
}
```

# fibs

#### Write a function, fibs(num) which returns an array of the first n elements from the fibonnacci sequence, given n.

#### Example input/output

> fibs(4) // = [1,1,2,3]
> fibs(0) // = []
> fibs(8) // = [1,1,2,3,5,8,13,21]

```JavaScript
function fib(n) {
  let fibs = [1, 1];
  if (n < 2) { return fibs.slice(0, n+1); }

  fibs = fib(n - 1);
  fibs = fibs.push(fibs[fibs.length - 1] + fibs[fibs.length - 2]);

  return fibs;
}
```

# pair_sum

#### Given an array of integers, return all pairs that sum up to a specified value k. List the pairs in [min, max] order.

#### Example input/output

> pair_sum([1, 2, -1], 0) // = [ [-1, 1] ]
> pair_sum([1, 2, -1, -1], 0) // = [ [-1, 1] ]
> pair_sum([1, 2, -1, -1, -2], 0) // = [ [-1, 1], [-2, 2] ]
> pair_sum([1, 2, -1, -1, -2], 1) // = [ [-1, 2] ]
> pair_sum([1, 2, -1, -1, -2], -1) // = [ [-2, 1] ]

```JavaScript
function pair_sum(arr, k) {
  let set = new Set();
  let answer = new Set();

  for(let i = 0; i < arr.length; i++) {
    if(set.has(k - arr[i])) {
      if((k-arr[i]) > arr[i]){
        answer.add([arr[i], k - arr[i]]);
      } else {
        answer.add([k - arr[i], arr[i]]);
      }
    }
    set.add(arr[i]);
  }

  return answer;
}
```
Time Complexity: O(n) checking inside set is O(1)
