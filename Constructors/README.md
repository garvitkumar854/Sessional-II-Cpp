# Constructors in C++
## Default Constructor
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