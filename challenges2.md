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
