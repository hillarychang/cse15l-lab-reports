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

A failure-inducing input for the buggy program, as a JUnit test and any associated code is ```int[] inputArray = {1, 2, 3, 4, 5};```

An input that doesn’t induce a failure, as a JUnit test and any associated code ```int[] inputArray = {3, 3, 3, 3, 3}; ```

The symptom, as the output of running the tests (provide it as a screenshot of running JUnit with at least the two inputs above) 
```
import static org.junit.Assert.*;
import org.junit.*;


public class ArrayTests2 {
	@Test 
	public void testReverseInPlace() {
    int[] inputArray = {1, 2, 3, 4, 5};
    ArrayExamples2.reverseInPlace(inputArray);
    assertArrayEquals(new int[]{5, 4, 3, 2, 1}, inputArray);
	}

}
```

- ![Image](fail.png)  

```
import static org.junit.Assert.*;
import org.junit.*;


public class ArrayTests2 {
	@Test 
	public void testReverseInPlace() {
    int[] inputArray = {3, 3, 3, 3, 3};
    ArrayExamples2.reverseInPlace(inputArray);
    assertArrayEquals(new int[]{3, 3, 3, 3, 3}, inputArray);
	}

}
```
- ![Image](success.png)  


The bug, as the before-and-after code change required to fix it 

Before code change:
``` 
static void reverseInPlace(int[] arr) {
  for(int i = 0; i < arr.length; i += 1) {
    arr[i] = arr[arr.length - i - 1];
  }
}
```

After code change:
```
static void reverseInPlace(int[] arr) {
    int length = arr.length;
    for (int i = 0; i < length / 2; i++) {
        int temp = arr[i];
        arr[i] = arr[length - i - 1];
        arr[length - i - 1] = temp;
    }
}
```
The fix I made was I changed the for loop so that it wasn’t iterating through the entire for loop. Because it was looping through the entire loop, the reversed elements were getting overridden and un-reversing it. This is because the code before the fix tries to reverse the array in place by assigning each element at index i with the corresponding element from the end of the array (the index at arr.length - i - 1). This is incorrect because it ends up overwriting elements before they have been properly swapped. I fixed this by using a temporary variable (temp) to store the value of the element at index i before it is overwritten. Also, I changed the loop so that it only iterates up to half of the array (length / 2) since swapping elements beyond half the length would revert the array back to its original order.



