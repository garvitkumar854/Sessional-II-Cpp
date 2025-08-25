# Dynamic Memory Allocation

## Dynamic Allocation Operators `new` and `delete`
```cpp
#include <iostream>
using namespace std;

int main() {
    int* p = new int;   // dynamically allocates memory for an int
    *p = 42;

    cout << "Value = " << *p << "\n";

    delete p;   // frees memory
    return 0;
}
```

## Initializing Allocated Memory
```cpp
#include <iostream>
using namespace std;

int main() {
    int* p = new int(100);   // directly initialized
    cout << "Value = " << *p << "\n"; // 100

    delete p;
}
```

## Allocating Arrays
```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter size of array: ";
    cin >> n;

    int* arr = new int[n];   // allocate array

    for (int i = 0; i < n; i++)
        arr[i] = i * 10;     // initializing

    for (int i = 0; i < n; i++)
        cout << arr[i] << " ";  // output array

    delete[] arr;   // delete array
}
```

## Allocating Objects
```cpp
#include <iostream>
using namespace std;

class Student {
public:
    string name;
    int marks;

    Student(string n, int m) {
        name = n; marks = m;
    }

    void display() {
        cout << name << " got " << marks << " marks.\n";
    }
};

int main() {
    Student* s = new Student("Aman", 95);  // allocate object dynamically
    s->display();

    delete s;  // free memory
}
```
