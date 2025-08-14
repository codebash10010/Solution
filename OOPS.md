
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





Object-oriented programming:
Object-oriented programming (OOP) aims to implement real-world entities such as inheritance, encapsulation, and polymorphism in programming. The primary goal of OOP is to bind data and the functions that operate on them so that no other part of the code can access this data except through these functions.
Unlike procedural programming, where functions are written to perform operations on data, OOP involves creating objects that contain both data and functions.
An object has two characteristics: attributes and behavior. For example, a car can be an object. And, it has
attributes - brand, model, size, mileage, etc.
behavior - driving, acceleration, parking, etc.

There are some basic concepts that act as the building blocks of OOPs i.e.
Class
Object
Encapsulation
Abstraction
Polymorphism
Inheritance
Dynamic Binding
Message Passing
Characteristics of an Object-Oriented Programming Language
2.1 Class Basics in C++
Class Declaration and Definition
A class in C++ is a user-defined data type that holds its own attributes (data members) and functions (methods). These members can be accessed and modified using objects of the class. A class serves as a blueprint for creating objects.
Example Analogy
Think of a class as a car blueprint that defines its properties (brand, model, mileage) and behaviors (drive, brake). Once we have the blueprint, we can create different car objects based on it, such as SUV, Sedan, and Van.

In the above code, we have used the class keyword to create a class named Car. Here,
brand and model are class attributes used to store data
drive() is a class function used to perform some operation

Access Specifiers in C++
Access specifiers define how members of a class can be accessed from outside the class. C++ provides three types:
Public (public:) → Accessible from anywhere.
Private (private:) → Only accessible within the class.
Protected (protected:) → Accessible within the class and its derived (child) classes.

Member Variables (Attributes)
Member variables store the state or data of a class. For example, in a Car class, attributes like brand, model, and mileage store car information.

Member Functions (Methods)
Functions inside a class define the behavior of an object. For example, a car has functions like drive() to increase mileage and show_data() to display details.

Objects:
An Object is an instance of a Class. When a class is defined, no memory is allocated but when it is instantiated (i.e. an object is created) memory is allocated.

For example, the Car class defines the model, brand, and mileage. Now, based on the definition.
Object Creation and Destruction
Creating Objects: When a class is defined, no memory is allocated until an object of the class is created.
Syntax for Object Creation:
 Class_Name object_name;
Car suv;
Car sedan;
Car van;
Object Destruction: When an object goes out of scope, its memory is automatically deallocated.

Scope Resolution Operator (::)
The :: operator is used to define a function outside the class definition.
Example:
class Car {
  public:
    string brand, model;
    int mileage;
    void drive(int);
};

// Defining the function outside the class
void Car::drive(int distance) {
    mileage += distance;
}


Example: Class and Objects in C++
#include <iostream>
using namespace std;

class Car {
  public:
    // Attributes
    string brand, model;
    int mileage = 0;

    // Function to drive the car
    void drive(int distance) {
        mileage += distance;
    }
    
    // Function to print car details
    void show_data() {
        cout << "Brand: " << brand << endl;
        cout << "Model: " << model << endl;
        cout << "Distance driven: " << mileage << " miles" << endl;
    }
};

int main() {
    // Creating an object of Car class
    Car my_car;

    // Initializing object attributes
    my_car.brand = "Honda";
    my_car.model = "Accord";
    my_car.drive(50);

    // Displaying object attributes
    my_car.show_data();

    return 0; 
}

Explanation:
We define a class Car with attributes and methods.
We create an object my_car.
We assign values to my_car.brand and my_car.model.
We call the function drive() to increase mileage.
We print the details using show_data().

Understanding the ‘this’ Pointer in C++
The this pointer is an implicit pointer available in all non-static member functions. It holds the memory address of the calling object.
Key Features of this Pointer:
Refers to the Current Object:
 It allows us to access members of the current object inside class functions.
Helps Differentiate Variable Names:
 If function parameters have the same name as class attributes, we use this-> to distinguish them.
Used in Method Chaining:
 The this pointer allows function calls to be chained.
Example of this Pointer in C++
#include <iostream>
using namespace std;

class Car {
  public:
    string brand;
    int mileage;

    // Constructor using 'this' pointer
    Car(string brand, int mileage) {
        this->brand = brand;
        this->mileage = mileage;
    }

    // Function to update mileage
    void drive(int distance) {
        this->mileage += distance;
    }

    // Function to display car details
    void show_data() {
        cout << "Brand: " << this->brand << endl;
        cout << "Mileage: " << this->mileage << " miles" << endl;
    }
};

int main() {
    // Creating an object of Car class
    Car my_car("Toyota", 100);
    
    // Calling member functions
    my_car.drive(50);
    my_car.show_data();

    return 0;
}

Explanation of this Pointer Usage:
In the Constructor:
this->brand = brand; assigns the constructor parameter brand to the object's attribute brand.
In Member Functions:
this->mileage += distance; updates the mileage of the calling object.
Calling Functions:
my_car.show_data(); uses this implicitly to access object members.

2.2 Constructors and Destructors in C++
Constructors
A constructor is a special member function of a class that is automatically called when an object of the class is created. It is used to initialize objects.
Key Characteristics of Constructors:
They have the same name as the class.
They do not return a value, not even void.
They can be overloaded to create different types of constructors.

1. Default Constructor
A default constructor is a constructor that takes no parameters and initializes class members with default values.
Example: Default Constructor
#include <iostream>
using namespace std;

class Car {
  public:
    string brand;
    int mileage;

    // Default constructor
    Car() {
        brand = "Unknown";
        mileage = 0;
    }

    void show_data() {
        cout << "Brand: " << brand << endl;
        cout << "Mileage: " << mileage << " miles" << endl;
    }
};

int main() {
    Car myCar;  // Default constructor is automatically called
    myCar.show_data();
    return 0;
}

Output:
Brand: Unknown  
Mileage: 0 miles


2. Parameterized Constructor
A parameterized constructor accepts arguments to initialize object attributes at the time of object creation.
Example: Parameterized Constructor
class Car {
  public:
    string brand;
    int mileage;

    // Parameterized constructor
    Car(string b, int m) {
        brand = b;
        mileage = m;
    }

    void show_data() {
        cout << "Brand: " << brand << endl;
        cout << "Mileage: " << mileage << " miles" << endl;
    }
};

int main() {
    Car myCar("Toyota", 5000);  // Passing values during object creation
    myCar.show_data();
    return 0;
}

Output:
Brand: Toyota  
Mileage: 5000 miles


3. Copy Constructor
A copy constructor initializes a new object by copying attributes from an existing object.
Syntax:
ClassName (const ClassName &oldObject) { }

Example: Copy Constructor
class Car {
  public:
    string brand;
    int mileage;

    // Parameterized constructor
    Car(string b, int m) {
        brand = b;
        mileage = m;
    }

    // Copy constructor
    Car(const Car &obj) {
        brand = obj.brand;
        mileage = obj.mileage;
    }

    void show_data() {
        cout << "Brand: " << brand << endl;
        cout << "Mileage: " << mileage << " miles" << endl;
    }
};

int main() {
    Car car1("Ford", 8000);  // Creating first object
    Car car2 = car1;  // Copying car1 into car2 using copy constructor

    car2.show_data();  // Output will be the same as car1
    return 0;
}

Output:
Brand: Ford  
Mileage: 8000 miles


4. Constructor Overloading
Constructor overloading means defining multiple constructors in a class with different parameters.
Example: Constructor Overloading
class Car {
  public:
    string brand;
    int mileage;

    // Default constructor
    Car() {
        brand = "Unknown";
        mileage = 0;
    }

