# StackQueue
#### Implement a queue using stacks. That is, write enqueue and dequeue using only push and pop operations.

#### Example input/output

> var sq = new StackQueue();
> sq.enqueue(1);
> sq.enqueue(2);
> sq.enqueue(3);
> sq.dequeue();  // = 1
> sq.dequeue();  // = 2
> sq.dequeue();  // = 3

```JavaScript
class stackQueue {
  constructor() {
    this.in = [];
    this.out = [];
  }

  enqueue(val) {
    this.in.push(val);
    return this.in[this.in.length - 1];
  }

  dequeue() {
    if(this.out.length === 0) {
      while(this.in.length > 0) {
        this.out.push(this.in.pop());
      }
    }
    return this.out.pop();
  }
}
```
Time complexity for enqueue: O(1) <br>
Time complexity for dequeue: O(1) ammortized

# Merge Sort

```JavaScript
function merge(left, right) {
  let sorted = [];
  while(left.length > 0 && right.length > 0) {
    if(left.length !== undefined && left[0] > right[0]) {
      sorted.push(right.shift());
    } else {
      sorted.push(left.shift());
    }
  }

  return sorted.concat(left).concat(right);
}

function merge_rec(arr) {
  if(arr.length < 2) {
    return arr;
  }
  let left = arr.slice(0, arr.length/2);
  let right = arr.slice(arr.length/2, arr.length);

  left = merge_rec(left);
  right = merge_rec(right);
  return merge(left, right);
}
```
Time complexity: O(n*logn)


# Binary Search
#### Implement binary search

```JavaScript
function binarySearch(sorted, val) {
  if(sorted.length === 0) {
    return -1;
  }
  let mid = Math.floor(sorted.length / 2);

  if(sorted[mid] === val) {
    return mid;
  } else if(val < sorted[mid]) {
    let left = sorted.slice(0, mid);
    return binarySearch(left, val);
  } else {
    let right = sorted.slice(mid + 1, sorted.length);
    let answer = binarySearch(right, val);
    return answer === -1 ? -1 : answer + (mid + 1);
  }

}
```
Time complexity: O(log(n)) <br>
