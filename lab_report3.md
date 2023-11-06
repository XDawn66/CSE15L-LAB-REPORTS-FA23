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