    // Parameterized constructor
    Car(string b, int m) {
        brand = b;
        mileage = m;
    }

    void show_data() {
        cout << "Brand: " << brand << endl;
        cout << "Mileage: " << mileage << " miles" << endl;
    }
};

int main() {
    Car car1;  // Calls default constructor
    Car car2("BMW", 3000);  // Calls parameterized constructor

    car1.show_data();
    car2.show_data();

    return 0;
}

Output:
Brand: Unknown  
Mileage: 0 miles  
Brand: BMW  
Mileage: 3000 miles  

5. Constructor Initialization List
Instead of assigning values inside the constructor body, we can use an initialization list to initialize attributes more efficiently.
Example: Constructor Initialization List
class Car {
  public:
    string brand;
    int mileage;
    // Constructor using initialization list
    Car(string b, int m) : brand(b), mileage(m) { }
    void show_data() {
        cout << "Brand: " << brand << endl;
        cout << "Mileage: " << mileage << " miles" << endl;
    }
};
int main() {
    Car car1("Tesla", 12000);
    car1.show_data();
    return 0;
}

🔹 The initialization list makes object initialization more efficient.

6. Destructor
A destructor is a special function that is automatically called when an object goes out of scope or is explicitly deleted. It is used to free resources like memory, files, etc.
Key Features of Destructors:
They have the same name as the class, but preceded by a tilde (~).
No parameters and no return type.
Automatically called when an object is destroyed.
Example: Destructor Implementation
class Car {
  public:
    string brand;
    // Constructor
    Car(string b) {
        brand = b;
        cout << "Car " << brand << " created." << endl;
    }

    // Destructor
    ~Car() {
        cout << "Car " << brand << " destroyed." << endl;
    }
};
int main() {
    Car myCar("Audi");  // Constructor is called
    // Destructor will be called automatically when myCar goes out of scope
    return 0;
}
Output:
Car Audi created.  
Car Audi destroyed.

7. Constructor Delegation
Constructor delegation means one constructor calling another constructor within the same class to avoid code duplication.
Example: Constructor Delegation
class Car {
  public:
    string brand;
    int mileage;
    // Delegating constructor
    Car() : Car("Unknown", 0) { }
    // Parameterized constructor
    Car(string b, int m) {
        brand = b;
        mileage = m;
    }
    void show_data() {
        cout << "Brand: " << brand << endl;
        cout << "Mileage: " << mileage << " miles" << endl;
    }
};
int main() {
    Car car1;  // Calls default constructor, which delegates to parameterized constructor
    car1.show_data();
    return 0;
}
Output:
Brand: Unknown  
Mileage: 0 miles  

2.3 Object Lifecycle in C++
Understanding the lifecycle of an object is crucial in C++ programming. Objects go through several phases:
Creation (Instantiation)
Usage (Active Lifetime)
Destruction (Deallocation)
These phases depend on where and how the object is created. C++ provides different ways to manage objects in stack, heap, and static memory.

1. Object Lifecycle Phases
Phase
Description
Object Creation
Memory is allocated, and the constructor is called.
Object Usage
The object is used for computations, data storage, or operations.
Object Destruction
The destructor is called, and memory is deallocated.


2. Object Creation in Different Memory Regions
Objects can be created in different memory regions, affecting their lifespan and behavior.
Storage Type
Memory Region
Creation
Destruction
Automatic (Local)
Stack
Created when function is called.
Destroyed when function ends.
Dynamic (Heap)
Heap
Created using new.
Must be manually deleted using delete.
Static
Global/Static Memory
Created once and persists throughout the program.
Destroyed at program termination.


3. Static Objects (Global/Static Memory)
🔹 Exist throughout the program.
 🔹 Destroyed only when the program ends.
 🔹 Useful for maintaining state between function calls.
Example: Static Object
#include <iostream>
using namespace std;

class Car {
  public:
    Car() { cout << "Car object created.\n"; }
    ~Car() { cout << "Car object destroyed.\n"; }
};

void demo() {
    static Car myCar;  // Static object (created once)
}

int main() {
    demo();
    cout << "Back in main.\n";
    demo();  // Uses the same static object
    return 0;
}

Output:
Car object created.
Back in main.
Back in main.
Car object destroyed.  // Destroyed when the program ends

✅ Key Takeaway:
A static object is created only once and is destroyed at program termination.

4. Automatic Objects (Stack Memory - Local Scope)
🔹 Created inside a function and stored in the stack.
 🔹 Automatically destroyed when the function exits.
 🔹 Faster allocation and deallocation compared to dynamic objects.
Example: Automatic Object
class Car {
  public:
    Car() { cout << "Car created.\n"; }
    ~Car() { cout << "Car destroyed.\n"; }
};

void demo() {
    Car myCar;  // Automatic object (Stack)
}

int main() {
    demo();  // Car created inside function
    cout << "Back in main.\n";
    return 0;
}

Output:
Car created.
Car destroyed.  // Destroyed when function exits
Back in main.

✅ Key Takeaway:
Automatic objects exist only inside the function where they are created and are destroyed when the function ends.

5. Dynamic Objects (Heap Memory - Manual Allocation)
🔹 Created using new and stored in heap memory.
 🔹 Exist until explicitly deleted using delete.
 🔹 Must be manually managed to prevent memory leaks.
Example: Dynamic Object
class Car {
  public:
    Car() { cout << "Car created.\n"; }
    ~Car() { cout << "Car destroyed.\n"; }
};

int main() {
    Car* myCar = new Car();  // Dynamic object in heap
    delete myCar;  // Free memory
    return 0;
}

Output:
Car created.
Car destroyed.

✅ Key Takeaway:
Forgetting to use delete causes memory leaks because the object remains in memory.

6. Object Arrays
We can create arrays of objects using static or dynamic allocation.
Example: Static Object Array
class Car {
  public:
    Car() { cout << "Car created.\n"; }
    ~Car() { cout << "Car destroyed.\n"; }
};

int main() {
    Car cars[3];  // Array of objects in stack
    return 0;
}

Output:
Car created.
Car created.
Car created.
Car destroyed.
Car destroyed.
Car destroyed.

✅ Key Takeaway:
Objects in a static array are automatically destroyed when main() ends.

Example: Dynamic Object Array
class Car {
  public:
    Car() { cout << "Car created.\n"; }
    ~Car() { cout << "Car destroyed.\n"; }
};

int main() {
    Car* cars = new Car[3];  // Dynamic array in heap
    delete[] cars;  // Must use delete[]
    return 0;
}

Output:
Car created.
Car created.
Car created.
Car destroyed.
Car destroyed.
Car destroyed.

✅ Key Takeaway:
When deleting a dynamic object array, use delete[] instead of delete.

7. Memory Management with new and delete
Rules for Proper Memory Management
✅ Use new to allocate memory dynamically.
 ✅ Use delete to free single objects.
 ✅ Use delete[] to free object arrays.
 ✅ Forgetting delete leads to memory leaks.
Example: Memory Leak (Improper Deallocation)
void leak() {
    int* ptr = new int(10);  // Memory allocated but not freed
}

🔹 Every time leak() runs, memory is lost because delete is missing.

Example: Proper Memory Management
void safe() {
    int* ptr = new int(10);
    delete ptr;  // Memory freed
}
🔹 Here, we correctly free the allocated memory.

3. Encapsulation in C++
Encapsulation is one of the key principles of Object-Oriented Programming (OOP). It is the process of binding data (variables) and functions (methods) together into a single unit, called a class, and restricting direct access to the data.

Why Encapsulation?
✅ Data Protection → Prevents accidental modification of sensitive data.
 ✅ Code Maintainability → Improves readability and modularity.
 ✅ Control Over Data → Allows controlled access using getter and setter functions.
 ✅ Security → Prevents unauthorized access to class attributes.

