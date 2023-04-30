Download Link: https://assignmentchef.com/product/solved-ensf614-lab-5
<br>
<strong><u>Objective:</u></strong>

The purpose of this lab is to practice concept of pointer to pointers, and some of the basic object-oriented design concepts such as: aggregation, composition, polymorphism, inheritance, and multiple inheritance in C++. Course material related to exercise B will be discussed on Monday Sept 28<sup>th</sup>.

<strong><u>Marking Scheme: </u></strong>

<ul>

 <li>Exercise A: Not marked</li>

 <li>Exercise B: 20 marks Exercise C: 10 marks</li>

</ul>

<strong>Note: Material related to Exercise B will be covered on Monday Sept 30.  </strong>

<strong>Exercise A: Array of Pointers and Command Line Arguments </strong>

<strong> </strong>

<strong>Read This First: </strong>

Up to this point in our C and C++ programs, we have always used main functions without any arguments. In fact, both languages, allow us to write programs that their main functions receives arguments. Here is the heading of such a function:




int main(int argc, char **argv){ … }




Of course, we never call a main function from anywhere in our program, and we never pass arguments to it. A main function can only receive its arguments from command line. In other words, when a user runs the program from command-line, he/she can pass one or more arguments to the main. Good examples of this type of programs are many of the Linux and Unix commands such as: cp, mv, gcc, g++.  For example, the following cp command receives the name of two files, to make file f.dat a copy of file f.txt:

cp f.txt f.dat

The first token in the above cp command is the program’s executable file name, followed by two file names. This information will be accessible to the main.  How does it work? Here is the answer:




To access the command-line arguments, a C/C++ main function can have arguments as follows:




#include &lt;iostream&gt; using std::cerr;

int main(int argc, char **argv) {     if(argc != 3) {

cerr &lt;&lt; “Usage: incorrect number of argument on the command line…
””;         exit(1);

}

// MORE CODE AS NEEDED.

return 0;

}




Where, argc is the number of tokens on the command-line. In our cp command example, the value of argc should be always 3 (one for program name and two for the file names). If the value of argc is not 3, the program terminates after giving an appropriate message. In other words, this argument is mainly used for error-checking to make sure user has entered the right number of tokens on the command line. The delimiter to count for the number of tokens on the command- line is one or more spaces. The second argument is a pointer-to-pointer, which points to an array of pointers. Each pointer in this array points to one of the string tokens on the command line. The following figure shows how argv[0], argv[1], and argv[2] point to the tokens on the command line:










The following code shows how you can simply access and display the command line strings in a C++ program:

cout &lt;&lt; “The program name is: ” &lt;&lt; argv[0] &lt;&lt; endl;

cout &lt;&lt; “The first string on the command line is: ” &lt;&lt; argv[1] &lt;&lt; endl; cout &lt;&lt; “The second string on the command line is: ” &lt;&lt; argv[2] &lt;&lt; endl;

<strong> </strong>

And, here is the output of this code segment for our cp command example:

The program name is: cp

The first string on the command line is: f.txt The second string on the command line is: f.dat




The exact location of the memory allocated for command-line arguments depends on the underlying OS and the compiler, but for most of the C/C++ systems it is a special area on the stack that is not used for the activation records.




<strong>Read This Second: </strong>

Since this part of exercise-A deals with the command line entries by the user, you are <strong>strongly</strong> recommended to implement, compile and run the program on a Cygwin terminal or Mac terminal.




You may be interested in knowing whether it is possible to pass command-line arguments to your program from inside an IDE environment such as Visual C++ or XCode. The answer is yes! It is possible.




Most of the commonly used IDEs provide some way of entering the command line arguments into C/C++ project. For example, in the newer versions of the XCode for the Mac computers, you can click on the ‘Edit Scheme’, under the ‘Product’ menu option, and enter the command line argument strings on the ‘arguments’ tab.  A similar way is also available in Visual Studio: Right-click on the project, then select ‘Properties’ -&gt; Debugging, and enter your arguments into the arguments box.  If you choose to use this option, you should seek for more details by consulting the help options available on your target IDE, or search on the Internet.




Our experience shows, using the command line argument from inside some of the IDEs is not always straightforward and figuring out how exactly it works, can be sometimes time-consuming.

<strong> </strong>

<strong>What to Do: </strong>

Download the file lab5ExA.cpp from D2L. This is a simple program that uses the insertion-sort algorithm to sort an array of integer numbers. Now, you should take the following steps:

