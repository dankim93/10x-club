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


# shuffle

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

# silly_years

#### Write a function that takes a year (four digit integer) and returns an array with the 10 closest subsequent years that meet the following condition: the first two digits summed with the last two digits are equal to the middle two digits
#### Example input/output

> silly_years(1) // = [1208, 1318, 1428, 1538, 1648, 1758, 1868, 1978, 2307, 2417] <br>
> silly_years(2017) // = [2307, 2417, 2527, 2637, 2747, 2857, 2967, 3406, 3516, 3626]

```JavaScript
function silly_years(year) {
  let answer = [];
  while(answer.length != 10){
    let str = year.toString();
    let first = parseInt(str.slice(0,2));
    let second = parseInt(str.slice(2,4));
    let middle = parseInt(str.slice(1,3));

    if (first + second === middle) { answer.push(year); }

    year += 1;
  }

  return answer;
}
```
Time complexity: O(n)
