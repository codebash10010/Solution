# C++ Object Oriented Programming

> **Learn C++ OOP from Basics to Advanced** 🚀  
> This guide covers everything about Object-Oriented Programming in C++, with explanations, examples, and key takeaways.

---

## 📑 Table of Contents
- [Introduction to OOP](#introduction-to-oop)
- [Class Basics in C++](#class-basics-in-c)
- [Access Specifiers](#access-specifiers)
- [The `this` Pointer](#the-this-pointer)
- [Constructors & Destructors](#constructors--destructors)
- [Object Lifecycle](#object-lifecycle)
- [Encapsulation](#encapsulation)
- [Inheritance](#inheritance)
- [Polymorphism](#polymorphism)
- [Advanced OOP Concepts](#advanced-oop-concepts)
- [SOLID Principles](#solid-principles)
- [Modern C++ Features](#modern-c-features)

---

## Introduction to OOP

Object-oriented programming (OOP) implements **real-world entities** like inheritance, encapsulation, and polymorphism in programming.

**Example: Car as an Object**
- Attributes: brand, model, size, mileage
- Behavior: drive, accelerate, park

**Core OOP Concepts**
1. Class
2. Object
3. Encapsulation
4. Abstraction
5. Polymorphism
6. Inheritance
7. Dynamic Binding
8. Message Passing

---

## Class Basics in C++

A **class** is a user-defined data type that contains attributes (data members) and methods (member functions). It acts as a *blueprint* for objects.

```cpp
#include <iostream>
using namespace std;

class Car {
public:
    string brand, model;
    int mileage = 0;

    void drive(int distance) {
        mileage += distance;
    }

    void show_data() {
        cout << "Brand: " << brand << endl;
        cout << "Model: " << model << endl;
        cout << "Mileage: " << mileage << " miles" << endl;
    }
};

int main() {
    Car myCar;
    myCar.brand = "Honda";
    myCar.model = "Accord";
    myCar.drive(50);
    myCar.show_data();
    return 0;
}
```

💡 **Key Takeaway**: A class defines the structure, but objects store actual data.

---

## Access Specifiers

Access specifiers control where class members can be accessed from:

| Specifier  | Accessible in Class | Accessible Outside Class | Accessible in Derived Class |
|------------|--------------------|--------------------------|-----------------------------|
| `private`  | ✅ Yes              | ❌ No                    | ❌ No                       |
| `protected`| ✅ Yes              | ❌ No                    | ✅ Yes                      |
| `public`   | ✅ Yes              | ✅ Yes                   | ✅ Yes                      |

---

## The `this` Pointer

The `this` pointer stores the address of the current object.

```cpp
class Car {
public:
    string brand;
    int mileage;

    Car(string brand, int mileage) {
        this->brand = brand;
        this->mileage = mileage;
    }

    void drive(int distance) {
        this->mileage += distance;
    }

    void show_data() {
        cout << "Brand: " << this->brand << endl;
        cout << "Mileage: " << this->mileage << " miles" << endl;
    }
};
```

💡 **Key Takeaway**: Use `this` to avoid naming conflicts and enable method chaining.

---

## Constructors & Destructors

A **constructor** initializes objects, while a **destructor** cleans up when an object is destroyed.

```cpp
class Car {
public:
    string brand;
    Car(string b) {
        brand = b;
        cout << "Car " << brand << " created." << endl;
    }
    ~Car() {
        cout << "Car " << brand << " destroyed." << endl;
    }
};
```

💡 **Key Takeaway**: Use constructors for initialization and destructors for cleanup.

---

*(The rest of the sections will follow the same structured, code-rich format with tips and highlights.)*
