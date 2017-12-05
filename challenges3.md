# rand7
#### Given a method rand5 which generates random integer (0..4) uniformly, write a method rand7 which generates random integer (0..6) uniformly

#### Example input/output

> rand7() // = random number between 0-7 with equal probability

```JavaScript
function rand5() {
  return Math.floor(Math.random() * 5);
  //(0, 1, 2, 3, 4)
}

function rand7() {
  while(true) {
    // 5 * (0, 1, 2, 3, 4) + (0, 1, 2, 3, 4) --> (0..24) uniformly
    let num = 5 * rand5() + rand5();
    if(num < 21) {
      return num % 7;
    }
  }
}
```
# move_zeros
#### Given an array, move all zeros to the end. The order of non-zero elements does not matter. Algorithm should be O(n); use O(1) extra space.

#### Example input/output

> move_zeros([1, 2, 0, 3, 4, 0, 5, 6, 0]) // = [1, 2, 6, 3, 4, 5, 0, 0, 0]

```JavaScript
function move_zeros(arr) {
  let pos = arr.length - 1;
  for(let i = 0; i < arr.length; i++) {
    if(arr[i] === 0) {
      while(arr[pos] === 0) {
        if(i === pos) { return arr; }
        pos -= 1;
      }
      arr[i] = arr[pos];
      arr[pos] = 0;
    }
  }

  return arr;
}
```
Time complexity: O(n) <br>
Space complexity: O(1)

# binary
#### Write a function that takes an integer and returns it in binary form.

#### Example input/output

> binary(10) // = 1010
> binary(0) // = 0
> binary(666) // = 1010011010

```JavaScript
function toBinary(int) {
  let binary = [];

  while (int > 0) {
    binary.unshift(int % 2);
    int = Math.floor(int/2);
  }

  return binary.join("");
}
```

# permutations
#### Write a method that takes an array and returns all its permutations. Time/memory complexity should be proportional to the number of permutations.

#### Example input/output

>permutations([1,2,3])
>=> [[1, 2, 3], [2, 1, 3], [2, 3, 1], [1, 3, 2], [3, 1, 2], [3, 2, 1]]

```JavaScript
function permutations(arr) {
  if (arr.length == 0) {
    return [arr];
  }

  let perms = [];

  for (let i = 0; i < arr.length; i++) {
    let n = arr[i];
    let rest = arr.slice(0, i).concat(arr.slice(i+1, arr.length));
    let newPerms = permutations(rest).map(function(perm) {
      perm.unshift(n);
      return perm;
    });
    perms = perms.concat(newPerms);
  }
  return perms;
}
```
