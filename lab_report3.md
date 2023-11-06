# Part 1:
## A failure-inducing input
```
 @Test 
public void testReverseInPlace2() {
    int[] input1 = { 3,2,1 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{1,2,3}, input1);
}
```
## An input that doesn’t induce a failure
```
@Test 
public void testReverseInPlace() {
    int[] input1 = { 3, 3, 3 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 3, 3, 3 }, input1);
}
```
## The symptom
![image]()

## The bug
### before fixed
```
  // Changes the input array to be in reversed order
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```

### after fixed
```
  // Changes the input array to be in reversed order
  static void reverseInPlace(int[] arr) {
    int temp = 0;
    for(int i = 0; i < arr.length/2; i += 1) {
      temp = arr[i];
      arr[i] = arr[arr.length - i - 1];
      arr[arr.length - i - 1] = temp;
    }
  }
```
* In the original code, it doesn't save values in the previous index before the reverse. After the swap, the array will lose those values. By adding a variable to save the original value and replacing the target element with the saved value, we can make sure the swap function works properly (the current index exchanges value with the target index). We also want to shrink the loop into half of the string to let the swap work correctly.

# Part 2:
I choose to explore the usage of the grep command, and all info is from https://www.geeksforgeeks.org/grep-command-in-unixlinux/

## 1. grep -c  (it will list the number of the matching content)
* Example 1: list out the number of lines that has ".txt"

*Example 2: list out the number of lines that has "void", or count how many void functions in that java code


Without the -c, the grep will show all the matching lines in the file.txt file. However, when we want to know how many lines ".txt" is in a very long file, we wouldn't like to count how many lines in the command prompt. Instead, adding a -c in the grep command just tells you how many lines are matching right away. It's more useful when we try to count some patterns in a long text file. 


