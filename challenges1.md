# isPalindrome

### Write a JavaScript function that takes a string and returns true if it's a palindrome, false if it's not. Use JavaScript.
### This solution takes less time and memory than rebuilding the string backward and comparing the two.

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
