# Lab Report 3

## Part 1 - Bugs
The bug I chose from lab 4 is the bug in the following function.

```
static void reverseInPlace(int[] arr) {
  for(int i = 0; i < arr.length; i += 1) {
    arr[i] = arr[arr.length - i - 1];
  }
}
```
