__Why is there a need for throws keyword in Code 1 and not in Code 2__

# Code 1
>public class Main { <be>
> public static void main(String[] args) throws ClassNotFoundException { <br>
>        try{ <br>
>           Class.forName("com.mysql.jdbc.Driver"); <br>
>        } catch (ClassNotFoundException e) { <br>
>           System.out.println(e.getMessage()); <br>
>        } <br>
>    } <br>
>} <br>

** In Code 1 **, the main method is declared with throws ClassNotFoundException. Here’s why:

Reason for throws Keyword: The Class.forName("com.mysql.jdbc.Driver") method call can throw a ClassNotFoundException. 
By declaring throws ClassNotFoundException, the method signature informs the caller that this exception might be thrown.

Redundancy in Catch Block: Despite the throws declaration, the exception is caught and handled within the method using a try-catch block. \
The redundancy here means you wouldn’t need the throws keyword if you are handling the exception within the same method. However, it’s a common pattern to keep throws for indicating potential exceptions to the calling environment or future modifications.


# Code 2
>public class ExceptionDemo2 { <br>
>    public static void main(String[] args) {  
>        Scanner sc = new Scanner(System.in);  
>        int x= sc.nextInt();  
>        int y= sc.nextInt();  
>        int[] arr = new int[5];  
>        try{  
>            int z = x/y;  
>            try{  
>                arr[5] = z;  
>            } catch(ArrayIndexOutOfBoundsException e) {  
>                System.out.println("Exception Caught: " + e.getMessage());  
>            }  
>        }catch (ArithmeticException e){  
>            System.out.println("Exception Caught: " + e.getMessage());  
>        }  
>    }  
>}  

**In Code 2**, there is no throws keyword in the method signature.

Reason for No throws Keyword: The exceptions ArithmeticException and ArrayIndexOutOfBoundsException handled here are unchecked exceptions (runtime exceptions). 
These exceptions are not required to be declared in a method's throws clause. 
The code handles these exceptions internally using try-catch blocks.


**Summary**
Checked vs. Unchecked Exceptions:

**Checked Exceptions (like ClassNotFoundException)**
must be either caught within the method or declared in the method signature using the throws keyword.

**Unchecked Exceptions (like ArithmeticException and ArrayIndexOutOfBoundsException) **
do not need to be declared using throws, and the method can handle them directly if needed.

Exception Handling: 
Code 1 redundantly declares throws but also handles the exception within the method. 
Code 2 handles exceptions internally without needing the throws declaration due to the nature of the exceptions involved.