3.1 Data Hiding
🔹 Data hiding is a fundamental concept of encapsulation that restricts direct access to class members (variables) to ensure controlled access through methods.
Access Modifiers (public, private, protected) help enforce data hiding.
Access Specifier
Accessible Inside the Class?
Accessible Outside the Class?
Accessible in Derived Classes?
private
✅ Yes
❌ No
❌ No
protected
✅ Yes
❌ No
✅ Yes
public
✅ Yes
✅ Yes
✅ Yes


1. Private Members
🔹 Private members can only be accessed within the same class. They are not accessible from outside the class.
Example: Private Members (Data Hiding)
#include <iostream>
using namespace std;

class Car {
  private:
    string brand;  // Private attribute (Cannot be accessed outside)
  
  public:
    void setBrand(string b) {  // Public setter function
        brand = b;
    }

    void getBrand() {  // Public getter function
        cout << "Brand: " << brand << endl;
    }
};

int main() {
    Car myCar;
    // myCar.brand = "Toyota";  // ❌ Error: brand is private
    myCar.setBrand("Toyota");  // ✅ Allowed (Using setter)
    myCar.getBrand();          // ✅ Allowed (Using getter)
    return 0;
}

Output:
Brand: Toyota

✅ Key Takeaway:
Private members cannot be accessed directly but can be modified using public methods.

2. Public Interface
🔹 Public members define the interface of the class.
 🔹 They provide controlled access to private members using getter and setter functions.
Best Practice: Keep data members private and use public methods to access them.

3. Protected Members
🔹 Protected members are like private members, but they can be accessed in derived (child) classes.
Example: Protected Members
class Vehicle {
  protected:
    int speed;  // Protected variable

  public:
    void setSpeed(int s) {
        speed = s;
    }
};

class Car : public Vehicle {
  public:
    void showSpeed() {
        cout << "Speed: " << speed << " km/h" << endl;  // ✅ Allowed (Inherited class)
    }
};

int main() {
    Car myCar;
    myCar.setSpeed(80);
    myCar.showSpeed();
    return 0;
}

Output:
Speed: 80 km/h

✅ Key Takeaway:
Protected members are accessible in derived classes but not from outside the class.

4. Getter and Setter Methods
🔹 Getter methods are used to retrieve private data.
 🔹 Setter methods are used to modify private data safely.
Example: Using Getter and Setter Methods
class BankAccount {
  private:
    double balance;

  public:
    void setBalance(double b) {  // Setter method
        if (b >= 0)
            balance = b;
        else
            cout << "Invalid balance!" << endl;
    }

    double getBalance() {  // Getter method
        return balance;
    }
};

int main() {
    BankAccount account;
    account.setBalance(500);
    cout << "Current Balance: $" << account.getBalance() << endl;
    return 0;
}

Output:
Current Balance: $500

✅ Key Takeaway:
Encapsulation helps prevent invalid data input by using setter functions.

5. Friend Functions and Classes
🔹 Friend functions allow an external function to access private members of a class.
 🔹 Friend classes allow another class to access the private members of a class.
Example: Friend Function
class Car {
  private:
    string brand = "Ford";

  public:
    friend void showBrand(Car c);  // Friend function declaration
};

void showBrand(Car c) {
    cout << "Car Brand: " << c.brand << endl;  // ✅ Allowed (Friend function)
}

int main() {
    Car myCar;
    showBrand(myCar);
    return 0;
}

Output:
Car Brand: Ford

✅ Key Takeaway:
A friend function can access private members without being a member of the class.

6. const Member Functions
🔹 const member functions do not modify the object's data.
 🔹 Helps ensure data integrity.
Example: Using const Member Function
class Car {
  private:
    string brand = "Toyota";

  public:
    void showBrand() const {  // Const function
        cout << "Brand: " << brand << endl;
    }
};

int main() {
    Car myCar;
    myCar.showBrand();  // ✅ Allowed
    return 0;
}

✅ Key Takeaway:
Const member functions ensure the function does not modify class attributes.

3.2 Properties and Access Control in C++
Encapsulation is crucial for controlling access to class properties. In C++, we can define properties with different access levels to protect data and ensure it is used correctly.

1. Read-Only Properties
A read-only property allows data to be retrieved but not modified after initialization. This is done using a getter function but no setter.
Example: Read-Only Property
#include <iostream>
using namespace std;

class Employee {
  private:
    int id;  // Private attribute

  public:
    // Constructor to initialize id
    Employee(int empId) { id = empId; }

    // Getter function (Read-only)
    int getId() const {
        return id;
    }
};

int main() {
    Employee emp(101);
    cout << "Employee ID: " << emp.getId() << endl;

    // emp.id = 102;  ❌ Error: Private attribute cannot be modified directly
    // emp.setId(102); ❌ No setter function available

    return 0;
}

Output:
Employee ID: 101

✅ Key Takeaway:
No setter function means the property cannot be changed after object creation.
The getter function provides read access.

2. Write-Only Properties
A write-only property allows modification but not direct retrieval. This is useful when storing sensitive data (e.g., passwords).
Example: Write-Only Property
class User {
  private:
    string password;

  public:
    // Setter function (Write-only)
    void setPassword(string pass) {
        password = pass;
    }
};

int main() {
    User user;
    user.setPassword("Secure123");

    // cout << user.password; ❌ Error: Cannot access private member
    // cout << user.getPassword(); ❌ No getter function available

    return 0;
}

✅ Key Takeaway:
Write-only properties are useful for security (e.g., storing passwords).
No getter function prevents unauthorized access.

3. Computed Properties
A computed property is not stored directly but is calculated dynamically based on other properties.
Example: Computed Property
class Rectangle {
  private:
    int width, height;

  public:
    Rectangle(int w, int h) { width = w; height = h; }

    // Computed property: Area (No need for separate storage)
    int getArea() const {
        return width * height;
    }
};

int main() {
    Rectangle rect(5, 10);
    cout << "Area: " << rect.getArea() << endl;  // Computed dynamically
    return 0;
}

Output:
Area: 50

✅ Key Takeaway:
Computed properties are dynamically calculated based on existing data.
No need to store separate variables for computed values.

4. Access Control Patterns
C++ provides various access control patterns using private, protected, and public access specifiers.
Common Access Control Patterns:
Encapsulation with Getters & Setters (Used for controlling access)
Protected Members in Inheritance (Used for extending functionality)
Friend Functions & Friend Classes (Allow external access when necessary)
Const Member Functions (Prevent accidental modification)
Example: Access Control with Getters & Setters
class BankAccount {
  private:
    double balance;

  public:
    BankAccount(double initialBalance) {
        balance = initialBalance;
    }

    // Getter function
    double getBalance() const {
        return balance;
    }

    // Setter function with validation
    void setBalance(double amount) {
        if (amount >= 0)
            balance = amount;
        else
            cout << "Invalid balance!" << endl;
    }
};

int main() {
    BankAccount account(500);
    cout << "Current Balance: $" << account.getBalance() << endl;

    account.setBalance(1000);  // Valid update
    cout << "Updated Balance: $" << account.getBalance() << endl;

    account.setBalance(-200);  // Invalid update
    return 0;
}

Output:
Current Balance: $500
Updated Balance: $1000
Invalid balance!

✅ Key Takeaway:
Encapsulation ensures controlled access to private data.
Setters can include validation to prevent incorrect values.

5. Data Validation in Setters
🔹 Data validation ensures that only valid values are assigned to properties.
 🔹 This helps prevent errors and enforce business rules.
Example: Data Validation in Setters
class Student {
  private:
    int age;

