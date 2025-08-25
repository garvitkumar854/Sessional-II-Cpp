# Pointers

## Basics Of Pointers

### Declaring & Initializing Pointers
```cpp
#include <iostream>
using namespace std;
int main() {
    int x = 10;
    int *p = &x;   // pointer stores address of x
    cout << "x = " << x << ", *p = " << *p << endl;
}
```

### Dereferencing `*p`
```cpp
#include <iostream>
using namespace std;
int main() {
    int x = 42;
    int *p = &x;
    cout << "Value of x using pointer: " << *p << endl;  // dereference
}
```

### Null Pointer
```cpp
#include <iostream>
using namespace std;
int main() {
    int* p = nullptr;
    if(p == nullptr) cout << "Pointer is NULL" << endl;
}
```

### Void Pointer
```cpp
#include <iostream>
using namespace std;
int main() {
    int x = 100;
    void* vp = &x;   // void pointer
    cout << "Value via casting: " << *(int*)vp << endl;
}
```

-----------------------------------------------------

## Pointers & Arrays

### Relationship arr[i] == *(arr+i)
```cpp
#include <iostream>
using namespace std;
int main() {
    int arr[] = {10, 20, 30};
    for(int i=0; i<3; i++)
        cout << arr[i] << " == " << *(arr+i) << endl;
}
```

### Pointer Arithmetic
```cpp
#include <iostream>
using namespace std;
int main() {
    int arr[] = {5,10,15,20};
    int* p = arr;
    cout << *p << endl;    // 5
    p++;
    cout << *p << endl;    // 10
    int* q = &arr[3];
    cout << "q - p = " << q - p << endl; // distance
}
```

### Passing Array using Pointers
```cpp
#include <iostream>
using namespace std;
void printArray(int* p, int size) {
    for(int i=0; i<size; i++) cout << *(p+i) << " ";
    cout << endl;
}
int main() {
    int arr[] = {1,2,3,4,5};
    printArray(arr, 5);
}
```

### Array of Pointers
```cpp
#include <iostream>
using namespace std;
int main() {
    char* names[] = {"Alice", "Bob", "Charlie"};
    for(int i=0; i<3; i++) cout << names[i] << endl;
}
```
--------------------------------------------------

## Pointers as Function Arguments

### Pass by Pointer vs Reference
```cpp
#include <iostream>
using namespace std;
void byPointer(int* x) { *x = *x + 10; }
void byReference(int& x) { x = x + 20; }
int main() {
    int a = 5, b = 5;
    byPointer(&a);
    byReference(b);
    cout << "a=" << a << ", b=" << b << endl; // a=15, b=25
}
```

### Swapping using Pointers
```cpp
#include <iostream>
using namespace std;
void swap(int* x, int* y) {
    int temp = *x;
    *x = *y;
    *y = temp;
}
int main() {
    int a=10, b=20;
    swap(&a,&b);
    cout << "a=" << a << " b=" << b;
}
```

### Function Returning Pointer
```cpp
#include <iostream>
using namespace std;
int* getMax(int* a, int* b) {
    return (*a > *b) ? a : b;
}
int main() {
    int x=100, y=200;
    int* p = getMax(&x,&y);
    cout << "Max = " << *p;
}
```
--------------------------------------

## Pointers to Functions
### Function Pointer
```cpp
#include <iostream>
using namespace std;
int add(int a, int b) { return a+b; }

int main() {
    int (*fp)(int,int) = add;
    cout << "Sum = " << fp(3,4);
}
```

### Passing Function as Argument
```cpp
#include <iostream>
using namespace std;
int add(int a,int b){return a+b;}
int operate(int x,int y,int (*func)(int,int)){
    return func(x,y);
}

int main(){
    cout << "Result: " << operate(5,7,add);
}
```
--------------------------------

## Pointers with Objects
### Pointer to Object
```cpp
#include <iostream>
using namespace std;
class Book { public: string title; };
int main() {
    Book b; b.title="C++";
    Book* p = &b;
    cout << p->title;
}
```

### Array of Objects with Pointers
```cpp
#include <iostream>
using namespace std;
class Emp { public: string name; int sal; };
int main() {
    Emp arr[2] = {{"A",500}, {"B",1000}};
    Emp* p = arr;
    for(int i=0;i<2;i++) cout << (p+i)->name << " " << (p+i)->sal << endl;
}
```

### `this` Pointer
```cpp
#include <iostream>
using namespace std;
class Student {
    int marks;
public:
    Student(int m){ marks = m; }
    void show() { cout << "Marks: " << this->marks << endl; }
};
int main() {
    Student s(90);
    s.show();
}
```
----------------------------------------------------------------------

## Dynamic Memory Allocation
### new & delete
```cpp
#include <iostream>
using namespace std;
int main() {
    int* p = new int(50);
    cout << *p << endl;
    delete p;
}
```

### Allocating Array Dynamically
```cpp
#include <iostream>
using namespace std;
int main() {
    int n; cout<<"Enter size: "; cin>>n;
    int* arr = new int[n];
    for(int i=0;i<n;i++) arr[i]=i+1;
    for(int i=0;i<n;i++) cout<<arr[i]<<" ";
    delete[] arr;
}
```

### Allocating Object Dynamically
```cpp
#include <iostream>
using namespace std;
class Car { public: string name; };
int main() {
    Car* c = new Car;
    c->name="Tesla";
    cout<<c->name;
    delete c;
}
```

### 2D Dynamic Array
```cpp
#include <iostream>
using namespace std;
int main() {
    int rows=2, cols=3;
    int** mat = new int*[rows];
    for(int i=0;i<rows;i++) mat[i]=new int[cols];

    int val=1;
    for(int i=0;i<rows;i++)
        for(int j=0;j<cols;j++)
            mat[i][j]=val++;

    for(int i=0;i<rows;i++){
        for(int j=0;j<cols;j++) cout<<mat[i][j]<<" ";
        cout<<endl;
    }

    for(int i=0;i<rows;i++) delete[] mat[i];
    delete[] mat;
}
```
------------------------------------------------------------------------

## Special Topics
### Returning Array using Pointer
```cpp
#include <iostream>
using namespace std;
int* getArray() {
    static int arr[3] = {10,20,30}; // static to persist after return
    return arr;
}
int main() {
    int* p = getArray();
    for(int i=0;i<3;i++) cout<<p[i]<<" ";
}
```

### Dangling Pointer & Memory Leak
```cpp
#include <iostream>
using namespace std;
int main() {
    int* p = new int(100);
    delete p;          // now dangling
    // cout << *p;     // unsafe!

    int* leak = new int[1000]; // if we forget delete[] => memory leak
    // delete[] leak;
}
```

### Smart Pointers (C++11)
```cpp
#include <iostream>
#include <memory>
using namespace std;
class Test { public: Test(){cout<<"Created\n";} ~Test(){cout<<"Destroyed\n";} };
int main() {
    unique_ptr<Test> p1(new Test);
    // automatically destroyed, no delete needed
}
```

### Static vs Dynamic Array
```cpp
#include <iostream>
using namespace std;
int main() {
    int arr[5]; // static, size fixed at compile time

    int n=5;
    int* darr = new int[n]; // dynamic, size at runtime
    delete[] darr;
}
```

