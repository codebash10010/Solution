Section 1: C++ Object Oriented Programming (Sample)
# 1. 🚀 C++ Object-Oriented Programming

📘 **Overview**  
C++ Object-Oriented Programming (OOP) is a programming paradigm based on **objects** that contain data (attributes) and code (methods). It focuses on reusability, modularity, and maintainability.

---

## 📊 OOP Pillars


OOP
├── 🏎 Class
├── 📦 Object
├── 🔒 Encapsulation
├── 🌀 Abstraction
├── 🔄 Polymorphism
└── 🌳 Inheritance


---

## 💡 Key Features of OOP in C++
- **Encapsulation** → Wrapping data & functions together
- **Abstraction** → Hiding implementation details
- **Inheritance** → Reusing code from existing classes
- **Polymorphism** → One interface, multiple implementations

---

## 💻 Example: Basic Class & Object
```cpp
#include <iostream>
using namespace std;

class Car {
public:
    string brand;
    int year;

    void display() {
        cout << "Brand: " << brand << ", Year: " << year << endl;
    }
};

int main() {
    Car myCar;
    myCar.brand = "Toyota";
    myCar.year = 2022;
    myCar.display();
}


Output:

Brand: Toyota, Year: 2022