  public:
    void setAge(int a) {
        if (a > 0 && a < 120)  // Ensuring valid age
            age = a;
        else
            cout << "Invalid age!" << endl;
    }

    int getAge() const {
        return age;
    }
};

int main() {
    Student student;
    student.setAge(20);
    cout << "Age: " << student.getAge() << endl;

    student.setAge(-5);  // Invalid input
    return 0;
}

Output:
Age: 20
Invalid age!

✅ Key Takeaway:
Setters should validate data before modifying private attributes.
Prevents invalid or dangerous values from being stored.


4. Inheritance in C++
Inheritance is one of the four main pillars of Object-Oriented Programming (OOP). It allows a new class (child class or derived class) to inherit properties and behavior from an existing class (parent class or base class).
Why Inheritance?
✔ Code Reusability → Avoid rewriting the same code in multiple classes.
 ✔ Hierarchy Representation → Represents relationships between objects.
 ✔ Extensibility → Modify or extend existing functionality easily.

4.1 Basic Inheritance
Syntax of Inheritance
class BaseClass {
    // Base class members
};

class DerivedClass : public BaseClass {
    // Derived class members
};

Here, DerivedClass inherits from BaseClass, meaning it gets access to its members based on access specifiers.

1. Single Inheritance
A single derived class inherits from a single base class.
Example: Single Inheritance
#include <iostream>
using namespace std;

// Base class
class Vehicle {
  public:
    void move() {
        cout << "This vehicle is moving!" << endl;
    }
};

// Derived class
class Car : public Vehicle {
  public:
    void honk() {
        cout << "Car is honking!" << endl;
    }
};

int main() {
    Car myCar;
    myCar.move();  // Inherited function from Vehicle class
    myCar.honk();  // Function from Car class
    return 0;
}

Output:
This vehicle is moving!
Car is honking!

✅ Key Takeaway:
The Car class inherits the move() function from Vehicle.
It can also have its own functions like honk().

2. Multiple Inheritance
A child class inherits from multiple parent classes.
Example: Multiple Inheritance
#include <iostream>
using namespace std;

// First Base Class
class Engine {
  public:
    void start() {
        cout << "Engine started!" << endl;
    }
};

// Second Base Class
class Wheels {
  public:
    void rotate() {
        cout << "Wheels are rotating!" << endl;
    }
};

// Derived Class
class Car : public Engine, public Wheels {
  public:
    void drive() {
        cout << "Car is driving!" << endl;
    }
};

int main() {
    Car myCar;
    myCar.start();   // Inherited from Engine class
    myCar.rotate();  // Inherited from Wheels class
    myCar.drive();   // Function of Car class
    return 0;
}

Output:
Engine started!
Wheels are rotating!
Car is driving!

✅ Key Takeaway:
Multiple inheritance allows a class to inherit from multiple base classes.
Be careful with naming conflicts if both base classes have functions with the same name.

3. Multi-Level Inheritance
A class inherits from another derived class, forming a chain.
Example: Multi-Level Inheritance
#include <iostream>
using namespace std;

// Base Class
class Vehicle {
  public:
    void move() {
        cout << "This vehicle moves!" << endl;
    }
};

// Derived Class (Child of Vehicle)
class Car : public Vehicle {
  public:
    void honk() {
        cout << "Car is honking!" << endl;
    }
};

// Further Derived Class (Child of Car)
class SportsCar : public Car {
  public:
    void turboBoost() {
        cout << "SportsCar activated Turbo Boost!" << endl;
    }
};

int main() {
    SportsCar myCar;
    myCar.move();      // Inherited from Vehicle
    myCar.honk();      // Inherited from Car
    myCar.turboBoost();// Own function
    return 0;
}

Output:
This vehicle moves!
Car is honking!
SportsCar activated Turbo Boost!

✅ Key Takeaway:
Multi-level inheritance allows deeper hierarchy levels.
Each derived class inherits all public and protected members from its parent.

4. Access Modes in Inheritance
C++ provides three modes of inheritance:
Mode
Private Members
Protected Members
Public Members
Public Inheritance
❌ Not Inherited
✅ Inherited as Protected
✅ Inherited as Public
Protected Inheritance
❌ Not Inherited
✅ Inherited as Protected
✅ Inherited as Protected
Private Inheritance
❌ Not Inherited
✅ Inherited as Private
✅ Inherited as Private

Example: Access Modes
class Base {
  public:
    int x = 10;
  protected:
    int y = 20;
  private:
    int z = 30;
};

// Public Inheritance
class Derived : public Base {
  public:
    void show() {
        cout << "x: " << x << endl;  // ✅ Accessible
        cout << "y: " << y << endl;  // ✅ Accessible
        // cout << "z: " << z;  ❌ Error: Private members are not inherited
    }
};

int main() {
    Derived obj;
    obj.show();
    return 0;
}

✅ Key Takeaway:
Public inheritance keeps the base class's public members public and protected members protected.
Private members are never inherited.

5. Base Class Initialization
When a derived class object is created, the base class constructor runs first.
Example: Base Class Constructor Execution
#include <iostream>
using namespace std;

class Base {
  public:
    Base() {
        cout << "Base class constructor called!" << endl;
    }
};

class Derived : public Base {
  public:
    Derived() {
        cout << "Derived class constructor called!" << endl;
    }
};

int main() {
    Derived obj;
    return 0;
}

Output:
Base class constructor called!
Derived class constructor called!

✅ Key Takeaway:
The base class constructor is always called first when an object of the derived class is created.

6. Constructor Chaining
To initialize a base class with parameters, use constructor chaining.
Example: Constructor Chaining
class Base {
  protected:
    int data;
  public:
    Base(int x) { 
        data = x;
        cout << "Base class initialized with " << x << endl;
    }
};

class Derived : public Base {
  public:
    Derived(int y) : Base(y) {  // Pass argument to Base constructor
        cout << "Derived class initialized with " << y << endl;
    }
};

int main() {
    Derived obj(50);
    return 0;
}

Output:
Base class initialized with 50
Derived class initialized with 50

✅ Key Takeaway:
Derived class constructor can pass parameters to the base class constructor.

4.2 Advanced Inheritance in C++

1. Virtual Functions
A virtual function is a member function in a base class that can be overridden in a derived class. It enables runtime polymorphism (dynamic method dispatch).
Why Virtual Functions?
Without virtual functions, C++ performs early binding (deciding which function to call at compile-time). With virtual functions, late binding (runtime binding) occurs, ensuring that the correct function of the derived class is called.
Example: Virtual Function in C++
#include <iostream>
using namespace std;

class Base {
  public:
    virtual void show() {  // Virtual function
        cout << "Base class function" << endl;
    }
};

class Derived : public Base {
  public:
    void show() override {  // Function overriding
        cout << "Derived class function" << endl;
    }
};

int main() {
    Base* obj;   // Pointer to Base class
    Derived d;
    obj = &d;
    
    obj->show();  // Calls Derived class function due to late binding
    return 0;
}

Output:
Derived class function

✅ Key Takeaway:
The show() function in the Derived class overrides the base class version because of virtual.
If virtual was removed, the Base class function would have been called instead (early binding).

2. Abstract Classes and Pure Virtual Functions
An abstract class in C++ cannot be instantiated. It serves as a blueprint for derived classes. A class becomes abstract when it has at least one pure virtual function.
A pure virtual function is declared using = 0 syntax and must be overridden in derived classes.
Example: Abstract Class & Pure Virtual Function
#include <iostream>
using namespace std;

// Abstract class
class Shape {
  public:
    virtual void draw() = 0;  // Pure virtual function
};