<ol>

 <li>Read the given program carefully to understand what it does.</li>

 <li>If you are using Geany, Cygwin, or Mac terminal, use the following command to create an executable file called sort:</li>

</ol>

g++ –Wall lab5ExA.cpp –o sort

<ol start="3">

 <li>Run the program using the following command: ./sort</li>

</ol>

It should print the list of several integer numbers, followed by the same list, sorted in ascending order.

<ol start="4">

 <li>Now change the value of the local variable sort_order from 1 to 2, recompile the program, and run it again. Now it should sort the array in descending order.</li>

 <li>Your task from this point is to modify the main function to have access to the command line arguments. We want to be able to run the program with the options of sorting the numbers either in ascending or descending order, based on the user’s input on the command-line.</li>

</ol>

Considering that the program’s executable name is sort, users must be able to run the program from the commandline in one of the following formats:

./sort  -a

Or:

./sort  -d




In the first command the option –a (no spaces between dash and a) stands for the ascending, and the second command with the option –d stands for the descending order.

Depending on the user’s selection of one of these options, the program must sort an array accordingly.

To be more precise, the main function in this program must check the following conditions:

<ul>

 <li>If argc &gt; 2 the program should give the following message and terminate:</li>

</ul>

Usage: Too many arguments on the command line




<ul>

 <li>If argc == 1, (meaning that the user didn’t enter any of the two options), the program should use ascending sort as its default order.</li>

</ul>




<ul>

 <li>If argv[1], is NOT one of the following: –a, -A, -d, or –D, the program should give the following message and terminate:</li>

</ul>

Usage: Invalid entry for the command line option. Then, the program should:

<ul>

 <li>Set the value of sort_order to 1, if argv[1] points to the C-string: “–a” or “-A”.</li>

 <li>Set the value of sort_order to 2, if argv[1] points to the C-string: “–d” or “-D”.</li>

</ul>




<strong>Note</strong>: as you should recall from material discussed earlier in the course, you cannot compare C-strings by simply using relational operators. Therefore, you need to call C library function strcmp. You may refresh your memory regarding this function by reading your course notes, any of your textbooks, or an online sources such as cplusplus.com at: <u>http://www.cplusplus.com/reference/cstring/strcmp</u>.

<strong> </strong>

<strong>What to Submit: </strong>




You don’t need to submit anything for this exercise.

<strong> </strong>

<h1>Exercise B – Inheritance in C++</h1>

<strong> </strong>

The concepts of aggregation, composition, and inheritance in C++ and Java in terms of concepts are similar, but they are completely different in terms of implementation and syntax. Also, another major difference between the two languages is that C++ unlike Java supports multiple-inheritance. <strong> </strong>




<strong>What to Do: Single Inheritance in C++: </strong>

In this exercise, first you will write the definitions of following classes: Point, Shape, Rectangle, Square, GraphicsWorld, as explained below.

<strong> </strong>

<strong>Class Point: </strong>

This class is supposed to represent a point in a Cartesian plane. It should have three data members: <strong>x</strong>, and <strong>y</strong> coordinates and an <strong>id</strong> number that its value will be assigned automatically. The first object’s <strong>id </strong>number should be 1001, second one should be 1002, and so on. Class Point should also have at least the following member functions: <strong> </strong>

<ul>

 <li>display – that displays x, and y coordinates of the point in the following format:</li>

</ul>

X-coordinate: ######.##

Y-coordinate: ######.##

<ul>

 <li>A constructor that initializes its data members.</li>

</ul>

<strong>Note:</strong> <strong>You are not supposed to define a default constructor in this class. Automatic calls to the default constructor will hide some of the important aspects of this assignment (marks will be deducted if you define a default constructor for this class). </strong>




<ul>

 <li>Access functions, getters and setters, as needed.</li>

</ul>




<ul>

 <li>Function counter()that returns the number of objects of class Point at any time.</li>

</ul>




<ul>

 <li>Two distance functions that return the distance between two points. One of the two must be a static function.</li>

</ul>




You should create two files for this class: called point.h and point.cpp

<strong> </strong>

<strong> </strong>

<strong>Class Shape</strong>:

This class is the base class or the ancestor of several classes, including class Rectangle, Square, Circle, etc. It should support basic operations and structures that are common among the children of this class. This class should have an object of class Point called origin, and a char pointer called shapeName that points to a dynamically allocated memory space, allocated by the class constructor.  This class should also have several functions and a constructor as follows: –         A constructor that initializes its data members.

