# Arrays
## Basics Of Arrays
### Declaring Arrays
```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[5] = {1, 2, 3, 4, 5};   // declaration + initialization

    cout << "Array elements: ";
    for(int i=0; i<5; i++) {
        cout << arr[i] << " ";
    }
    return 0;
}
```

### Traversing Arrays (for & while loop)
```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[5] = {10, 20, 30, 40, 50};

    cout << "Using for loop: ";
    for(int i=0; i<5; i++) {
        cout << arr[i] << " ";
    }

    cout << "\nUsing while loop: ";
    int i=0;
    while(i < 5) {
        cout << arr[i] << " ";
        i++;
    }
    return 0;
}
```

### Multidimensional Array (2D Array)
```cpp
#include <iostream>
using namespace std;

int main() {
    int a[3][3] = {
        {1, 2, 3},
        {4, 5, 6},
        {7, 8, 9}
    };

    cout << "2D Array:\n";
    for(int i=0; i<3; i++) {
        for(int j=0; j<3; j++) {
            cout << a[i][j] << " ";
        }
        cout << endl;
    }
    return 0;
}
```

### Array as Function Argument
```cpp
#include <iostream>
using namespace std;

// Function taking array as argument
void printArray(int arr[], int n) {
    for(int i=0; i<n; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;
}

int main() {
    int arr[5] = {5, 10, 15, 20, 25};
    cout << "Array elements: ";
    printArray(arr, 5);  // passing array to function
    return 0;
}
```
--------------------------------------------

## Arrays of Objects

### Storing Objects in an Array
```cpp
#include <iostream>
using namespace std;

class Book {
public:
    string title;
    int price;
};

int main() {
    Book b[3]; // array of objects

    b[0] = {"C++ Basics", 400};
    b[1] = {"OOP Concepts", 550};
    b[2] = {"DSA in C++", 700};

    cout << "Books stored successfully.\n";
    return 0;
}
```

### Input/Output for Array of Objects
```cpp
#include <iostream>
using namespace std;

class Book {
public:
    string title;
    int price;

    void input() {
        cout << "Enter title & price: ";
        cin >> title >> price;
    }

    void display() {
        cout << "Title: " << title << ", Price: " << price << endl;
    }
};

int main() {
    Book b[3];

    cout << "Enter details of 3 books:\n";
    for(int i=0; i<3; i++) {
        b[i].input();
    }

    cout << "\nBooks entered:\n";
    for(int i=0; i<3; i++) {
        b[i].display();
    }

    return 0;
}
```

### Searching / Filtering Objects (Books with price > 500)
```cpp
#include <iostream>
using namespace std;

class Book {
public:
    string title;
    int price;

    void input() {
        cout << "Enter title & price: ";
        cin >> title >> price;
    }
};

int main() {
    Book b[5];

    for(int i=0; i<5; i++) {
        b[i].input();
    }

    cout << "\nBooks with price > 500:\n";
    for(int i=0; i<5; i++) {
        if(b[i].price > 500) {
            cout << b[i].title << " - " << b[i].price << endl;
        }
    }
    return 0;
}
```

### Finding Max (Employee with Highest Salary)
```cpp
#include <iostream>
using namespace std;

class Employee {
public:
    int id;
    string name;
    int salary;

    void input() {
        cout << "Enter ID, Name, Salary: ";
        cin >> id >> name >> salary;
    }
};

int main() {
    int n;
    cout << "Enter number of employees: ";
    cin >> n;

    Employee e[n];

    for(int i=0; i<n; i++) {
        e[i].input();
    }

    // Find max salary
    int maxIndex = 0;
    for(int i=1; i<n; i++) {
        if(e[i].salary > e[maxIndex].salary) {
            maxIndex = i;
        }
    }

    cout << "\nEmployee with highest salary:\n";
    cout << e[maxIndex].id << " " << e[maxIndex].name 
         << " " << e[maxIndex].salary << endl;

    return 0;
}
```
---------------------------------------------------

## Pointers with Arrays

### Relationship: arr[i] = *(arr+i)
```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[5] = {10, 20, 30, 40, 50};

    cout << "Access using arr[i]: ";
    for(int i=0; i<5; i++) {
        cout << arr[i] << " ";
    }

    cout << "\nAccess using *(arr+i): ";
    for(int i=0; i<5; i++) {
        cout << *(arr+i) << " ";
    }

    return 0;
}
```