class Circle : public Shape {
  public:
    void draw() override {
        cout << "Drawing Circle" << endl;
    }
};

class Square : public Shape {
  public:
    void draw() override {
        cout << "Drawing Square" << endl;
    }
};

int main() {
    Shape* s1 = new Circle();
    Shape* s2 = new Square();

    s1->draw();  // Calls Circle's draw()
    s2->draw();  // Calls Square's draw()

    delete s1;
    delete s2;
    return 0;
}

Output:
Drawing Circle
Drawing Square

✅ Key Takeaway:
Shape is an abstract class since it has a pure virtual function.
Derived classes must override pure virtual functions.

3. Interface Implementation
In C++, interfaces are simulated using abstract classes with only pure virtual functions.
Example: Interface in C++
#include <iostream>
using namespace std;

// Interface (Abstract Class with only Pure Virtual Functions)
class Drawable {
  public:
    virtual void draw() = 0;  // Pure virtual function
};

class Circle : public Drawable {
  public:
    void draw() override {
        cout << "Drawing Circle" << endl;
    }
};

class Rectangle : public Drawable {
  public:
    void draw() override {
        cout << "Drawing Rectangle" << endl;
    }
};

int main() {
    Drawable* obj1 = new Circle();
    Drawable* obj2 = new Rectangle();

    obj1->draw();  // Calls Circle's draw()
    obj2->draw();  // Calls Rectangle's draw()

    delete obj1;
    delete obj2;
    return 0;
}

Output:
Drawing Circle
Drawing Rectangle

✅ Key Takeaway:
Interfaces in C++ are simulated using abstract classes.
The class Drawable has only pure virtual functions, making it act as an interface.

4. The Diamond Problem
The diamond problem occurs in multiple inheritance when a class inherits from two classes that both inherit from a common base class. This can lead to ambiguity in function calls.
Problem Example:
#include <iostream>
using namespace std;

class A {
  public:
    void show() {
        cout << "Class A" << endl;
    }
};

class B : public A {};  // Inherits A
class C : public A {};  // Inherits A

class D : public B, public C {};  // D has two copies of A

int main() {
    D obj;
    // obj.show();  // ❌ ERROR: Ambiguous function call
    return 0;
}

