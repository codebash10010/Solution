# 🚀 C++ Object Oriented Programming Guide

> **Master C++ OOP from Basics to Advanced**  
> This guide covers **every concept** in OOP with explanations, examples, diagrams, and key takeaways.

---

## 📑 Table of Contents
- [🏁 Introduction to OOP](#-introduction-to-oop)
- [🏎 Class Basics in C++](#-class-basics-in-c)
- [🔑 Access Specifiers](#-access-specifiers)
- [📌 The `this` Pointer](#-the-this-pointer)
- [⚙️ Constructors & Destructors](#️-constructors--destructors)
- [♻️ Object Lifecycle](#️-object-lifecycle)
- [🔒 Encapsulation](#-encapsulation)
- [🌳 Inheritance](#-inheritance)
- [🔄 Polymorphism](#-polymorphism)
- [🧩 Advanced OOP Concepts](#-advanced-oop-concepts)
- [🛠 SOLID Principles](#-solid-principles)
- [✨ Modern C++ Features](#-modern-c-features)

---

## 🏁 Introduction to OOP

Object-oriented programming (OOP) brings **real-world entities** into code.

📊 **OOP Pillars Diagram**
```
OOP
 ├── 🏎 Class
 ├── 📦 Object
 ├── 🔒 Encapsulation
 ├── 🌀 Abstraction
 ├── 🔄 Polymorphism
 └── 🌳 Inheritance
```

💡 **Key Idea**: OOP groups data + behavior together.

---

## 🏎 Class Basics in C++

A **class** is a blueprint. An **object** is built from that blueprint.

**Example Diagram:**
```
Class: Car
  ├── brand
  ├── model
  └── drive()

Object: myCar
  ├── brand = "Honda"
  ├── model = "Accord"
  └── drive(50)
```

**Code Example:**
```cpp
#include <iostream>
using namespace std;

class Car {
public:
    string brand, model;
    int mileage = 0;

    void drive(int distance) { mileage += distance; }
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
}
```

💡 **Tip**: Classes = plan, Objects = product.

---

## 🔑 Access Specifiers

Control who can access your data.

| Emoji | Specifier  | In Class | Outside | Inherited |
|-------|------------|----------|---------|-----------|
| 🔒    | private    | ✅       | ❌      | ❌        |
| 🛡     | protected | ✅       | ❌      | ✅        |
| 🌐    | public     | ✅       | ✅      | ✅        |

---

## 📌 The `this` Pointer

📍 Points to the **current object**.

```cpp
class Car {
public:
    string brand;
    int mileage;

    Car(string brand, int mileage) {
        this->brand = brand;
        this->mileage = mileage;
    }
};
```

💡 **Tip**: Use `this` to avoid variable name conflicts.

---

## ⚙️ Constructors & Destructors

🏗 **Constructor**: Sets things up  
🗑 **Destructor**: Cleans up

**Diagram:**
```
Object Created → Constructor runs
Object Ends   → Destructor runs
```

```cpp
class Car {
public:
    string brand;
    Car(string b) { brand = b; cout << "Created " << brand; }
    ~Car() { cout << "Destroyed " << brand; }
};
```

---

## ♻️ Object Lifecycle

**Memory Areas Diagram:**
```
Stack    → Auto variables
Heap     → new/delete
Static   → Exists till program ends
```

💡 **Tip**: Always `delete` heap objects to prevent leaks.

---

## 🔒 Encapsulation

Hides data, allows safe access.

```cpp
class BankAccount {
private:
    double balance;
public:
    void setBalance(double b) { if (b>=0) balance = b; }
    double getBalance() const { return balance; }
};
```

---

## 🌳 Inheritance

📊 Diagram:
```
Vehicle
 └── Car
      └── SportsCar
```

💡 **Tip**: Use `public` inheritance for "is-a" relationships.

---

## 🔄 Polymorphism

Lets the same function act differently.

```cpp
class Base { public: virtual void show() { cout << "Base"; } };
class Derived : public Base { public: void show() override { cout << "Derived"; } };

```

---

## 🧩 Advanced OOP Concepts

- Composition 🏗
- Aggregation 🧷
- Virtual Inheritance 🌐

---

## 🛠 SOLID Principles

💡 **S**ingle Responsibility — One job per class  
💡 **O**pen/Closed — Extend without modifying  
💡 **L**iskov — Subclasses must be replaceable  
💡 **I**nterface Segregation — No unused methods  
💡 **D**ependency Inversion — Depend on abstractions

---

## ✨ Modern C++ Features

- 🔑 Smart Pointers
- 🚚 Move Semantics
- 🏷 Lambda Expressions
- 📦 STL Containers

---

📚 **End** — Happy Coding! 🚀
