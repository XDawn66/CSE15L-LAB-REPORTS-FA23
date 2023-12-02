# Question about my printing code #99

### StudentA
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

The data.txt:
```
```

The error message:

![img]()

**Comment** 

# 1 Answer
### JoJo ***STAFF***
#### 1h ago

- First, your function is not running because the class with the name Code could not be found in the working directory. You will want to do some modification in your program in order to make the code matches the class name that you are trying to complie. 
- Second, in Java, you need to declare a function inside a class, and if you define a function in the main class, the function must be static. Otherwise, the program will not run properly.
  
Hopefully that helps! :D

**Comment** 

 ##### StudentA
 Based on what you said, I changed the name of my class inside the program and made it the same as my program name, and it works! Just like you said, if I don't put my function into a class, the program indeed produces an error about the unnamed class. I moved that into the main class and tried to make the function static, and my program works now. The bugs for the 

Correct code:
```
import java.io.IOException;
import java.net.URI;
import java.io.*;
import java.util.*;

class Handler implements URLHandler {

    String result ="";
    int index = 1;


    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return String.format(result);
        } 
         else 
         {
            if (url.getPath().contains("/add-message")) {
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                   result += index + ". " + parameters[1] + "\n\n";
                   index++;
                   return String.format(result);
                }
            }
             return "404 Not Found!";
         } 
        
    }
}

class stringserver {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}


```