Why is this an issue?
D inherits A twice (once via B and once via C), creating two separate copies of A.
Calling show() from D causes ambiguity (compiler doesn't know which A::show() to call).

5. Virtual Inheritance (Solution to Diamond Problem)
To resolve the diamond problem, use virtual inheritance. This ensures only one instance of the base class exists.
Solution: Using Virtual Inheritance
#include <iostream>
using namespace std;

class A {
  public:
    void show() {
        cout << "Class A" << endl;
    }
};

class B : virtual public A {};  // Virtual Inheritance
class C : virtual public A {};  // Virtual Inheritance

class D : public B, public C {};  // No duplicate copies of A

int main() {
    D obj;
    obj.show();  // ✅ Calls A::show() without ambiguity
    return 0;
}

Output:
Class A

✅ Key Takeaway:
B and C inherit A virtually, ensuring only one copy of A exists in D.
Virtual inheritance solves ambiguity issues in multiple inheritance.

5. Polymorphism in C++
Polymorphism means "many forms." In C++, it allows functions or operators to behave differently based on the input type or context.
There are two types of polymorphism in C++:
Compile-time polymorphism (Early Binding or Static Polymorphism)
Run-time polymorphism (Late Binding or Dynamic Polymorphism)
This section covers compile-time polymorphism.

5.1 Compile-time Polymorphism
Compile-time polymorphism is achieved using:
 ✔ Function Overloading
 ✔ Operator Overloading
 ✔ Templates (Function & Class Templates)
 ✔ Static Binding
1. Function Overloading
Function overloading allows multiple functions with the same name but different parameters (different number or types of parameters).
Example: Function Overloading
#include <iostream>
using namespace std;

class Math {
  public:
    // Function to add two integers
    int add(int a, int b) {
        return a + b;
    }

    // Function to add three integers
    int add(int a, int b, int c) {
        return a + b + c;
    }

    // Function to add two double values
    double add(double a, double b) {
        return a + b;
    }
};

int main() {
    Math obj;
    cout << "Sum of 2 integers: " << obj.add(5, 10) << endl;
    cout << "Sum of 3 integers: " << obj.add(5, 10, 15) << endl;
    cout << "Sum of 2 doubles: " << obj.add(3.5, 2.2) << endl;
    return 0;
}

Output:
Sum of 2 integers: 15
Sum of 3 integers: 30
Sum of 2 doubles: 5.7

✅ Key Takeaway:
The same function name (add) is used, but with different parameters.
The compiler determines which function to call at compile-time (static binding).

2. Operator Overloading
C++ allows us to overload operators to work with user-defined types (e.g., classes).
Example: Overloading + Operator
#include <iostream>
using namespace std;

class Complex {
  public:
    int real, imag;

    Complex(int r, int i) : real(r), imag(i) {}

    // Overload + operator
    Complex operator+(const Complex& obj) {
        return Complex(real + obj.real, imag + obj.imag);
    }

    void display() {
        cout << real << " + " << imag << "i" << endl;
    }
};

int main() {
    Complex c1(3, 4), c2(1, 2);
    Complex c3 = c1 + c2;  // Calls overloaded operator+
    c3.display(); 
    return 0;
}

Output:
4 + 6i

✅ Key Takeaway:
The + operator is overloaded to work with the Complex class.
This enables adding two objects like primitive data types.

3. Template Functions
Templates allow writing generic functions that work with any data type.
Example: Template Function
#include <iostream>
using namespace std;

// Template function
template <typename T>
T findMax(T a, T b) {
    return (a > b) ? a : b;
}

int main() {
    cout << "Max of 5 and 10: " << findMax(5, 10) << endl;
    cout << "Max of 3.5 and 2.8: " << findMax(3.5, 2.8) << endl;
    return 0;
}

Output:
Max of 5 and 10: 10
Max of 3.5 and 2.8: 3.5

✅ Key Takeaway:
The same function works with both integers and floating-point numbers.
The compiler automatically generates function definitions for the required data types.

4. Template Classes
Template classes allow creating reusable, type-independent classes.
Example: Template Class
#include <iostream>
using namespace std;

// Template class
template <typename T>
class Box {
  private:
    T value;
  public:
    Box(T val) : value(val) {}
    void show() { cout << "Value: " << value << endl; }
};

int main() {
    Box<int> intBox(10);
    Box<double> doubleBox(5.5);

    intBox.show();
    doubleBox.show();
    
    return 0;
}

Output:
Value: 10
Value: 5.5

✅ Key Takeaway:
Box<int> works with integers, and Box<double> works with floating-point numbers.
A single template definition handles multiple data types.

5. Static Binding
Static binding happens at compile-time, meaning the compiler determines which function to call before execution.
Example: Static Binding
#include <iostream>
using namespace std;

class Base {
  public:
    void show() {  // Non-virtual function
        cout << "Base class function" << endl;
    }
};

class Derived : public Base {
  public:
    void show() {  // Function Overriding (Not Virtual)
        cout << "Derived class function" << endl;
    }
};

int main() {
    Base* obj;
    Derived d;
    obj = &d;
    
    obj->show();  // Calls Base class function due to static binding
    return 0;
}

Output:
Base class function

✅ Key Takeaway:
Since show() in Base is not virtual, static binding happens.
Even though obj points to a Derived object, Base::show() is called.
To enable dynamic binding, use virtual in the base class function.

5.2 Runtime Polymorphism in C++
Runtime polymorphism allows function calls to be resolved at runtime instead of compile-time. It is achieved through:
 ✔ Virtual functions
 ✔ Dynamic binding
 ✔ Virtual destructors
 ✔ override and final keywords
 ✔ Dynamic casting

1. Virtual Functions
A virtual function in C++ is a function declared in the base class and overridden in the derived class. When using a base class pointer, the function call is resolved at runtime, ensuring the correct function is called from the derived class.
Example: Virtual Function
#include <iostream>
using namespace std;

class Base {
public:
    virtual void show() {  // Virtual function
        cout << "Base class show() function" << endl;
    }
};

class Derived : public Base {
public:
    void show() override {  // Overriding base class function
        cout << "Derived class show() function" << endl;
    }
};

int main() {
    Base* ptr;  
    Derived d;  
    ptr = &d;  // Base class pointer pointing to Derived class object

    ptr->show();  // Calls Derived's show() due to runtime polymorphism
    return 0;
}

Output:
Derived class show() function

✅ Key Takeaway:
If show() in Base was not virtual, the base class version would have been called.
Since show() is virtual, the derived class version is called at runtime.

2. Dynamic Binding (Late Binding)
Dynamic binding means function calls are resolved at runtime using the vtable (virtual table) mechanism.
Example: Without Virtual Function (Static Binding)
#include <iostream>
using namespace std;

class Base {
public:
    void show() {  // Not virtual
        cout << "Base class show() function" << endl;
    }
};

class Derived : public Base {
public:
    void show() {  // Overriding function
        cout << "Derived class show() function" << endl;
    }
};

int main() {
    Base* ptr;
    Derived d;
    ptr = &d;

    ptr->show();  // Calls Base's show() due to static binding
    return 0;
}

Output:
Base class show() function

💡 Solution? Use virtual functions to enable dynamic binding!

3. Virtual Destructors
If a class has virtual functions, always use a virtual destructor to ensure proper cleanup of derived class objects.
Example: Without Virtual Destructor (Memory Leak)
#include <iostream>
using namespace std;

class Base {
public:
    Base() { cout << "Base Constructor" << endl; }
    ~Base() { cout << "Base Destructor" << endl; }
};

class Derived : public Base {
public:
    Derived() { cout << "Derived Constructor" << endl; }
    ~Derived() { cout << "Derived Destructor" << endl; }
};

int main() {
    Base* ptr = new Derived();
    delete ptr;  // Only Base destructor is called!
    return 0;
}

Output (Incorrect Cleanup)
Base Constructor
Derived Constructor
Base Destructor

🚨 Problem: The Derived destructor is never called, leading to memory leaks.
Solution: Use Virtual Destructor
class Base {
public:
    Base() { cout << "Base Constructor" << endl; }
    virtual ~Base() { cout << "Base Destructor" << endl; }  // Virtual destructor
};

Correct Output
Base Constructor
Derived Constructor
Derived Destructor
Base Destructor

✅ Key Takeaway:
If the base class destructor is not virtual, only the base class destructor is called.
Always use virtual destructors when using runtime polymorphism.

4. override Keyword
The override keyword ensures that a function overrides a virtual function in the base class. If no matching function exists, the compiler throws an error.
Example: Using override Correctly
class Base {
public:
    virtual void show() {}
};

class Derived : public Base {
public:
    void show() override {}  // Correct
};

Example: Incorrect Override
class Derived : public Base {
public:
    void show(int x) override {}  // ERROR: No matching function in base class
};

✅ Key Takeaway:
Use override to prevent accidental mistakes when overriding virtual functions.

5. final Keyword
The final keyword prevents further overriding of a function or class.
Example: Using final
class Base {
public:
    virtual void show() final {}  // No further overrides allowed
};

class Derived : public Base {
public:
    // void show() {}  // ERROR: Cannot override final function
};

Example: Final Class
class FinalClass final {};  

class Derived : public FinalClass {  // ERROR: Cannot inherit from a final class
};

✅ Key Takeaway:
Use final for security and performance when no further overriding is needed.

6. Dynamic Casting
Dynamic casting allows safely downcasting (casting a base class pointer to a derived class pointer). It works only for polymorphic classes (classes with at least one virtual function).
Example: Dynamic Casting
#include <iostream>
using namespace std;

class Base {
public:
    virtual void show() {}  // Must be virtual
};

class Derived : public Base {
public:
    void display() { cout << "Derived class function" << endl; }
};

int main() {
    Base* basePtr = new Derived();

    // Safe downcasting using dynamic_cast
    Derived* derivedPtr = dynamic_cast<Derived*>(basePtr);
    
    if (derivedPtr) {  // Check if casting succeeded
        derivedPtr->display();
    } else {
        cout << "Failed to cast!" << endl;
    }

    delete basePtr;
    return 0;
}

Output:
Derived class function

✅ Key Takeaway:
dynamic_cast ensures safe downcasting and prevents undefined behavior.

6. Advanced OOP Concepts


6.1 Composition and Aggregation in C++
In Object-Oriented Programming (OOP), composition and aggregation are used to represent "has-a" relationships between objects. They define how objects are related and how their lifecycles are managed.

1. Composition vs. Aggregation
Both composition and aggregation establish part-whole relationships, but they differ in ownership and lifecycle dependency.
Concept
Definition
Example
Composition
Strong relationship where the contained object cannot exist independently of the container.
A car has-a engine. If the car is destroyed, the engine is also destroyed.
Aggregation
Weaker relationship where the contained object can exist independently of the container.
A university has-a student. If the university closes, students still exist.


2. Composition (Strong Relationship)
Owner (container) manages the lifetime of the contained objects.
If the container is destroyed, the contained objects are also destroyed.
Implemented using member objects (not pointers).
Example: Composition (Car and Engine)
#include <iostream>
using namespace std;

class Engine {
public:
    Engine() { cout << "Engine Created" << endl; }
    ~Engine() { cout << "Engine Destroyed" << endl; }
    void start() { cout << "Engine Started" << endl; }
};

class Car {
private:
    Engine engine;  // Engine is part of Car (strong relationship)
public:
    Car() { cout << "Car Created" << endl; }
    ~Car() { cout << "Car Destroyed" << endl; }
    void startCar() { engine.start(); }
};

int main() {
    Car myCar;  // Engine is created when Car is created
    myCar.startCar();
    return 0;
}  // Car is destroyed, so Engine is also destroyed.

Output:
Engine Created
Car Created
Engine Started
Car Destroyed
Engine Destroyed

✅ Key Takeaways:
The Engine object is automatically created when a Car object is created.
When Car is destroyed, Engine is also destroyed.

3. Aggregation (Weak Relationship)
Owner does not manage the lifetime of the contained objects.
If the container is destroyed, the contained objects still exist.
Implemented using pointers or references.
Example: Aggregation (Student and University)
#include <iostream>
using namespace std;

class Student {
public:
    string name;
    Student(string n) : name(n) {}
    void show() { cout << "Student: " << name << endl; }
};

class University {
private:
    Student* student;  // Pointer (weak relationship)
public:
    University(Student* s) : student(s) {}  // Linking student to university
    void showStudent() { student->show(); }
};

int main() {
    Student s1("Alice");
    University uni(&s1);  // Student exists outside University
    uni.showStudent();

    return 0;
}  // Student still exists even after University is destroyed.

Output:
Student: Alice

✅ Key Takeaways:
Student object exists independently of University.
The University object only holds a reference to a Student.

4. Dependency Management
In composition, dependencies are strong. The object cannot function without its parts.
In aggregation, dependencies are weak, meaning objects can exist without each other.
Example: Dependency in Composition
class Body {
public:
    void function() { cout << "Body is functioning." << endl; }
};

class Human {
private:
    Body body;  // Composition: Human cannot exist without a body
public:
    void live() { body.function(); }
};

Example: Dependency in Aggregation
class Teacher {
public:
    void teach() { cout << "Teaching students." << endl; }
};

class School {
private:
    Teacher* teacher;  // Aggregation: School has a teacher but doesn't own it
public:
    School(Teacher* t) : teacher(t) {}
    void startClass() { teacher->teach(); }
};


5. Ownership Semantics
Composition = Strong ownership (one object owns another).
Aggregation = Shared ownership (one object references another but doesn’t manage it).
✅ Use Composition When:
Parts cannot exist independently (e.g., Engine in Car).
The owner controls the object’s lifecycle.
✅ Use Aggregation When:
Objects exist independently (e.g., Student and University).
The owner does not control the object’s lifecycle.

6. Lifecycle Management
Object Creation & Destruction
Composition: Contained objects are created and destroyed with the owner.
Aggregation: Contained objects must be created and destroyed separately.
Example: Handling Aggregation with Dynamic Memory
class Library {
private:
    string name;
public:
    Library(string n) : name(n) {}
    void show() { cout << "Library: " << name << endl; }
};

class City {
private:
    Library* library;  // Aggregation (heap allocation)
public:
    City(string libName) { library = new Library(libName); }
    ~City() { delete library; }  // Manually deleting object
    void showLibrary() { library->show(); }
};

int main() {
    City c("Central Library");
    c.showLibrary();
    return 0;
}  // Library must be manually destroyed

✅ Key Takeaways:
If aggregation uses raw pointers, memory must be managed manually.
Smart pointers (shared_ptr, unique_ptr) can help with automatic memory management.


6.2 SOLID Principles in Object-Oriented Programming
The SOLID principles are five fundamental design principles that improve software maintainability, scalability, and flexibility. They help create clean, reusable, and efficient code in object-oriented programming (OOP).

1. Single Responsibility Principle (SRP)
"A class should have only one reason to change."
✅ Explanation:
Each class should have only one job.
If a class has multiple responsibilities, changes in one responsibility might affect others, making the code difficult to maintain.
❌ Bad Example (Violating SRP)
class Report {
public:
    void generateReport() { cout << "Generating report..." << endl; }
    void printReport() { cout << "Printing report..." << endl; }  // Printing is a different responsibility
    void saveToFile() { cout << "Saving report to file..." << endl; }  // File handling is separate
};

🔴 Problem: This class mixes multiple responsibilities:
Generating the report
Printing the report
Saving the report to a file
✅ Good Example (Following SRP)
class Report {
public:
    void generateReport() { cout << "Generating report..." << endl; }
};

class ReportPrinter {
public:
    void printReport() { cout << "Printing report..." << endl; }
};

class ReportSaver {
public:
    void saveToFile() { cout << "Saving report to file..." << endl; }
};

✔ Now each class has a single responsibility and can be modified independently.

2. Open-Closed Principle (OCP)
"Software entities (classes, modules, functions) should be open for extension, but closed for modification."
✅ Explanation:
We should extend existing functionality without modifying existing code.
Achieved using inheritance and polymorphism.
❌ Bad Example (Violating OCP)
class Shape {
public:
    string type;
    void draw() {
        if (type == "Circle") cout << "Drawing Circle..." << endl;
        else if (type == "Square") cout << "Drawing Square..." << endl;
    }
};

🔴 Problem: If we add a new shape (e.g., Triangle), we must modify draw(), violating OCP.
✅ Good Example (Following OCP)
class Shape {
public:
    virtual void draw() = 0;  // Pure virtual function
};

class Circle : public Shape {
public:
    void draw() override { cout << "Drawing Circle..." << endl; }
};

class Square : public Shape {
public:
    void draw() override { cout << "Drawing Square..." << endl; }
};

✔ Now, new shapes can be added without modifying existing code.

3. Liskov Substitution Principle (LSP)
"Objects of a derived class should be able to replace objects of the base class without affecting correctness."
✅ Explanation:
A subclass must fully substitute its base class without changing behavior.
If a subclass breaks the functionality of the base class, it violates LSP.
❌ Bad Example (Violating LSP)
class Bird {
public:
    virtual void fly() { cout << "Flying..." << endl; }
};

class Penguin : public Bird {
public:
    void fly() override { throw logic_error("Penguins can't fly!"); }
};

🔴 Problem:
Penguins cannot fly, but they inherit the fly() method, violating LSP.
Any code expecting all Bird objects to fly will break.
✅ Good Example (Following LSP)
class Bird {
public:
    virtual void makeSound() { cout << "Chirping..." << endl; }
};

class FlyingBird : public Bird {
public:
    virtual void fly() { cout << "Flying..." << endl; }
};

class Sparrow : public FlyingBird {};
class Penguin : public Bird {};  // No fly method in Penguin

✔ Now, Penguin does not inherit fly(), preventing incorrect behavior.

4. Interface Segregation Principle (ISP)
"Clients should not be forced to depend on interfaces they do not use."
✅ Explanation:
Large interfaces should be split into smaller, more specific ones.
A class should only implement methods it actually needs.
❌ Bad Example (Violating ISP)
class Machine {
public:
    virtual void print() = 0;
    virtual void scan() = 0;
    virtual void fax() = 0;
};

class Printer : public Machine {
public:
    void print() override { cout << "Printing..." << endl; }
    void scan() override { throw logic_error("Not supported!"); }  // Unnecessary method
    void fax() override { throw logic_error("Not supported!"); }  // Unnecessary method
};

🔴 Problem:
A Printer should not implement scan() or fax().
✅ Good Example (Following ISP)
class IPrinter {
public:
    virtual void print() = 0;
};

class IScanner {
public:
    virtual void scan() = 0;
};

class Printer : public IPrinter {
public:
    void print() override { cout << "Printing..." << endl; }
};

class Scanner : public IScanner {
public:
    void scan() override { cout << "Scanning..." << endl; }
};

✔ Now, each class implements only the required interface.

5. Dependency Inversion Principle (DIP)
"High-level modules should not depend on low-level modules. Both should depend on abstractions."
✅ Explanation:
Depend on abstract interfaces instead of concrete classes.
Helps with flexibility and scalability.
❌ Bad Example (Violating DIP)
class LightBulb {
public:
    void turnOn() { cout << "Light ON" << endl; }
};

class Switch {
private:
    LightBulb bulb;
public:
    void press() { bulb.turnOn(); }
};

🔴 Problem:
Switch depends directly on LightBulb, making changes harder.
✅ Good Example (Following DIP)
class Switchable {
public:
    virtual void turnOn() = 0;
};

class LightBulb : public Switchable {
public:
    void turnOn() override { cout << "Light ON" << endl; }
};

class Switch {
private:
    Switchable* device;
public:
    Switch(Switchable* d) : device(d) {}
    void press() { device->turnOn(); }
};

int main() {
    LightBulb bulb;
    Switch mySwitch(&bulb);
    mySwitch.press();  // Works with any Switchable device!
}

✔ Now, Switch works with any Switchable device, improving flexibility.

6.3 Modern C++ Features in Object-Oriented Programming
Modern C++ (C++11, C++14, C++17, C++20) introduced several features that enhance OOP by improving memory management, efficiency, and flexibility. Let's explore key modern C++ features related to OOP.

1. Smart Pointers (Memory Management)
Smart pointers in C++ manage memory automatically and help prevent memory leaks by deallocating memory when it is no longer needed.
✅ Types of Smart Pointers:
std::unique_ptr – Owns an object exclusively (no copying).
std::shared_ptr – Allows multiple shared ownership.
std::weak_ptr – Prevents circular references in shared_ptr.
Example: Using std::unique_ptr
#include <iostream>
#include <memory>  // Required for smart pointers

class Car {
public:
    Car() { std::cout << "Car Created\n"; }
    ~Car() { std::cout << "Car Destroyed\n"; }
    void drive() { std::cout << "Driving...\n"; }
};

int main() {
    std::unique_ptr<Car> car = std::make_unique<Car>();  // Creates a unique_ptr
    car->drive();  // Access object methods
    return 0;
}  // `car` is automatically destroyed when it goes out of scope

✔ No need to manually delete the object – memory is handled automatically!

2. Move Semantics (Efficient Resource Transfer)
Move semantics eliminate unnecessary copying of objects, improving performance.
✅ How Move Semantics Work?
Introduces rvalue references (&&), which allow moving resources instead of copying.
Used in move constructors and move assignment operators.
Example: Move Constructor
#include <iostream>
#include <vector>

class Data {
private:
    std::vector<int> numbers;
public:
    Data(std::vector<int> vec) : numbers(std::move(vec)) {  // Move constructor
        std::cout << "Move Constructor Called\n";
    }
};

int main() {
    std::vector<int> vec = {1, 2, 3, 4, 5};
    Data obj(std::move(vec));  // Moves `vec` into `obj`, avoiding expensive copy
    return 0;
}

✔ std::move(vec) transfers ownership instead of copying the vector.

3. Perfect Forwarding (Efficient Function Arguments)
Perfect forwarding allows preserving the type of arguments passed to a function without unnecessary copies.
Example: Using std::forward
#include <iostream>
#include <utility>  // Required for std::forward

class Example {
public:
    template <typename T>
    void process(T&& value) {  // Universal reference
        forward(value);
    }

    void forward(const std::string& str) {
        std::cout << "Lvalue: " << str << std::endl;
    }

    void forward(std::string&& str) {
        std::cout << "Rvalue: " << str << std::endl;
    }
};

int main() {
    Example obj;
    std::string text = "Hello";
    
    obj.process(text);  // Calls lvalue version
    obj.process(std::move(text));  // Calls rvalue version
}

✔ Preserves the type of arguments, improving function efficiency.

4. Lambda Expressions (Inline Functions)
Lambdas are anonymous functions that simplify code by replacing small function objects or callbacks.
✅ Lambda Syntax
[capture](parameters) -> return_type { function_body };

Example: Using a Lambda
#include <iostream>
#include <vector>
#include <algorithm>

int main() {
    std::vector<int> numbers = {1, 2, 3, 4, 5};

    std::for_each(numbers.begin(), numbers.end(), [](int n) {
        std::cout << n * 2 << " ";
    });
    
    return 0;
}

✔ Lambdas improve readability and reduce the need for extra functions.

5. STL Containers with Objects
STL (Standard Template Library) containers like vector, map, and unordered_map work well with objects.
Example: std::vector of Objects
#include <iostream>
#include <vector>

class Car {
public:
    std::string brand;
    Car(std::string b) : brand(b) {}
    void show() { std::cout << "Car Brand: " << brand << std::endl; }
};

int main() {
    std::vector<Car> cars = { Car("Toyota"), Car("Honda"), Car("BMW") };

    for (const auto& car : cars) {
        car.show();
    }
    return 0;
}

✔ STL containers manage objects efficiently, reducing manual memory handling.




















EXTRA

1. C++ Encapsulation
In C++, object-oriented programming allows us to bundle together data members (such as variables, arrays, etc.) and its related functions into a single entity. This programming feature is known as encapsulation.


In Example 1, we bundled together the related variables brand, model and mileage with the function show_data() into a class named Car.
class Car {
  public:

    // class data
    string brand;
    string model;
    int mileage = 0;

    // class function
    void show_data() {
        // code
    }
};
Encapsulation ensures that only member functions of a class can access its data, which results in data hiding.
In C++, we hide data using the private and protected keywords. In contrast, using the public keyword for certain class members makes those members accessible to all other functions and classes.
Example-2: Consider a real-life example of encapsulation, in a company, there are different sections like the accounts section, finance section, sales section, etc. The finance section handles all the financial transactions and keeps records of all the data related to finance. Similarly, the sales section handles all the sales-related activities and keeps records of all the sales. Now there may arise a situation when for some reason an official from the finance section needs all the data about sales in a particular month. In this case, he is not allowed to directly access the data of the sales section. He will first have to contact some other officer in the sales section and then request him to give the particular data. This is what encapsulation is. Here the data of the sales section and the employees that can manipulate them are wrapped under a single name “sales section”.
Key Features of Encapsulation:
Restricted Direct Access:
Functions inside a class cannot be accessed directly.
An object of the class is required to access these functions that use member variables.
Encapsulation Requires Data Usage Inside Functions:
A function inside a class must use member variables of that class to be considered encapsulated.
Encapsulation is Not Just About Having a Class:
If a function inside a class does not use the class’s member variables, then it is not considered encapsulation.
Improves Code Quality:
Readability & Maintainability: Organizes code in a structured manner.
Security: Protects data from unauthorized access.
Controlled Data Modification:
By using getter and setter methods, encapsulation ensures that data is accessed and modified in a controlled way.
2. C++ Abstraction
In object-oriented programming, abstraction refers to the concept of showing only the necessary information to the user i.e. hiding the complex details of program implementation and execution.
For example, let us consider a slightly modified version of the Car class:
class Car {
  private:

    // class data
    int speed;

    // class function
    void show_car_status() {
        // code
    }
};
Suppose we want the show_car_status() function to show the status of the car based on the value of the speed variable.
We can implement such conditional statements using the if...else statement inside the show_car_status() function.
void show_car_status() {
    if (speed != 0)
        cout << "The car is being driven." << endl;
    else
        cout << "The car is stationary." << endl;
}
Here, we do not need to show the user all the codes we have written to determine if the car is stationary or not; we just need to show them whether the car is being driven or not depending on its speed.
In other words, we are only giving useful and relevant information to the user, while hiding all the unnecessary details.
This is data abstraction in OOP.
To learn more about abstraction, visit our C++ Abstraction tutorial.
Note: Abstraction is not the same as data hiding. Abstraction is showing only the relevant information, while data hiding is restricting access to data members (variables, arrays, structures, etc.) so that they cannot be accessed from outside the class.
3. C++ Inheritance
Inheritance in C++ allows us to create a new class (derived class) from an existing class (base class).
The derived class inherits features from the base class and can have additional features of its own.
#include <iostream>
using namespace std;

// base class
class Vehicle {
  public:

    string brand;
    
    void show_brand() {
        cout << "Brand: " << brand << endl;
    }    
};

// derived class
class Car : public Vehicle {  
  public:
   
    string model;

    void show_model() {
        cout << "Model: " << model << endl;
    }
};

int main() {
    
    // create an object of Car class
    Car my_car;

    // initialize variables of my_car
    my_car.brand = "Honda";
    my_car.model = "Accord";

    // display variables of my_car
    my_car.show_brand();
    my_car.show_model();

    return 0;    
}
Output
Brand: Honda
Model: Accord
Here,
Vehicle is the base class.
Car is the derived class.
The derived class inherits the features of the base class. We can see this from the brand variable and the show_brand() function, since the Car object my_car can access them.
In addition to the features of the base class, the derived class also has features of its own. The unique features of the Car class are:
model - a string variable
show_model() - a function that prints the model variable.
We can also see that the Vehicle class has not been modified by its derived class.
4. C++ Polymorphism
Polymorphism is the ability to use a common function (or operator) in multiple ways.
In C++, polymorphism is implemented with the help of function overloading, operator overloading, function overriding, and virtual functions.
Let's look at function overriding as an example.

