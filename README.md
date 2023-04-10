Below is a running total list of programs along with their explanations that I have written in Computer Science II. Individual README.md files found in assignment folders as well.
- Assignment 1: Basic computation & slow converging series fit into a double
- Assignment 2: Calculus application, recursions, polynomials, error bound calculations, pi manipulation and derivation, recursive root approximation
- Assignment 3: Model-View-Controller Architecture designed GUI minesweeper, representing Sierpinski's Triangle fractal via a recursive GUI, simple graphics
- Assignment 4: Encryption & decryption on text files using Caesar's Cipher & Vignere Cipher, simple GUI web browser which opens a socket and pipes data down a stream, robot teleoperation and simulating translating movements into differential rotor speeds via a GUI controller
- Assignment 5: Refactor minesweeper architecture to convert a game to bytes so that it can be saved and loaded through an OS's filesystem, Webserver on port 8080 which opens a socket on the client and server end so that it can display an local html file off an OS's filesystem, analysis of merge sort and bubble sort algorithms computed in O(n), O(n^2), and O(nlogn) time
# Assignment 1
## Greeting.java , Average.java , Fib.java , Gregory.java
### Not Hello World - Greeting.java
It can say anything, except for “Hello, world!”

To run the program, use the following command in your terminal:
```
$ java Greeting
```
The output should be:
```
¡Hola, mundo!
```
### Statistics - Average.java
Allows the user to continue to enter numbers until they respond with a negative number. Prints out how many numbers the user entered (not including the negative one), and the average of those numbers.

To run the program, use the following command in your terminal:
```
$ java Average
Enter a series of numbers. Enter a negative number to quit.
1
2
4.5
3
5
-1
```
The output should be:
```
You entered 5 numbers averaging 3.1.
```
### Fibonacci numbers - Fib.java
The Fibonacci sequence is a famous mathematical sequence where each successive term is the sum of the two preceding ones. Using the Scanner object, this program allows a user to enter a number n as a command-line argument, and will print out the nth Fibonacci term.

To run the program, use the following command in your terminal:
```
$ java Fib 4
```
The output should be:
```
3
```
### Investigations into π - Gregory.java
The Gregory series is a series converging to a π/4. This program takes a number n specified by the user (via the command line) and calculates π using the first n terms of the Gregory series, prints the approximated value of π, as well as the percentage error between this value and the one provided by Java in the constant Math.PI.

To run the program, use the following command in your terminal:
```
$ java Gregory 10
```
The output should be:
```
Pi according to Gregory series: 3.0418396189294032
This differs from Java’s value by 3.175237710923643 percent.
```
# Assignment 2
## Factorial.java , FibTest.java , Ramanujan.java, FunctionTest.java , Poly.java , Function.java , RamanujanBig.java , SinFunc.java , CosFunc.java , PolyFunc.java
### Factorial - Factorial.java
Contains a method ***public static long calculate(long n)*** which recursively calculates n!, where 0! = 1 and n! = n(n − 1)!. Prints out an error 
and exits if n < 0 or n > 20, since factorial is not defined for negative numbers and will overflow Java’s long variable with larger numbers.
```
long result1 = Factorial.calculate(0);
System.out.println("Factorial.calculate(0) returned " + result1 + ". Test passed!");

long result2 = Factorial.calculate(5);
System.out.println("Factorial.calculate(5) returned " + result2 + ". Test passed!");
```
Output:
```
Factorial.calculate(0) returned 1. Test passed!
Factorial.calculate(5) returned 120. Test passed!
```
### Fibonacci revisted - FibTest.java
Contains two methods for calculating Fibonacci nth term: ***public static int fibIter(int n)*** and 
***public static int fibRecur(int n)*** which use an iterative and recursive approach, respectively.
Will also test both methods and prints out the time it takes to execute each method for the input 40.
```
int result1 = FibTest.fibIter(7);
System.out.println("FibTest.fibIter(7) returned " + result1 + ". Test passed!");

int result2 = FibTest.fibRecur(7);
System.out.println("FibTest.fibRecur(7) returned " + result2 + ". Test passed!");
```
Output:
```
FibTest.fibIter(7) returned 13. Test passed!
FibTest.fibRecur(7) returned 13. Test passed!
ms to execute FibTest.fibIter(40): <Varies by device>
ms to execute FibTest.fibRecur(40): <Less than fibIter(40)>
```
### π revisited - Ramanujan.java
Ramanujan's approximation for 1/π converges ***much*** faster than the Gregory series. This program 
takes a number n specified by the user on the command line and 
calculates π using the first n terms of the Ramanujan series. Prints this approximate value of π, 
as well as the percentage error between this value and the one provided by Java in the constant Math.PI.

