# CIDM 4390
## Description: 
Prerequisites: CIDM 2315, CIDM 3350, and CIDM4390. A capstone course for the study of software engineering, Emphasis on requirement specifications, logical design, issues in OOP, design pattern, client-server computing, project management. Students construct original and significant projects that synthesize all course experiences to produce well-designed software applications.
### Books: 

> Guide to Software Structure and Design By: Bob Martin  
> Essential Scrum: A Practical Guide to the Most Popular Agile Process By: Kenneth S. Rubin


Weekly meeting set for Wednesdays @ 6pm

# Martin Chapter 3: Paradigm Overview
- Structured Programming
    - Structured programming imposes disciplin on direct transfer of control 
- Object Oriented Programming OOP: 
    - OOP imposes disciplin on indirect transfer of control 
- Functional Programming
    - Functional Programming imposes disciplin upon assignment

# Martin Chapter 4: Structured Programming
Concept created by Edsger Wybe Dijkstra in 1968
### Proof
- Dijkstra realized early on programming was extremely difficult
- A program of any complexity contains too many
details for a human brain to manage without help. Overlooking just one small detail
results in programs that may seem to work, but fail in surprising ways.  
- Solution? Apply the matematical disciplin of **PROOF**
    - In other words, programmers would use proven structures, and tie
them together with code that they would then prove correct themselves. Accomplishing this was rather challenging. 
- Dijkstra discovered that *certain* uses of `goto` statements prevent modules from being decomposed recursively into smaller and smaller units. 
    - *Certain* `goto` statements that were considered good uses of `goto` corresponded to simple selection and iteration control structures such as `if/then/else` and `do/while`. Modules that used **only** those kinds of control structures could be recursively subdivided into provable units. 
- The very control structures that made a module provable were the same minimum set of control structures from which all programs can be built. Thus **Structured Programming** was born. 
- Nowadays we are all structured programmers, though not by choice. It's just that modern languages don't give us the option to use **undisciplined direct transfer of control** and most modern languages do not have a `goto` statement
    - Languages that still support the `goto` keyword often restrict the target to within the scope of the current function. 
- Formal proofs never actually caught on in the programming world, No one really believes it's an effective method for writing good software. Rather the scientific method is better for programming proofs. Science does not work the same as math. Science does not work by proving statements true, but rather by proving statements false. THose statements that we cannot prove false, after much effort, we deem to be true enough for our purposes. 
- ## Testing shows the presence, **not** absence of bugs
    - All that tests can do, after sufficient testing effort, is allow us to deem a program to be correct enough for our purposes. 
- STructured programming forces us to recursively decompose a program into a set of small provable functions. We can then test to try to prove those small provable functions incorrect. If such tests fail to prove incorrectness, then we deem the functions to be correct enough for our purposes. 

# Chapter 5: Object Oriented Programming (OOP)
-What is Object-oriented design (OO)?  
- The combination of data and function? 
    - argues that `o.f()` and `f(o)` are somehow different
    - false because programmers were passing data structures inot functions long before OO was created. 
- A way to model the real world? 
    - answer is too broad and loosely defined
- 3 'magic' words to describe OO: 
    1. Encapsulation
    2. Inheritance
    3. Polymorphism

## Encapsulation
OO Languages provide easy and effective encapsulation of data and function. As a result, a line can be drawn around a cohesive set of data and functions. Outside of that line, the data is hidden and only some functions are known. Concept is best seen in action with private data members and the public member functions of a `class`.
- Idea is not unique to OO, infact `C` had perfect encapsulation
```C
point.h
struct Point;
struct Point* makePoint(double x, double y);
double distance (struct Point *p1, struct Point *p2);
``` 
```C
point.c
#include "point.h"
#include <stdlib.h>
#include <math.h>
struct Point {
    double x,y;
};
struct Point* makepoint(double x, double y) {
    struct Point* p = malloc(sizeof(struct Point));
    p->x = x;
    p->y = y;
    return p;
}
double distance(struct Point* p1, struct Point* p2) {
    double dx = p1->x - p2->x;
    double dy = p1->y - p2->y;
    return sqrt(dx*dx+dy*dy);
}
```
- The users of `point.h` have no access whatsoever to the members of `struct Point.` They can call `makePoint()` function and the `distance()` function but they have absolutely no knowledge of the implementation of either `Point` data structure or functions. 
- This is perfect encapsulation...in a non-OO language. By forward declaring data structures and functions in header files, and then implement them in implementation files, the users never had access to the elements in those implementation files. 
- The `C++` compiler for technical reasons(source) needed the member variables of a class to be declared in the header file of that class. So the `Point` example changes to look like this: 
```C++
point.h
class Point {
public:
    Point(double x, double y);
    double distance(const Point& p) const;
private:
    double x;
    double y;
};
```
```C++
point.cc
#include "point.h"
#include <math.h>
Point::Point(double x, double y)
: x(x), y(y)
{}
double Point::distance(const Point& p) const {
    double dx = x-p.x;
    double dy = y-p.y;
    return sqrt(dx*dx + dy*dy);
}
```
- Clients of the header file `point.h` know about the variables `x` and `y`! The compiler prevents access to them but the client still knows they exist and encapsulation is broken. 
- Encapsulation is partially repaired by indroducing `public` `private` and `protected` keywords into the language. 
    - this was a 'hack' necessitated by the technical needs of the compiler to see those variables in the header file. 
    - `Java` and `C#` made this worse by abolishing the header/implementation split altogether. In those languages it's impossible to seperate the declaration and definition of a class. 