## Part 2 - Researching Commands: ```find```
# Using -type Option:
```find ./technical/biomed -type f -name "*.txt"```
This command searches for all files with names ending in ".txt" in the ./technical/biomed directory and its subdirectories.
```
find ./technical/biomed -type f -name "*.txt"
./technical/biomed/1468-6708-3-1.txt
./technical/biomed/1468-6708-3-10.txt
./technical/biomed/1468-6708-3-3.txt
./technical/biomed/1468-6708-3-4.txt
./technical/biomed/1468-6708-3-7.txt
./technical/biomed/1471-2091-2-10.txt
./technical/biomed/1471-2091-2-11.txt
./technical/biomed/1471-2091-2-12.txt
./technical/biomed/1471-2091-2-13.txt
./technical/biomed/1471-2091-2-16.txt
./technical/biomed/1471-2091-2-5.txt
./technical/biomed/1471-2091-2-7.txt
./technical/biomed/1471-2091-2-9.txt
./technical/biomed/1471-2091-3-13.txt
./technical/biomed/1471-2091-3-14.txt
./technical/biomed/1471-2091-3-15.txt
./technical/biomed/1471-2091-3-16.txt
./technical/biomed/1471-2091-3-17.txt
./technical/biomed/1471-2091-3-18.txt
./technical/biomed/1471-2091-3-22.txt
./technical/biomed/1471-2091-3-23.txt
./technical/biomed/1471-2091-3-30.txt
./technical/biomed/1471-2091-3-31.txt
./technical/biomed/1471-2091-3-4.txt
./technical/biomed/1471-2091-3-8.txt
./technical/biomed/1471-2091-4-1.txt
./technical/biomed/1471-2091-4-5.txt
./technical/biomed/1471-2105-1-1.txt
./technical/biomed/1471-2105-2-1.txt
./technical/biomed/1471-2105-2-8.txt
./technical/biomed/1471-2105-2-9.txt
./technical/biomed/1471-2105-3-12.txt
./technical/biomed/1471-2105-3-14.txt
./technical/biomed/1471-2105-3-16.txt
./technical/biomed/1471-2105-3-17.txt
./technical/biomed/1471-2105-3-18.txt
./technical/biomed/1471-2105-3-2.txt
./technical/biomed/1471-2105-3-22.txt
./technical/biomed/1471-2105-3-23.txt
./technical/biomed/1471-2105-3-24.txt
./technical/biomed/1471-2105-3-26.txt
./technical/biomed/1471-2105-3-28.txt
./technical/biomed/1471-2105-3-3.txt
./technical/biomed/1471-2105-3-30.txt
./technical/biomed/1471-2105-3-34.txt
./technical/biomed/1471-2105-3-37.txt
./technical/biomed/1471-2105-3-38.txt
./technical/biomed/1471-2105-3-4.txt
./technical/biomed/1471-2105-3-6.txt
./technical/biomed/1471-2105-4-13.txt
./technical/biomed/1471-2105-4-24.txt
./technical/biomed/1471-2105-4-25.txt
./technical/biomed/1471-2105-4-26.txt
./technical/biomed/1471-2105-4-27.txt
./technical/biomed/1471-2105-4-28.txt
./technical/biomed/1471-2105-4-31.txt
./technical/biomed/1471-2121-1-2.txt
./technical/biomed/1471-2121-2-1.txt
./technical/biomed/1471-2121-2-10.txt
./technical/biomed/1471-2121-2-11.txt
./technical/biomed/1471-2121-2-12.txt
./technical/biomed/1471-2121-2-15.txt
./technical/biomed/1471-2121-2-18.txt
./technical/biomed/1471-2121-2-21.txt
./technical/biomed/1471-2121-2-22.txt
./technical/biomed/1471-2121-2-3.txt
./technical/biomed/1471-2121-2-6.txt
./technical/biomed/1471-2121-3-10.txt
./technical/biomed/1471-2121-3-11.txt
./technical/biomed/1471-2121-3-12.txt
./technical/biomed/1471-2121-3-13.txt
./technical/biomed/1471-2121-3-15.txt
./technical/biomed/1471-2121-3-16.txt
./technical/biomed/1471-2121-3-18.txt
./technical/biomed/1471-2121-3-19.txt
./technical/biomed/1471-2121-3-2.txt
./technical/biomed/1471-2121-3-21.txt
./technical/biomed/1471-2121-3-22.txt
./technical/biomed/1471-2121-3-25.txt
./technical/biomed/1471-2121-3-30.txt
./technical/biomed/1471-2121-3-4.txt
./technical/biomed/1471-2121-3-6.txt
./technical/biomed/1471-2121-3-8.txt
./technical/biomed/1471-2121-4-1.txt
./technical/biomed/1471-2121-4-2.txt
./technical/biomed/1471-2121-4-3.txt
./technical/biomed/1471-2121-4-4.txt
./technical/biomed/1471-2121-4-5.txt
./technical/biomed/1471-2121-4-6.txt
./technical/biomed/1471-213X-1-1.txt
./technical/biomed/1471-213X-1-10.txt
./technical/biomed/1471-213X-1-11.txt
./technical/biomed/1471-213X-1-12.txt
./technical/biomed/1471-213X-1-13.txt
./technical/biomed/1471-213X-1-15.txt
./technical/biomed/1471-213X-1-2.txt
./technical/biomed/1471-213X-1-3.txt
./technical/biomed/1471-213X-1-4.txt
./technical/biomed/1471-213X-1-6.txt
./technical/biomed/1471-213X-1-9.txt
./technical/biomed/1471-213X-2-1.txt
./technical/biomed/1471-213X-2-7.txt
./technical/biomed/1471-213X-2-8.txt
./technical/biomed/1471-213X-3-2.txt
./technical/biomed/1471-213X-3-3.txt
./technical/biomed/1471-213X-3-4.txt
./technical/biomed/1471-213X-3-7.txt
./technical/biomed/1471-2148-1-1.txt
./technical/biomed/1471-2148-1-14.txt
./technical/biomed/1471-2148-1-4.txt
./technical/biomed/1471-2148-1-6.txt
./technical/biomed/1471-2148-1-8.txt
./technical/biomed/1471-2148-2-12.txt
./technical/biomed/1471-2148-2-14.txt
./technical/biomed/1471-2148-2-15.txt
./technical/biomed/1471-2148-2-17.txt
./technical/biomed/1471-2148-2-2.txt
./technical/biomed/1471-2148-2-5.txt
./technical/biomed/1471-2148-2-7.txt
./technical/biomed/1471-2148-2-8.txt
./technical/biomed/1471-2148-3-1.txt
./technical/biomed/1471-2148-3-18.txt
./technical/biomed/1471-2148-3-3.txt
./technical/biomed/1471-2148-3-4.txt
./technical/biomed/1471-2148-3-7.txt
./technical/biomed/1471-2156-2-1.txt
./technical/biomed/1471-2156-2-12.txt
./technical/biomed/1471-2156-2-17.txt
./technical/biomed/1471-2156-2-18.txt
./technical/biomed/1471-2156-2-3.txt
./technical/biomed/1471-2156-2-5.txt
./technical/biomed/1471-2156-2-7.txt
./technical/biomed/1471-2156-2-8.txt
./technical/biomed/1471-2156-3-10.txt
./technical/biomed/1471-2156-3-11.txt
./technical/biomed/1471-2156-3-16.txt
./technical/biomed/1471-2156-3-17.txt
./technical/biomed/1471-2156-3-22.txt
./technical/biomed/1471-2156-3-3.txt
./technical/biomed/1471-2156-3-4.txt
./technical/biomed/1471-2156-4-10.txt
./technical/biomed/1471-2156-4-5.txt
./technical/biomed/1471-2156-4-6.txt
./technical/biomed/1471-2156-4-9.txt
./technical/biomed/1471-2164-2-1.txt
./technical/biomed/1471-2164-2-2.txt
./technical/biomed/1471-2164-2-4.txt
./technical/biomed/1471-2164-2-6.txt
./technical/biomed/1471-2164-2-7.txt
./technical/biomed/1471-2164-2-8.txt
./technical/biomed/1471-2164-2-9.txt
./technical/biomed/1471-2164-3-1.txt
./technical/biomed/1471-2164-3-10.txt
./technical/biomed/1471-2164-3-13.txt
./technical/biomed/1471-2164-3-15.txt
./technical/biomed/1471-2164-3-16.txt
./technical/biomed/1471-2164-3-18.txt
./technical/biomed/1471-2164-3-19.txt
./technical/biomed/1471-2164-3-23.txt
./technical/biomed/1471-2164-3-24.txt
./technical/biomed/1471-2164-3-26.txt
./technical/biomed/1471-2164-3-27.txt
./technical/biomed/1471-2164-3-28.txt
./technical/biomed/1471-2164-3-29.txt
./technical/biomed/1471-2164-3-30.txt
./technical/biomed/1471-2164-3-31.txt
./technical/biomed/1471-2164-3-32.txt
./technical/biomed/1471-2164-3-33.txt
./technical/biomed/1471-2164-3-34.txt
./technical/biomed/1471-2164-3-35.txt
./technical/biomed/1471-2164-3-4.txt
./technical/biomed/1471-2164-3-6.txt
./technical/biomed/1471-2164-3-7.txt
./technical/biomed/1471-2164-3-8.txt
./technical/biomed/1471-2164-3-9.txt
./technical/biomed/1471-2164-4-13.txt
./technical/biomed/1471-2164-4-14.txt
./technical/biomed/1471-2164-4-15.txt
./technical/biomed/1471-2164-4-16.txt
./technical/biomed/1471-2164-4-19.txt
./technical/biomed/1471-2164-4-2.txt
./technical/biomed/1471-2164-4-21.txt
./technical/biomed/1471-2164-4-22.txt
./technical/biomed/1471-2164-4-23.txt
./technical/biomed/1471-2164-4-24.txt
./technical/biomed/1471-2164-4-25.txt
./technical/biomed/1471-2164-4-26.txt
./technical/biomed/1471-2164-4-28.txt
./technical/biomed/1471-2164-4-4.txt
./technical/biomed/1471-2164-4-5.txt
./technical/biomed/1471-2164-4-6.txt
./technical/biomed/1471-2172-1-1.txt
./technical/biomed/1471-2172-2-10.txt
./technical/biomed/1471-2172-2-3.txt
./technical/biomed/1471-2172-2-4.txt
./technical/biomed/1471-2172-2-9.txt
./technical/biomed/1471-2172-3-1.txt
./technical/biomed/1471-2172-3-10.txt
./technical/biomed/1471-2172-3-12.txt
./technical/biomed/1471-2172-3-16.txt
./technical/biomed/1471-2172-3-2.txt
./technical/biomed/1471-2172-3-4.txt
./technical/biomed/1471-2172-3-9.txt
./technical/biomed/1471-2172-4-1.txt
./technical/biomed/1471-2172-4-2.txt
./technical/biomed/1471-2180-1-12.txt
./technical/biomed/1471-2180-1-16.txt
./technical/biomed/1471-2180-1-26.txt
./technical/biomed/1471-2180-1-28.txt
./technical/biomed/1471-2180-1-29.txt
./technical/biomed/1471-2180-1-31.txt
./technical/biomed/1471-2180-1-33.txt
./technical/biomed/1471-2180-1-34.txt
./technical/biomed/1471-2180-1-7.txt
./technical/biomed/1471-2180-1-8.txt
./technical/biomed/1471-2180-2-1.txt
./technical/biomed/1471-2180-2-13.txt
./technical/biomed/1471-2180-2-16.txt
./technical/biomed/1471-2180-2-2.txt
./technical/biomed/1471-2180-2-20.txt
./technical/biomed/1471-2180-2-22.txt
./technical/biomed/1471-2180-2-26.txt
./technical/biomed/1471-2180-2-29.txt
./technical/biomed/1471-2180-2-32.txt
./technical/biomed/1471-2180-2-35.txt
./technical/biomed/1471-2180-2-38.txt
./technical/biomed/1471-2180-2-7.txt
./technical/biomed/1471-2180-3-10.txt
./technical/biomed/1471-2180-3-11.txt
./technical/biomed/1471-2180-3-13.txt
./technical/biomed/1471-2180-3-15.txt
./technical/biomed/1471-2180-3-4.txt
./technical/biomed/1471-2180-3-5.txt
./technical/biomed/1471-2180-3-9.txt
./technical/biomed/1471-2199-2-1.txt
./technical/biomed/1471-2199-2-10.txt
./technical/biomed/1471-2199-2-12.txt
./technical/biomed/1471-2199-2-2.txt
./technical/biomed/1471-2199-2-3.txt
./technical/biomed/1471-2199-2-4.txt
./technical/biomed/1471-2199-2-5.txt
./technical/biomed/1471-2199-2-6.txt
./technical/biomed/1471-2199-3-10.txt
./technical/biomed/1471-2199-3-11.txt
./technical/biomed/1471-2199-3-12.txt
./technical/biomed/1471-2199-3-17.txt
./technical/biomed/1471-2199-3-3.txt
./technical/biomed/1471-2199-3-7.txt
./technical/biomed/1471-2199-4-4.txt
./technical/biomed/1471-2199-4-5.txt
./technical/biomed/1471-2202-1-1.txt
./technical/biomed/1471-2202-2-1.txt
./technical/biomed/1471-2202-2-10.txt
./technical/biomed/1471-2202-2-12.txt
./technical/biomed/1471-2202-2-14.txt
./technical/biomed/1471-2202-2-15.txt
./technical/biomed/1471-2202-2-16.txt
./technical/biomed/1471-2202-2-17.txt
./technical/biomed/1471-2202-2-18.txt
./technical/biomed/1471-2202-2-19.txt
./technical/biomed/1471-2202-2-2.txt
./technical/biomed/1471-2202-2-20.txt
./technical/biomed/1471-2202-2-3.txt
./technical/biomed/1471-2202-2-5.txt
./technical/biomed/1471-2202-2-6.txt
./technical/biomed/1471-2202-2-7.txt
./technical/biomed/1471-2202-2-8.txt
./technical/biomed/1471-2202-2-9.txt
./technical/biomed/1471-2202-3-1.txt
./technical/biomed/1471-2202-3-10.txt
./technical/biomed/1471-2202-3-11.txt
./technical/biomed/1471-2202-3-14.txt
./technical/biomed/1471-2202-3-16.txt
./technical/biomed/1471-2202-3-17.txt
./technical/biomed/1471-2202-3-19.txt
./technical/biomed/1471-2202-3-20.txt
./technical/biomed/1471-2202-3-3.txt
./technical/biomed/1471-2202-3-4.txt
./technical/biomed/1471-2202-3-5.txt
./technical/biomed/1471-2202-3-7.txt
./technical/biomed/1471-2202-3-8.txt
./technical/biomed/1471-2202-4-10.txt
./technical/biomed/1471-2202-4-11.txt
./technical/biomed/1471-2202-4-12.txt
./technical/biomed/1471-2202-4-16.txt
./technical/biomed/1471-2202-4-17.txt
./technical/biomed/1471-2202-4-2.txt
./technical/biomed/1471-2202-4-3.txt
./technical/biomed/1471-2202-4-5.txt
./technical/biomed/1471-2202-4-6.txt
./technical/biomed/1471-2210-1-10.txt
./technical/biomed/1471-2210-1-2.txt
./technical/biomed/1471-2210-1-3.txt
./technical/biomed/1471-2210-1-4.txt
./technical/biomed/1471-2210-1-7.txt
./technical/biomed/1471-2210-1-8.txt
./technical/biomed/1471-2210-2-14.txt
./technical/biomed/1471-2210-2-4.txt
./technical/biomed/1471-2210-2-5.txt
./technical/biomed/1471-2210-2-6.txt
./technical/biomed/1471-2210-2-8.txt
./technical/biomed/1471-2210-2-9.txt
./technical/biomed/1471-2210-3-1.txt
./technical/biomed/1471-2210-3-3.txt
./technical/biomed/1471-2229-1-2.txt
./technical/biomed/1471-2229-1-3.txt
./technical/biomed/1471-2229-2-11.txt
./technical/biomed/1471-2229-2-3.txt
./technical/biomed/1471-2229-2-4.txt
./technical/biomed/1471-2229-2-8.txt
./technical/biomed/1471-2229-2-9.txt
./technical/biomed/1471-2229-3-3.txt
./technical/biomed/1471-2253-1-1.txt
./technical/biomed/1471-2253-2-4.txt
./technical/biomed/1471-2253-2-5.txt
./technical/biomed/1471-2261-1-6.txt
./technical/biomed/1471-2261-2-11.txt
./technical/biomed/1471-2261-3-4.txt
./technical/biomed/1471-2261-3-5.txt
./technical/biomed/1471-2288-1-9.txt
./technical/biomed/1471-2288-2-10.txt
./technical/biomed/1471-2288-2-11.txt
./technical/biomed/1471-2288-2-4.txt
./technical/biomed/1471-2288-3-4.txt
./technical/biomed/1471-2288-3-8.txt
./technical/biomed/1471-2288-3-9.txt
./technical/biomed/1471-2296-3-18.txt
./technical/biomed/1471-2296-3-19.txt
./technical/biomed/1471-2296-3-3.txt
./technical/biomed/1471-230X-1-10.txt
./technical/biomed/1471-230X-1-5.txt
./technical/biomed/1471-230X-1-6.txt
./technical/biomed/1471-230X-1-8.txt
./technical/biomed/1471-230X-2-17.txt
./technical/biomed/1471-230X-2-21.txt
./technical/biomed/1471-230X-2-23.txt
./technical/biomed/1471-230X-3-3.txt
./technical/biomed/1471-230X-3-5.txt
./technical/biomed/1471-2318-3-2.txt
./technical/biomed/1471-2326-2-4.txt
./technical/biomed/1471-2334-1-10.txt
./technical/biomed/1471-2334-1-13.txt
./technical/biomed/1471-2334-1-17.txt
./technical/biomed/1471-2334-1-21.txt
./technical/biomed/1471-2334-1-24.txt
./technical/biomed/1471-2334-1-9.txt
./technical/biomed/1471-2334-2-1.txt
./technical/biomed/1471-2334-2-24.txt
./technical/biomed/1471-2334-2-26.txt
./technical/biomed/1471-2334-2-27.txt
./technical/biomed/1471-2334-2-29.txt
./technical/biomed/1471-2334-2-5.txt
./technical/biomed/1471-2334-2-6.txt
./technical/biomed/1471-2334-2-7.txt
./technical/biomed/1471-2334-3-10.txt
./technical/biomed/1471-2334-3-11.txt
./technical/biomed/1471-2334-3-12.txt
./technical/biomed/1471-2334-3-13.txt
./technical/biomed/1471-2334-3-15.txt
./technical/biomed/1471-2334-3-9.txt
./technical/biomed/1471-2350-2-11.txt
./technical/biomed/1471-2350-2-12.txt
./technical/biomed/1471-2350-2-2.txt
./technical/biomed/1471-2350-2-8.txt
./technical/biomed/1471-2350-3-1.txt
./technical/biomed/1471-2350-3-12.txt
./technical/biomed/1471-2350-3-7.txt
./technical/biomed/1471-2350-3-9.txt
./technical/biomed/1471-2350-4-2.txt
./technical/biomed/1471-2350-4-3.txt
./technical/biomed/1471-2350-4-4.txt
./technical/biomed/1471-2350-4-6.txt
./technical/biomed/1471-2369-3-1.txt
./technical/biomed/1471-2369-3-10.txt
./technical/biomed/1471-2369-3-6.txt
./technical/biomed/1471-2369-3-9.txt
./technical/biomed/1471-2369-4-1.txt
./technical/biomed/1471-2369-4-5.txt
./technical/biomed/1471-2377-1-2.txt
./technical/biomed/1471-2377-2-4.txt
./technical/biomed/1471-2377-2-6.txt
./technical/biomed/1471-2377-3-4.txt
./technical/biomed/1471-2407-1-13.txt
./technical/biomed/1471-2407-1-15.txt
./technical/biomed/1471-2407-1-19.txt
./technical/biomed/1471-2407-1-6.txt
./technical/biomed/1471-2407-2-11.txt
./technical/biomed/1471-2407-2-12.txt
./technical/biomed/1471-2407-2-15.txt
./technical/biomed/1471-2407-2-16.txt
./technical/biomed/1471-2407-2-17.txt
./technical/biomed/1471-2407-2-18.txt
./technical/biomed/1471-2407-2-19.txt
./technical/biomed/1471-2407-2-22.txt
./technical/biomed/1471-2407-2-23.txt
./technical/biomed/1471-2407-2-3.txt
./technical/biomed/1471-2407-2-31.txt
./technical/biomed/1471-2407-2-33.txt
./technical/biomed/1471-2407-2-8.txt
./technical/biomed/1471-2407-2-9.txt
./technical/biomed/1471-2407-3-14.txt
./technical/biomed/1471-2407-3-15.txt
./technical/biomed/1471-2407-3-16.txt
./technical/biomed/1471-2407-3-18.txt
./technical/biomed/1471-2407-3-3.txt
./technical/biomed/1471-2407-3-4.txt
./technical/biomed/1471-2407-3-5.txt
./technical/biomed/1471-2415-3-1.txt
./technical/biomed/1471-2415-3-3.txt
./technical/biomed/1471-2415-3-4.txt
./technical/biomed/1471-2415-3-5.txt
./technical/biomed/1471-2431-2-1.txt
./technical/biomed/1471-2431-2-11.txt
./technical/biomed/1471-2431-2-12.txt
./technical/biomed/1471-2431-2-4.txt
./technical/biomed/1471-2431-3-3.txt
./technical/biomed/1471-2431-3-4.txt
./technical/biomed/1471-2431-3-5.txt
./technical/biomed/1471-2431-3-6.txt
./technical/biomed/1471-244X-2-9.txt
./technical/biomed/1471-244X-3-5.txt
./technical/biomed/1471-2458-1-9.txt
./technical/biomed/1471-2458-2-11.txt
./technical/biomed/1471-2458-2-16.txt
./technical/biomed/1471-2458-2-18.txt
./technical/biomed/1471-2458-2-21.txt
./technical/biomed/1471-2458-2-25.txt
./technical/biomed/1471-2458-2-3.txt
./technical/biomed/1471-2458-2-6.txt
./technical/biomed/1471-2458-3-11.txt
./technical/biomed/1471-2458-3-2.txt
./technical/biomed/1471-2458-3-20.txt
./technical/biomed/1471-2458-3-5.txt
./technical/biomed/1471-2458-3-9.txt
./technical/biomed/1471-2466-1-1.txt
./technical/biomed/1471-2466-2-3.txt
./technical/biomed/1471-2466-2-4.txt
./technical/biomed/1471-2466-3-1.txt
./technical/biomed/1471-2474-2-1.txt
./technical/biomed/1471-2474-2-2.txt
./technical/biomed/1471-2474-2-3.txt
./technical/biomed/1471-2474-3-23.txt
./technical/biomed/1471-2474-3-3.txt
./technical/biomed/1471-2474-4-4.txt
./technical/biomed/1471-2474-4-8.txt
./technical/biomed/1471-2490-3-2.txt
./technical/biomed/1471-5945-1-3.txt
./technical/biomed/1471-5945-2-13.txt
./technical/biomed/1471-5945-3-3.txt
./technical/biomed/1472-6750-1-11.txt
./technical/biomed/1472-6750-1-12.txt
./technical/biomed/1472-6750-1-13.txt
./technical/biomed/1472-6750-1-6.txt
./technical/biomed/1472-6750-1-8.txt
./technical/biomed/1472-6750-2-10.txt
./technical/biomed/1472-6750-2-13.txt
./technical/biomed/1472-6750-2-14.txt
./technical/biomed/1472-6750-2-2.txt
./technical/biomed/1472-6750-2-21.txt
./technical/biomed/1472-6750-3-11.txt
./technical/biomed/1472-6750-3-4.txt
./technical/biomed/1472-6750-3-6.txt
./technical/biomed/1472-6769-1-1.txt
./technical/biomed/1472-6769-1-2.txt
./technical/biomed/1472-6769-1-3.txt
./technical/biomed/1472-6769-1-4.txt
./technical/biomed/1472-6785-1-3.txt
./technical/biomed/1472-6785-1-5.txt
./technical/biomed/1472-6785-2-6.txt
./technical/biomed/1472-6785-2-7.txt
./technical/biomed/1472-6793-1-11.txt
./technical/biomed/1472-6793-1-12.txt
./technical/biomed/1472-6793-1-15.txt
./technical/biomed/1472-6793-1-2.txt
./technical/biomed/1472-6793-1-6.txt
./technical/biomed/1472-6793-1-8.txt
./technical/biomed/1472-6793-2-1.txt
./technical/biomed/1472-6793-2-11.txt
./technical/biomed/1472-6793-2-16.txt
./technical/biomed/1472-6793-2-17.txt
./technical/biomed/1472-6793-2-18.txt
./technical/biomed/1472-6793-2-19.txt
./technical/biomed/1472-6793-2-2.txt
./technical/biomed/1472-6793-2-4.txt
./technical/biomed/1472-6793-2-5.txt
./technical/biomed/1472-6793-2-8.txt
./technical/biomed/1472-6793-3-3.txt
./technical/biomed/1472-6793-3-4.txt
./technical/biomed/1472-6793-3-5.txt
./technical/biomed/1472-6793-3-6.txt
./technical/biomed/1472-6807-1-1.txt
./technical/biomed/1472-6807-2-1.txt
./technical/biomed/1472-6807-2-2.txt
./technical/biomed/1472-6807-2-3.txt
./technical/biomed/1472-6807-2-4.txt
./technical/biomed/1472-6807-2-5.txt
./technical/biomed/1472-6807-2-9.txt
./technical/biomed/1472-6807-3-1.txt
./technical/biomed/1472-6807-3-2.txt
./technical/biomed/1472-6815-2-3.txt
./technical/biomed/1472-6823-2-2.txt
./technical/biomed/1472-6823-3-1.txt
./technical/biomed/1472-6831-2-2.txt
./technical/biomed/1472-6831-3-1.txt
./technical/biomed/1472-684X-1-5.txt
```


