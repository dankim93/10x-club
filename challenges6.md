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