Hard to say that encapsulation defines OO. OO certainly does depend on the idea that programmers are well-behaved enough to not circumvent encapsulated data. Even so, the languages that claim to provid OO have only weakend the once perfect encapsulation provided by `C`. 

## Inheritance
If OO languages didn't give us better encapsulation, then they certainly gave us inheritance...kinda. 
- Inheritance is simply the redeclaration of group variables and function within an enclosing scope. 
    - `C` Programmers were able to manually do this long before there was an OO language
Consider the following addition to the original  `point.h` `C` program: 
```C
namedPoint.h
struct NamedPoint;
struct NamedPoint* makeNamedPoint(double x, double y, char* name);
void setName(struct NamedPoint* np, char* name);
char* getName(struct NamedPoint* np);
```
```C
namedPoint.c
#include "namedPoint.h"
#include <stdlib.h>
struct NamedPoint {
    double x,y;
    char* name;
};
struct NamedPoint* makeNamedPoint(double x, double y, char* name) {
    struct NamedPoint* p = malloc(sizeof(struct NamedPoint));
    p->x = x;
    p->y = y;
    p->name = name;
    return p;
}
void setName(struct NamedPoint* np, char* name) {
    np->name = name;
}
char* getName(struct NamedPoint* np) {
    return np->name;
}
```
```C
main.c
#include "point.h"
#include "namedPoint.h"
#include <stdio.h>
int main(int ac, char** av) {
    struct NamedPoint* origin = makeNamedPoint(0.0, 0.0, "origin");
    struct NamedPoint* upperRight = makeNamedPoint (1.0, 1.0, "upperRight");
    printf("distance=%f\n",
        distance(
                (struct Point*) origin,
                (struct Point*) upperRight));
}
```
- If you look carefully at the `main` program, you’ll see that the `NamedPoint` data structure
acts as though it is a derivative of the `Point` data structure. This is because the order of
the first two fields in `NamedPoint` is the same as `Point`. In short, `NamedPoint` can
masquerade as `Point` because `NamedPoint` is a pure superset of `Point` and maintains
the ordering of the members that correspond to `Point`. Note also that in `main.c`, I was forced to cast the `NamedPoint` arguments to `Point`. In a real OO language, such upcasting would be implicit.

You could argue that inheritance existed long before OO languages were invented and this is true to a fault. Inheritance in the `C` program above is acheived by some tricky workarounds and multiple inheritance is considerably more difficult to acheive this way. It’s fair to say that while OO languages did not give us something completely brand new, it did make the masquerading of data structures significantly more convenient.

## Polimorphism
Polymorphic behavior again existed before OO languages, look at the following `C` program: 
```C
#include <stdio.h>
void copy() {
    int c;
    while ((c=getchar()) != EOF)
        putchar(c);
}
```
- the function `getchar()` reads from `STDIN` but what device is `STDIN`? `putchar()` writes to `STDOUT` but what device is that? Ergo, these functions are polymorphic, the behavior of each depends on the type of `STDIN` and `STDOUT` Of course, there are no interfaces in the example C program—so how does
the call to `getchar()` actually get delivered to the device driver that reads the
character?
    - The answer to that question is pretty straightforward. The `UNIX` operating system
requires that every `IO` device driver provide five standard functions: `open`, `close`,
`read`, `write`, and `seek`. The signatures of those functions must be identical for every `IO`
driver.

The `FILE` data structure contains five pointers to functions. In our example, it might look
like this:
```C
struct FILE {
    void (*open)(char* name, int mode);
    void (*close)();
    int (*read)();
    void (*write)(char);
    void (*seek)(long index, int mode);
};
```
The IO driver for the console will define those functions and load up a FILE data
structure with their addresses—something like this:
```C
#include "file.h"
void open(char* name, int mode) {/*...*/}
void close() {/*...*/};
int read() {int c;/*...*/ return c;}
void write(char c) {/*...*/}
void seek(long index, int mode) {/*...*/}
struct FILE console = {open, close, read, write, seek};
```
Now if `STDIN` is defined as a `FILE*`, and if it points to the console data structure, then
`getchar()` might be implemented this way:
```C
extern struct FILE* STDIN;
int getchar() {
    return STDIN->read();
}
```
In other words, `getchar()` simply calls the function pointed to by the read pointer of
the `FILE` data structure pointed to by `STDIN`.

- This simple trick is the basis for all polymorphism in OO. 
    - In C++, for example, every virtual function within a class has a pointer in a table called a `vtable`, and all calls to virtual functions go through that table. Constructors of derivatives simply load theirversions of those functions into the `vtable` of the object being created.
### Polymorphism is the application of pointers to functions. 
- Programmers have been using pointers to functions to achieve polymorphic behavior since Von Neumann architectures were first implemented in the late 1940's. 
- OO languages didn't add polymorphism, but made it safer and much more convient to use. 