### Pointer Arithmetic (p+1, p++, q-p)
```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[] = {5, 10, 15, 20, 25};
    int* p = arr;     // points to arr[0]
    int* q = &arr[4]; // points to arr[4]

    cout << "p points to: " << *p << endl;
    cout << "p+1 points to: " << *(p+1) << endl;

    p++;
    cout << "After p++: " << *p << endl;

    cout << "q - p = " << q - p << endl; // distance in elements
    return 0;
}
```

### Passing Array using Pointers
```cpp
#include <iostream>
using namespace std;

void printArray(int* p, int size) {
    for(int i=0; i<size; i++) {
        cout << *(p+i) << " ";  // pointer arithmetic
    }
    cout << endl;
}

int main() {
    int arr[5] = {1, 2, 3, 4, 5};
    printArray(arr, 5);   // array decays to pointer
    return 0;
}
```

### Dynamic Arrays using new
```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter size of array: ";
    cin >> n;

    int* arr = new int[n];   // dynamic allocation

    cout << "Enter " << n << " elements:\n";
    for(int i=0; i<n; i++) {
        cin >> arr[i];
    }

    cout << "You entered: ";
    for(int i=0; i<n; i++) {
        cout << arr[i] << " ";
    }

    delete[] arr; // free memory
    return 0;
}
```

### 2D Arrays with Pointers
```cpp
#include <iostream>
using namespace std;

int main() {
    int rows, cols;
    cout << "Enter rows and cols: ";
    cin >> rows >> cols;

    int** mat = new int*[rows];   // array of int*
    for(int i=0; i<rows; i++) {
        mat[i] = new int[cols];   // each row allocated
    }

    cout << "Enter matrix elements:\n";
    for(int i=0; i<rows; i++) {
        for(int j=0; j<cols; j++) {
            cin >> mat[i][j];
        }
    }

    cout << "Matrix:\n";
    for(int i=0; i<rows; i++) {
        for(int j=0; j<cols; j++) {
            cout << mat[i][j] << " ";
        }
        cout << endl;
    }

    // free memory
    for(int i=0; i<rows; i++) {
        delete[] mat[i];
    }
    delete[] mat;

    return 0;
}
```
-------------------------------------------------------

## Special Topics

### Array of Pointers (char* names[5])
```cpp
#include <iostream>
using namespace std;

int main() {
    const char* names[5] = {"Alice", "Bob", "Charlie", "David", "Eve"};

    cout << "Names list:\n";
    for(int i=0; i<5; i++) {
        cout << names[i] << endl;
    }
    return 0;
}
```

### Pointer to Array (int (*p)[5])
```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[5] = {10, 20, 30, 40, 50};

    int (*p)[5] = &arr;  // p is a pointer to array of 5 ints

    cout << "Access using pointer to array:\n";
    for(int i=0; i<5; i++) {
        cout << (*p)[i] << " ";
    }
    cout << endl;

    return 0;
}
```

### Returning Array from Function (using Pointers)
```cpp
#include <iostream>
using namespace std;

int* createArray(int n) {
    int* arr = new int[n];  // dynamically allocate
    for(int i=0; i<n; i++) {
        arr[i] = i+1;       // store 1..n
    }
    return arr;             // return pointer
}

int main() {
    int n = 5;
    int* arr = createArray(n);

    cout << "Array returned from function: ";
    for(int i=0; i<n; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;

    delete[] arr;  // free memory
    return 0;
}
```

### Difference: Static Array vs Dynamic Array
```cpp
#include <iostream>
using namespace std;

int main() {
    // Static array (size fixed at compile-time)
    int staticArr[5] = {1, 2, 3, 4, 5};
    cout << "Static array: ";
    for(int i=0; i<5; i++) cout << staticArr[i] << " ";
    cout << endl;

    // Dynamic array (size decided at runtime)
    int n;
    cout << "Enter size for dynamic array: ";
    cin >> n;

    int* dynamicArr = new int[n];
    cout << "Enter " << n << " elements:\n";
    for(int i=0; i<n; i++) cin >> dynamicArr[i];

    cout << "Dynamic array: ";
    for(int i=0; i<n; i++) cout << dynamicArr[i] << " ";
    cout << endl;

    delete[] dynamicArr; // free memory
    return 0;
}
```
-----------------------------------------------