To run the program, use the following command in your terminal:
```
$ java Ramanujan 1
```
The output will be:
```
Pi according to Ramanujan series: 3.1415926535897936
This is error bound from Java's value by 2.842170943040401E-14 percent
```
### Ramanujan series represented w/ BigDecimal class - RamanujanBig.java
Interestingly, this method creatively makes use of my Polynomial and Root class to retrieve the necessary approximation of sqrt(2) constant in the
Ramanujan series. By using BigDecimal class, we can estimate π to a larger number of digits.

To run the program, use the following command in your terminal:
```
java RamanujanBig 3
```
The output will be:
```
Pi according to Ramanujan series: 3.1415926535897932384626433832795028841971693993751
```
### Root finding - FunctionTest.java
Contains a method ***public static double findRoot(double a, double b, double epsilon)*** 
which uses the bisection method to find the root of the Math.sin() function between two given values with a given level of tolerance.

Tests the root of the particular function sin(x) that falls between 3 and 4, to within 0.00000001.
```
double result = FunctionTest.findRoot(3, 4, 0.00000001);
System.out.println("FunctionTest.findRoot(3, 4, 0.00000001) returned " + result + ".");
```
Output:
```
FunctionTest.findRoot(3, 4, 0.00000001) returned 3.1415926519626075.
```
### Polynomial - Poly.java
***Extremely*** useful throughout many classes. 
Contains a Java class Poly that represents polynomials 
(i.e., functions of the form ax^n + bx^(n-1) + ... + cx^2 + dx + e).

***Poly(int[] coefficients)***: Constructor for an array of coefficients where c[n] is the coefficient of x^n. In other words, 
polynomial 2x^5 + 3x^4 - 8x^2 + 4 would be represented by the array ***[4, 0, -8, 0, 3, 2]***.

***int degree()***: Returns the power of the highest non-zero term.

***String toString()***: Returns a string representation of the polynomial using x as the variable, 
arranged in decreasing order of exponent and printing nothing for terms with a coefficient of zero. For example, 
the Poly represented by the array ***[4, 0, -8, 0, 3, 2]*** should return the string: ***2x^5+3x^4-8x^2+4***.

***Poly add(Poly a)***: Constructs and returns a new Poly object with a new coefficient array 
created by adding the coefficients of the current object and the Poly object passed as an argument to the ***add()*** function.

***double evaluate(double x)***: Returns the value of the function at the point x.
Additionally, the project contains a main method to test each of the methods.

### Inheritance implementation - Function.java, SinFunc.java, CosFunc.java, PolyFunc.java, 
In this part of the project, I extend the functionality of the Function class. The Function class supports an abstract method:
```
public abstract double evaluate(double x)
```
***FunctionTest.findRoot()*** method is refactored to belong to the Function class. 

***evaluate()*** method replaces the use of ***Math.sin()*** in ***findRoot()*** method. A new class SinFunc is created, which extends Function and implements ***evaluate()*** using ***Math.sin()***. 
Similarly, CosFunc is created, which implements ***Math.cos()***. Lastly, I create a new class PolyFunc which extends Function and implements the 
***evaluate()*** method for polynomials.

The implemented abstract method ***public abstract double evaluate(double x)*** evaluates a given function at a particular point x.
The SinFunc, CosFunc, and PolyFunc classes each extend Function and implement their respective evaluate() method. These classes contain no additional methods.
 
