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
* Example 1: list out the number of lines that have ".txt" in the file.txt file
  
![image]()

![image]()

* Example 2: list out the number of lines that have "void", or for our purpose, count how many void functions in that Java code
  
![image]()

![image]()

Without the -c, the grep will show all the matching lines in the file.txt file. However, when we want to know how many lines ".txt" is in a very long file, we wouldn't like to count how many lines in the command prompt. Instead, adding a -c in the grep command just tells you how many lines are matching right away. It's more useful when we try to count some patterns in a long text file. 

## 2. grep -l  (it will list the filename of the matching content)
* Example 1: list out all the filename of files that have a pattern "for" under the lab3 directory
  
![image]()

* Example 2: list out the filename of files that have a pattern "main", or for our purpose, count how many Java programs have the main class under the lab3 directory

![image]()

The additional -l will list out the filename for files that have the matching content, it's useful if we try to find a certain program or text file but we only remember some keywords.

## 3. grep -w  (it will list lines that exactly match the whole word)
* Example 1: list out the names of files that have the whole word "for" under ArrayExamples.java
  
![image]()

* Example 2: list out the names of files that have the whole word "fo" under ArrayExamples.java
  
![image]()

The additional -w will list out the lines that have the exact matching content, it's useful if we try to find lines that have the exact keyword from a large amount of files.