<ul>

 <li><strong>No default constructor </strong></li>

 <li>A destructor that de-allocates the memory space allocated dynamically for shapeName</li>

 <li>getOrigin – that returns a reference to point origin. The reference should not allow the x and y values of point to be modified through this reference.</li>

 <li>getName – that returns the name of the shape.</li>

 <li>display – that prints on the screen the shape’s name, x and y coordinates of point origin,  in the following format:</li>

</ul>

Shape Name:

X-coordinate:

Y-coordinate:

<ul>

 <li>two distance functions double distance (Shape&amp; other);</li>

</ul>

static double distance (Shape&amp; the_shape, Shape&amp; other);

<ul>

 <li>move: that changes the position of the shape, the current x and y coordinates, to x+dx, and y+dx. The function’s interface (prototype) should be;</li>

</ul>

void move (double dx, double dy);




You should create two files for this class: called shape.h and shape.cpp

<strong> </strong>

<strong>Class Square: </strong>

This class is supposed to be derived from class Shape, and should have one data member, called side_a, and in addition to its constructor should have a constructor and several member functions as follows:

<ul>

 <li>One constructor that initializes its data members with its arguments supplied by the user.</li>

 <li><strong>No default constructor</strong>. Marks will be deducted if a default constructor is defined for this class</li>

 <li>area – that returns the area of a square</li>

 <li>perimeter: that returns the perimeter of a square – get and set – as needed.</li>

 <li>display – that displays the name, x and y coordinates of the origin, side_a, area, and perimeter of a square object in the following format:</li>

</ul>

Square Name:

X-coordinate:

Y-coordinate:

Side a:

Area:

Perimeter;

<ul>

 <li>More Functions, if needed.</li>

</ul>




You should create two files for this class: called square.h and square.cpp




<strong>Class Rectangle: </strong>

Class Rectangle that is derived from class Square needs to have one more side called side_b. This class, in addition to its constructor (no default constructor), should support the following functions:

<ul>

 <li>area – that calculates and returns the area of a rectangle</li>

 <li>perimeter – that calculates and returns the perimeter of a rectangle</li>

 <li>get and set – that retrieves or changes the values of its private data members.</li>

 <li>display – that displays the name, and x and y coordinate origin of the shape, side_a, side_b, area, and perimeter of a rectangle object, in the following format:</li>

</ul>

Rectangle Name:

X-coordinate:  Y-coordinate:

Side a:

Side b:

Area:

Perimeter;

<ul>

 <li>More Functions, if needed.</li>

</ul>

You should create two files for this class: called rectangle.h and rectangle.cpp

<strong> </strong>

<strong>Class GraphicsWorld</strong>:

This class should have only a function called <em>run</em>, which declares instances of the above-mentioned classes as its local variable. This function should first display a short message about the author(s) of the program and then start testing all of the functions of the classes in this system.  A sample code segment of function <em>run</em> is given below.  You are recommended to use conditional compilation directives to test your code (one class at a time).