```find ./technical -type d```
This command searches for all directories within the ./technical directory.
```
find ./technical -type d
./technical
./technical/911report
./technical/biomed
./technical/government
./technical/government/About_LSC
./technical/government/Alcohol_Problems
./technical/government/Env_Prot_Agen
./technical/government/Gen_Account_Office
./technical/government/Media
./technical/government/Post_Rate_Comm
./technical/plos
```


# Using -name Option:
```find ./technical -type f -name "*911report*"```
This command searches for a directory named 911report within the ./technical directory.
```
find ./technical -type f -name "*911report*"
```


```find ./technical -type f -name "*.pdf"```
This command searches for all files with a .pdf extension within the ./technical directory.
```
find ./technical -type f -name "*.pdf"
```


# Using -size Option:
```find ./technical -type f -size -1024c```
This command searches for files within the ./technical directory that are smaller than 1 kilobyte (1024 bytes).
```
find ./technical -type f -size -1024c
./technical/plos/pmed.0020191.txt
./technical/plos/pmed.0020226.txt
```

```find ./technical -type f -size 0```
This command searches for empty files (files with a size of 0 bytes) within the ./technical directory.
```
find ./technical -type f -size 0
```


# Using -mtime Option:
```find ./technical -type f -mtime +5 -mtime -10```
This command searches for files within the ./technical directory that were modified between 5 and 10 days ago.
```
find ./technical -type f -mtime +5 -mtime -10
```


```find ./technical -type f -mtime -1```
This command searches for files within the ./technical directory that were modified within the past day
```
find ./technical -type f -mtime -1
```

## Sources
I primarily found examples for the find command from the following sources:
https://www.redhat.com/sysadmin/linux-find-command
