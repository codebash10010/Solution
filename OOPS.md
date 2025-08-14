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

> This README serves as a roadmap for mastering C++ Object-Oriented Programming, from fundamental concepts to advanced techniques and best practices.

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
