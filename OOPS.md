# C++ Object-Oriented Programming (OOP)

This repository contains comprehensive notes and examples on **C++ Object-Oriented Programming**, covering everything from the basics of classes to advanced OOP concepts and modern C++ features.

---

## Table of Contents

### 1. C++ Object-Oriented Programming
- Overview of OOP in C++

### 2. Class Basics in C++
- Access Specifiers in C++
- Scope Resolution Operator (`::`)
- Understanding the `this` Pointer

### 3. Constructors and Destructors
1. Default Constructor  
2. Parameterized Constructor  
3. Copy Constructor  
4. Constructor Overloading  
5. Constructor Initialization List  
6. Destructor  
7. Constructor Delegation  

### 4. Object Lifecycle in C++
1. Object Lifecycle Phases  
2. Object Creation in Different Memory Regions  
3. Static Objects (Global/Static Memory)  
4. Automatic Objects (Stack Memory - Local Scope)  
5. Dynamic Objects (Heap Memory - Manual Allocation)  
6. Object Arrays  
7. Memory Management with `new` and `delete`  

### 5. Encapsulation in C++
#### 5.1 Data Hiding
- Private Members  
- Public Interface  
- Protected Members  
- Getter and Setter Methods  
- Friend Functions and Classes  
- `const` Member Functions  

#### 5.2 Properties and Access Control
- Read-Only Properties  
- Write-Only Properties  
- Computed Properties  
- Access Control Patterns  
- Data Validation in Setters  

### 6. Inheritance in C++
#### 6.1 Basic Inheritance
- Single Inheritance  
- Multiple Inheritance  
- Multi-Level Inheritance  
- Access Modes in Inheritance  
- Base Class Initialization  
- Constructor Chaining  

#### 6.2 Advanced Inheritance
- Virtual Functions  
- Abstract Classes and Pure Virtual Functions  
- Interface Implementation  
- The Diamond Problem  
- Virtual Inheritance (Solution to Diamond Problem)  

### 7. Polymorphism in C++
#### 7.1 Compile-time Polymorphism
- Function Overloading  
- Operator Overloading  
- Template Functions  
- Template Classes  
- Static Binding  

#### 7.2 Runtime Polymorphism
- Virtual Functions  
- Dynamic Binding (Late Binding)  
- Virtual Destructors  
- `override` Keyword  
- `final` Keyword  
- Dynamic Casting  

### 8. Advanced OOP Concepts
#### 8.1 Composition and Aggregation
- Composition vs. Aggregation  
- Composition (Strong Relationship)  
- Aggregation (Weak Relationship)  
- Dependency Management  
- Ownership Semantics  
- Lifecycle Management  

#### 8.2 SOLID Principles in OOP
- Single Responsibility Principle (SRP)  
- Open-Closed Principle (OCP)  
- Liskov Substitution Principle (LSP)  
- Dependency Inversion Principle (DIP)  

#### 8.3 Modern C++ Features in OOP
- Smart Pointers (Memory Management)  
- Move Semantics (Efficient Resource Transfer)  
- Perfect Forwarding (Efficient Function Arguments)  
- Lambda Expressions (Inline Functions)  
- STL Containers with Objects  

---

# C++ Object-Oriented Programming (OOP) Basics

Object-oriented programming (OOP) aims to model real-world entities in code using concepts like **inheritance, encapsulation, and polymorphism**. The primary goal of OOP is to bind data and the functions that operate on them so that no other part of the program can access this data except through these functions.

Unlike procedural programming, which operates on data using standalone functions, OOP creates **objects** that encapsulate both data and behavior.

---

## Key Concepts of OOP

An object has two main characteristics:  

- **Attributes (State):** Describe the object, e.g., a car has brand, model, mileage, etc.  
- **Behavior (Functions/Methods):** Define what the object can do, e.g., driving, acceleration, parking.

**Building Blocks of OOP:**
- Class  
- Object  
- Encapsulation  
- Abstraction  
- Polymorphism  
- Inheritance  
- Dynamic Binding  
- Message Passing  

**Characteristics of OOP Languages:**  
- Data encapsulation  
- Inheritance  
- Polymorphism  
- Abstraction  
- Dynamic binding  

---

## 1. Class Basics in C++

### Class Declaration and Definition
A **class** in C++ is a user-defined data type that contains **attributes (data members)** and **functions (methods)**. It serves as a **blueprint** for creating objects.

**Example Analogy:**  
Think of a class as a blueprint for a car. You can create multiple car objects like SUV, Sedan, or Van from this blueprint.

**Example:**
```cpp
class Car {
public:
    string brand, model;
    void drive();
};
brand and model are attributes.

drive() is a class function.

Access Specifiers in C++
Access specifiers control visibility of class members:

Public (public:) → Accessible from anywhere.

Private (private:) → Accessible only within the class.

Protected (protected:) → Accessible within the class and its derived classes.

Member Variables and Functions
Member Variables: Store the state of an object (e.g., brand, model, mileage).

Member Functions: Define the behavior of an object (e.g., drive(), show_data()).

Objects
An object is an instance of a class. Memory is allocated when an object is created.

Object Creation Syntax:

cpp
Copy
Edit
Car suv;
Car sedan;
Car van;
Object Destruction:
Memory is automatically deallocated when the object goes out of scope.

Scope Resolution Operator (::)
Used to define class functions outside the class definition:

cpp
Copy
Edit
class Car {
public:
    string brand, model;
    int mileage;
    void drive(int);
};

void Car::drive(int distance) {
    mileage += distance;
}
Example: Class and Objects in C++
cpp
Copy
Edit
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
        cout << "Distance driven: " << mileage << " miles" << endl;
    }
};

int main() {
    Car my_car;

    my_car.brand = "Honda";
    my_car.model = "Accord";
    my_car.drive(50);

    my_car.show_data();
    return 0;
}
Explanation:

Class Car is defined with attributes and methods.

Object my_car is created.

Values are assigned to brand and model.

drive() increases mileage.

show_data() prints object details.

Understanding the this Pointer
The this pointer is an implicit pointer available in all non-static member functions. It refers to the current object calling the function.

Key Uses:

Access members of the current object.

Differentiate between class attributes and function parameters with the same name.

Enable method chaining.

Example:

cpp
Copy
Edit
#include <iostream>
using namespace std;

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

int main() {
    Car my_car("Toyota", 100);
    my_car.drive(50);
    my_car.show_data();
    return 0;
}
Explanation:

In the constructor, this->brand = brand assigns the parameter to the object’s attribute.

In drive(), this->mileage updates the calling object's mileage.

show_data() accesses the object’s attributes using this.

