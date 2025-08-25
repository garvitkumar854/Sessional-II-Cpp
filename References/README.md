# References

## References in C++

### References (Basic)
```cpp
#include <iostream>
using namespace std;

int main() {
    int x = 10;
    int& ref = x;   // reference to x

    ref = 20;       // changes x also
    cout << "x = " << x << "\n";  // 20
    cout << "ref = " << ref << "\n";  // 20
}
```

### Reference Parameters
```cpp

(Passing variables by reference to avoid copying)

#include <iostream>
using namespace std;

void increment(int& n) {   // reference parameter
    n++;
}

int main() {
    int a = 5;
    increment(a);   // modifies original 'a'
    cout << "a = " << a << "\n";  // 6
}
```

### Passing References to Objects
```cpp
#include <iostream>
using namespace std;

class Student {
public:
    string name;
    int marks;

    void display() {
        cout << name << " got " << marks << " marks.\n";
    }
};

void updateMarks(Student& s) {   // reference to object
    s.marks += 10;
}

int main() {
    Student s1 = {"Aman", 80};
    updateMarks(s1);   // changes actual object
    s1.display();      // Aman got 90 marks.
}
```

### Returning References
```cpp

(Useful when we want to modify original variable)

#include <iostream>
using namespace std;

int& getElement(int arr[], int index) {
    return arr[index];   // returns reference
}

int main() {
    int arr[5] = {10,20,30,40,50};

    getElement(arr, 2) = 99;  // modifies arr[2]
    cout << arr[2] << "\n";   // 99
}
```

### this Pointer
```cpp

(this is an implicit pointer to the calling object)

#include <iostream>
using namespace std;

class Box {
    int length;
public:
    Box(int l) { this->length = l; }   // using this pointer

    Box& setLength(int l) {   // returning *this (reference)
        this->length = l;
        return *this;         // allows chaining
    }

    void show() { cout << "Length = " << length << "\n"; }
};

int main() {
    Box b(10);
    b.show();

    b.setLength(20).show();   // method chaining
}