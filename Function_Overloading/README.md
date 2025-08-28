# Function Overloading
Function overloading in C++ is the ability to define multiple functions with the same name but with different parameter lists (different number or types of arguments). The compiler decides which function to call based on the arguments passed.
- Same function name, but different signature (parameter type/number).
- Return type alone cannot distinguish overloaded functions.
- Improves readability and reusability.
- Example: add(int, int) and add(double, double) both exist in same program.
- If compiler cannot decide which version to call → ambiguity error.

## Basic Overloading (Different Number of Parameters)
```cpp
#include <iostream>
using namespace std;

class Print {
public:
    void show(int x) {
        cout << "Single int: " << x << endl;
    }
    void show(int x, int y) {
        cout << "Two ints: " << x << " and " << y << endl;
    }
};

int main() {
    Print p;
    p.show(10);
    p.show(10, 20);
    return 0;
}
```

## Overloading with Different Parameter Types
```cpp
#include <iostream>
using namespace std;

class Area {
public:
    void area(int r) {  // circle
        cout << "Circle area: " << 3.14 * r * r << endl;
    }
    void area(double l, double b) {  // rectangle
        cout << "Rectangle area: " << l * b << endl;
    }
};

int main() {
    Area a;
    a.area(5);
    a.area(4.5, 6.2);
    return 0;
}
```

## Constructor Overloading
```cpp
#include <iostream>
using namespace std;

class Student {
    string name;
    int age;
public:
    Student() {   // default constructor
        name = "Unknown"; age = 0;
    }
    Student(string n) {   // parameterized constructor
        name = n; age = 0;
    }
    Student(string n, int a) {
        name = n; age = a;
    }
    void display() {
        cout << "Name: " << name << ", Age: " << age << endl;
    }
};

int main() {
    Student s1;
    Student s2("Rahul");
    Student s3("Aman", 21);

    s1.display();
    s2.display();
    s3.display();
    return 0;
}
```

## Overloading vs Default Arguments (Ambiguity Example)
```cpp
#include <iostream>
using namespace std;

void show(int x, int y = 10) {
    cout << "x: " << x << ", y: " << y << endl;
}

void show(int x) {
    cout << "Only x: " << x << endl;
}

int main() {
    show(5); // ⚠️ Ambiguous: could call show(int) OR show(int, int=10)
    return 0;
}
```

## Overloading & Type Conversion (Ambiguity)
```cpp
#include <iostream>
using namespace std;

void fun(int x) {
    cout << "Int version: " << x << endl;
}

void fun(double x) {
    cout << "Double version: " << x << endl;
}

int main() {
    fun(5);     // calls int
    fun(5.5);   // calls double
    fun('a');   // ⚠️ Ambiguous: 'a' → int or double
    return 0;
}
```

## Overloading with References (C++11: Lvalue vs Rvalue)
```cpp
#include <iostream>
using namespace std;

void print(const int& x) {   // lvalue reference
    cout << "Lvalue reference: " << x << endl;
}

void print(int&& x) {        // rvalue reference
    cout << "Rvalue reference: " << x << endl;
}

int main() {
    int a = 10;
    print(a);     // lvalue → calls first
    print(20);    // rvalue → calls second
    return 0;
}
```
