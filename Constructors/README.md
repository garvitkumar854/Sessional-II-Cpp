# Constructors in C++
## Default Constructor
A default constructor is a constructor that takes no arguments and initializes objects with default values. If not written, the compiler provides one automatically.
```cpp
#include <iostream>
using namespace std;

class Student {
    string name;
    int age;
public:
    Student() {   // Default Constructor
        name = "Unknown";
        age = 0;
    }
    void display() {
        cout << "Name: " << name << ", Age: " << age << endl;
    }
};

int main() {
    Student s1;   // calls default constructor
    s1.display();
    return 0;
}
```

## Parameterized Constructor
**A default constructor is a constructor that takes no arguments and initializes objects with default values. If not written, the compiler provides one automatically.**
```cpp
#include <iostream>
using namespace std;

class Student {
    string name;
    int age;
public:
    Student(string n, int a) {   // Parameterized Constructor
        name = n;
        age = a;
    }
    void display() {
        cout << "Name: " << name << ", Age: " << age << endl;
    }
};

int main() {
    Student s1("Rahul", 20);  
    s1.display();
    return 0;
}
```

## Constructor Overloading
Constructor overloading in C++ means defining multiple constructors within the same class, each having different parameter lists, allowing objects to be initialized in various ways depending on provided arguments.
```cpp
#include <iostream>
using namespace std;

class Student {
    string name;
    int age;
public:
    Student() {                 // Default
        name = "Unknown"; age = 0;
    }
    Student(string n) {         // 1 param
        name = n; age = 0;
    }
    Student(string n, int a) {  // 2 params
        name = n; age = a;
    }
    void display() {
        cout << "Name: " << name << ", Age: " << age << endl;
    }
};

int main() {
    Student s1, s2("Aman"), s3("Riya", 22);
    s1.display();
    s2.display();
    s3.display();
    return 0;
}
```

## Copy Constructor
A copy constructor in C++ is a special constructor that initializes a new object as a copy of an existing object. It takes a reference to the same class as a parameter. By default, the compiler provides a shallow copy constructor, but programmers can define their own to perform deep copying when needed.

- Special constructor used to create a copy of an object.
- Syntax: ClassName(const ClassName &obj)
- Called when passing objects by value, returning objects, or creating one object from another.
- Default copy constructor performs shallow copy (copies addresses, not data).
- User-defined copy constructor ensures deep copy (new memory allocation).
```cpp
#include <iostream>
using namespace std;

class Student {
    string name;
    int age;
public:
    Student(string n, int a) {   // Parameterized
        name = n; age = a;
    }

    Student(const Student &s) {  // Copy Constructor
        name = s.name;
        age = s.age;
    }

    void display() {
        cout << "Name: " << name << ", Age: " << age << endl;
    }
};

int main() {
    Student s1("Ravi", 21);
    Student s2 = s1;  // copy constructor called

    s1.display();
    s2.display();
    return 0;
}
```

## Constructor with Default Arguments
```cpp
#include <iostream>
using namespace std;

class Student {
    string name;
    int age;
public:
    Student(string n = "Unknown", int a = 0) {  
        name = n; age = a;
    }
    void display() {
        cout << "Name: " << name << ", Age: " << age << endl;
    }
};

int main() {
    Student s1;            // uses default args
    Student s2("Ankit");   // only name given
    Student s3("Meena", 19);

    s1.display();
    s2.display();
    s3.display();
    return 0;
}
```

## Destructor (bonus, paired with constructor)
```cpp
#include <iostream>
using namespace std;

class Demo {
public:
    Demo() {
        cout << "Constructor called!" << endl;
    }
    ~Demo() {
        cout << "Destructor called!" << endl;
    }
};

int main() {
    Demo d1;  // constructor executes
    return 0; // destructor executes automatically
}
```