<table width="676">

 <tbody>

  <tr>

   <td width="676">void GraphicsWorld::run(){#if 0               // Change 0 to 1 to test PointPoint m (6, 8);         Point n (6,8);         n.setx(9);cout &lt;&lt; “
Expected to dispaly the distance between m and n is: 3”; cout &lt;&lt; “
The distance between m and n is: ” &lt;&lt;      m.distance(n); cout &lt;&lt; “
Expected second version of the distance function also print: 3”;  cout &lt;&lt; “
The distance between m and n is again: ”&lt;&lt; Point::distance(m, n);#endif             // end of block to test Point#if 0               // Change 0 to 1 to test Squarecout &lt;&lt; “

Testing Functions in class Square:” &lt;&lt;endl;     Square s(5, 7, 12, “SQUARE – S”);s.display();#endif             // end of block to test Square #if 0               // Change 0 to 1 to test Rectangle         cout &lt;&lt; “
Testing Functions in class Rectangle:”;         Rectangle a(5, 7, 12, 15, “RECTANGLE A”);         a.display();Rectangle b(16 , 7, 8, 9, “RECTANGLE B”);         b.display();double d = a.distance(b); cout &lt;&lt;“
Distance between square a, and b is: ” &lt;&lt; d &lt;&lt; endl;Rectangle rec1 = a;         rec1.display();cout &lt;&lt; “
Testing assignment operator in class Rectangle:” &lt;&lt;endl;Rectangle rec2 (3, 4, 11, 7, “RECTANGLE rec2”); rec2.display(); rec2 = a;a.set_side_b(200);a.set_side_a(100);cout &lt;&lt; “
Expected to display the following values for objec rec2: ” &lt;&lt; endl; cout &lt;&lt; “Rectangle Name: RECTANGLE A
” &lt;&lt; “X-coordinate: 5
”  &lt;&lt; “Y-coordinate: 7
”          &lt;&lt; “Side a: 12
” &lt;&lt; “Side b: 15
” &lt;&lt; “Area: 180
” &lt;&lt; “Perimeter: 54
” ; cout &lt;&lt; “
If it doesn’t there is a problem with your assignment operator.
” &lt;&lt; endl; rec2.display(); cout &lt;&lt; “
Testing copy constructor in class Rectangle:” &lt;&lt;endl;Rectangle rec3 (a); rec3.display();a.set_side_b(300);a.set_side_a(400);cout &lt;&lt; “
Expected to display the following values for objec rec2: ” &lt;&lt; endl;cout &lt;&lt; “Rectangle Name: RECTANGLE A
” &lt;&lt; “X-coordinate: 5
”  &lt;&lt; “Y-coordinate: 7
” &lt;&lt; “Side a: 100
” &lt;&lt; “Side b: 200
” &lt;&lt; “Area: 20000
” &lt;&lt; “Perimeter: 600
” ; cout &lt;&lt; “
If it doesn’t there is a problem with your assignment operator.
” &lt;&lt; endl;</td>

  </tr>

  <tr>

   <td width="676">rec3.display();#endif              // end of block to test Rectangle #if 0               // Change 0 to 1 to test using array of pointer and polymorphism cout &lt;&lt; “
Testing array of pointers and polymorphism:” &lt;&lt;endl;Shape* sh[4]; sh[0] = &amp;s; sh[1] = &amp;b; sh [2] = &amp;rec1; sh [3] = &amp;rec3; sh [0]-&gt;display(); sh [1]-&gt;display(); sh [2]-&gt;display(); sh [3]-&gt;display();#endif             // end of block to test array of pointer and polymorphism</td>

  </tr>

 </tbody>

</table>




You should create two files for this class: called graphicsWorld.h and graphicsWorld.cpp

<strong> </strong>

<strong>What to Submit for Exercise B:  </strong>

As part of your lab report (PDF file) submit:  your source codes (.cpp and .h files) and the program output showing your code in exercise A.Also submit a zipped file that contains your source files: .cpp and .h for all your classes.

<strong> </strong>

<h1>Exercise C – Multiple-Inheritance</h1>




This exercise is the continuation of exercise B. You have to complete exercise A and then start this exercise.




C++ allows a class to have more than one parent:




This is called multiple inheritance.  For example, if we have two classes called B and C, and class D is derived for both classes (B and C), we say class D has two parents (multiple inheritance).  This is a powerful feature of C++ language that other languages such as Java do not support. For the details please refer to your class notes.




<strong>What to Do  </strong>




In this exercise you should add two new classes to your program:

<strong> </strong>

<strong>Class Circle: </strong>

This class is supposed to be derived from class Shape, and should have a data member radius, and in addition to its constructor it should support the similar functions as class Rectangle, such as area, perimeter, get, set, and display.







You should create two files for this class: called circle.h and circle.cpp




<strong>Class CurveCut: </strong>

<strong>CurveCut</strong> represents a shape that needs properties of class Rectangle and class Circle. In fact it’s a rectangle that its left top corner can have an arch-form cut  (see the following picture).




This class must be derived from class Rectangle and class Circle. Where the origins (x and y coordinates) of both shapes are the same.  This class in addition to a constructor should support the following functions:

<ul>

 <li>area – that calculates the highlighted area of the above figure.</li>

 <li>perimeter – that calculates and returns the perimeter of highlighted areas.</li>

 <li>display – that displays the name, x, y coordinates of origin of the shape, width and length (as shown in the picture above), and radius of the cut, in the following format:</li>

</ul>

CurveCut Name:   X-coordinate:

Y-coordinate:

Width:

Length:

Radius of the cut.

Note: The radius of the circle must be always less than or equal the smaller of the width and length. Otherwise, program should display an error message and terminate.




You should also add some code to function run in class GraphicsWorld to:

<ul>

 <li>test the member functions of class CurveCut.</li>

 <li>use an array of pointers to Shape objects, where each pointer points to a <strong>different object</strong> in the shapes hierarchy. Then test the functions of each class again.</li>

</ul>




A sample code segment that you can use to test your program is given in the following box (you can add more codes to this function if you want to show additional features of your program).

<table width="676">

 <tbody>

  <tr>

   <td width="676">void GraphicsWorld::run(){/****************************ASSUME CODE SEGMENT FOR EXERCISE A IS HERE ************************/#if 0cout &lt;&lt; “
Testing Functions in class Circle:” &lt;&lt;endl;      Circle c (3, 5, 9, “CIRCLE C”);c.display();cout &lt;&lt; “the area of ” &lt;&lt; c.getName() &lt;&lt;” is: “&lt;&lt; c.area() &lt;&lt; endl;cout &lt;&lt; “the perimeter of ” &lt;&lt; c.getName() &lt;&lt; ” is: “&lt;&lt; c.perimeter() &lt;&lt; endl;      d = a.distance(c);cout &lt;&lt; “
The distance between rectangle a and circle c is: ” &lt;&lt;d;CurveCut rc (6, 5, 10, 12, 9, “CurveCut rc”);         rc.display();cout &lt;&lt; “the area of ” &lt;&lt; rc.getName() &lt;&lt;” is: “&lt;&lt; rc.area();         cout &lt;&lt; “the perimeter of ” &lt;&lt; rc.getName() &lt;&lt; ” is: “&lt;&lt; rc.perimeter();       d = rc.distance(c);cout &lt;&lt; “
The distance between rc and c is: ” &lt;&lt;d;  // Using array of Shape pointers:      Shape* sh[4];         sh[0] = &amp;s;    sh[1] = &amp;a;         sh [2] = &amp;c;  sh [3] = &amp;rc;         sh [0]-&gt;display();cout &lt;&lt; “
the area of “&lt;&lt; sh[0]-&gt;getName() &lt;&lt; “is: “&lt;&lt; sh[0] -&gt;area();cout &lt;&lt; “
the perimeter of ” &lt;&lt; sh[0]-&gt;getName () &lt;&lt; ” is: “&lt;&lt; sh[0]-&gt;perimeter();         sh [1]-&gt;display();cout &lt;&lt; “
the area of “&lt;&lt; sh[1]-&gt;getName() &lt;&lt; “is: “&lt;&lt; sh[1] -&gt;area();cout &lt;&lt; “
the perimeter of ” &lt;&lt; sh[0]-&gt;getName () &lt;&lt; ” is: “&lt;&lt; sh[1]-&gt;perimeter();         sh [2]-&gt;display();cout &lt;&lt; “
the area of “&lt;&lt; sh[2]-&gt;getName() &lt;&lt; “is: “&lt;&lt; sh[2] -&gt;area();cout &lt;&lt; “
the circumference of ” &lt;&lt; sh[2]-&gt;getName ()&lt;&lt; ” is: “&lt;&lt; sh[2]-&gt;perimeter();</td>

  </tr>

  <tr>

   <td width="676">     sh [3]-&gt;display();cout &lt;&lt; “
the area of “&lt;&lt; sh[3]-&gt;getName() &lt;&lt; “is: “&lt;&lt; sh[3] -&gt;area();cout &lt;&lt; “
the perimeter of ” &lt;&lt; sh[3]-&gt;getName () &lt;&lt; ” is: “&lt;&lt; sh[3]-&gt;perimeter(); cout &lt;&lt; “
Testing copy constructor in class CurveCut:” &lt;&lt;endl;CurveCut cc = rc;         cc.display(); cout &lt;&lt; “
Testing assignment operator in class CurveCut:” &lt;&lt;endl;CurveCut cc2(2, 5, 100,  12, 9,  “CurveCut cc2”);        cc2.display();        cc2 = cc;cc2.display();#endif}       // END OF FUNCTION run</td>

  </tr>

 </tbody>

</table>

<strong> </strong>

<strong>What to Submit for Exercise B: </strong>

<ol>

 <li>As part of your lab report (PDF file) submit: Copy of your complete source codes (.cpp and .h files), and the program output showing your code in exercise B works.</li>

</ol>

A zipped file with source file: All .cpp and .h files