In ***Function.main()***, I verify that the root of sin(x) between 3 and 4 is the same as it was before, and find the root of cos(x) between 1 and 3. 
I also find the positive root (x > 0) of x^2 - 3 and x^2 - x - 2.
```
Function sin = new SinFunc();
System.out.println(sin.findRoot(3, 4, 0.00000001));
		
Function cos = new CosFunc();
System.out.println(cos.findRoot(1, 3, 0.00000001));
		
int[] coef1 = {-3, 0, 1};
int[] coef2 = {-2, -1, 1};
Function polynomial1 = new PolyFunc(coef1);
Function polynomial2 = new PolyFunc(coef2);
		
System.out.println(polynomial1.findRoot(1,2, 0.000000001));
System.out.println(polynomial2.findRoot(1,3, 0.000000001));
```
Yields:
```
3.1415926590561867
1.5707963332533836
1.7320508072152734
2.0000000009313226
```
### Convenient Utilities - ConvenciencyMethods.txt
Contains some discarded convenient methods used to complete this assignment. Class not runnable, but methods inside can be implemented in other projects.

***public int[] getDegreesArray(int[] c)*** method returns the array of degrees to link to their corresponding coefficients for the Poly class.

***public HashMap<Integer,Integer> getDegreesMap(int[] c)*** method takes an array as an argument and returns a HashMap of coefficients linked to 
the value of their degrees.

***public int[] reverse(int[] arr, int arr_length)*** simple but powerful method to reverse an array. Extremely useful when dealing with polynomials.

# Assignment 3
## Minesweeper.java, MinesweeperPanel.java, MinesweeperBoard.java, MinesweeperFrame.java, Sierpinski.java, SierpinskiFrame.java, SierpinskiPanel.java, Message.java, MessageFrame.java, MessagePanel.java
- imports javax.swing.\*, java.awt.\*, java.awt.event.*, etc.

### Minesweeper ~ Model-View-Controller Architecture
This program implements a simple GridLayout of JButtons (View) with MouseHandlers with inner ***private class MinesweeperMouseListener*** extending ***MouseAdapter*** (Controller). The inner class overrides ***mouseClicked()*** and recognizes the ***MouseEvent*** of the interacted JButton so that it is differentiable between left clicks and right clicks (defined by final BUTTON1 and final BUTTON3). The Model stores all of the gameplay aspects and methods to be called in the controller ***MinesweeperMouseListener***. The MinesweeperBoard initializes the new game by assigning a particular JButton to "Mine" based on an interchangable probability of 12.5%. The MinesweeperBoard defines mines and safe squares by assigning integer -1 (mine) and 0 (non-mine). These values are communicated to the controller via a java HashMap<JButton, Integer> which organizes well in terms of the communication occurring inside ***MinesweeperMouseListener***.

To launch Minesweeper.java, open your terminal and run:
```
$ java Minesweeper
```
It will launch 10x10 Minesweeper game, which, for example, looks like this if played out:

![Minesweeper](https://i.imgur.com/qNGgctG.png)

### Sierpinski's Triangle ~ Representing Recursive Fractals with a GUI
This program contains an overridden ***paintComponent*** method which determines the length of the smallest dimension of your resizable window by utilizing functions ***getWidth()*** and ***getHeight()***. This length (represented by **int length = minDimension**) is passed into method ***drawSierpinski()*** which takes arguments of the **Graphics** object from ***paintComponent()***, int x, int y, and int length. This is a recursive method where the base case calls ***fillRect(x,y,1,1)*** on the Graphics object passed, which draws a square the size of a single pixel at coordinates x and y. The else{} contains 3 recursive calls, which will draw a square on the left (x, y+1/2(length)), on the right (x + 1/2(length), y + 1/2(length)), and on the top (x + 1/4(length), y), where length is approaching the base case ***length == 1*** by recursive halves.

To launch Sierpinski.java, open your terminal and run:
```
$ java Sierpinski
```
It will launch a window initialized to 300x200 pixels, displaying Sierpinski's Triangle. The GUI will repaint based on resizing of the window to display the recursive fractal. It will look something like this:

![Sierpinski](https://i.imgur.com/M5yBR76.png)

![Sierpinski](https://i.imgur.com/6NqGjFx.png)

### Message ~ A Simple GUI Graphic
This is a simple graphic that draws a "Message in a bottle". The program contains a panel that overrides ***paintComponent()*** and passes in a **Graphics** object. The program calls a handful of ***draw()*** methods to create the "Message in a bottle" displayed when the program is launched. The MessagePanel extending JPanel is added to the MessageFrame extending JFrame which closes on exit, initialized to 500x500 pixels, and titled "Message in a bottle".

To launch Message.java, open your terminal and run:
```
$ java Message
```
It will launch a GUI program that displays:

![Message](https://i.imgur.com/Vyms4YB.png)
