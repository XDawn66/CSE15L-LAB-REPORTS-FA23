# Question about my printing code #99

<img src="drawing.jpg" alt="drawing" width="200"/> ### StudentA
##### 1d ago in **General**

Hello, I'am confused on getting the compiling error for my program. 
Did I compile it wrong or I need to make the function static in order to make it work? Can you guys take a look?
Thanks!

My code:
```
import java.util.*;

public void print_even(int[] arr)
{
    int len = arr.length;
    for(int i = 0; i < len; i++)
    {
        if(i % 2 == 0)
        {
            System.out.println("arr: "+arr[i]);
        }
    }
}

public class Main
{
	public static void main(String[] args) {
        int [] a = new int [20];
		for (int i = 0; i < 20; i++) //initializing the array
        {
            a[i] = i;
        }
        print_even(a);
	}
}

```
The bash file code:
```
javac Code.java
java Code > data.txt
```

The error message:

![img]()

**Comment** 

# 1 Answer

<img src="drawing.jpg" alt="drawing" width="200"/> ### JoJo ***STAFF***

- First, your function is not running because the class with the name Code could not be found in the working directory. You will want to do some modification in your program in order to make the code matches the class name that you are trying to complie. 
- Second, in Java, you need to declare a function inside a class, and if you define a function in the main class, the function must be static. Otherwise, the program will not run properly.
  
Hopefully that helps! :D






