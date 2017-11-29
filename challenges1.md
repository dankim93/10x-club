# isPalindrome

#### Write a JavaScript function that takes a string and returns true if it's a palindrome, false if it's not. Use JavaScript.

#### Example input/output

> is_palindrome("abba") // = true <br>
> is_palindrome("bye") // = false <br>
> is_palindrome("a") // = true <br>
> is_palindrome("") // = true

```JavaScript
function isPalindrome(str) {
  for(let i = 0; i < str.length/2; i++) {
    if(str[i] != str[str.length - 1 - i]) {
      return false;
    }
  }

  return true;
}
```

Time complexity: O(n) <br>
Space complexity: O(1)


# Shuffle

```JavaScript
function shuffle(arr) {
  let new_array = arr.slice();

  for(let i = 0; i < arr.length; i++) {
    let rand = i + Math.floor(Math.random() * (arr.length - i));
    let temp1 = new_array[i];
    let temp2 = new_array[rand]
    new_array[i] = temp2;
    new_array[rand] = temp1;
  }

  return new_array;
}
```
