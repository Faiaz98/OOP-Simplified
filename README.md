 # OOP-Simplified

Object-Oriented Programming (OOP) is a programming paradigm that uses "objects" to design software.

## Outline of OOP Concepts

- Introduction to OOP
- Classes and Objects
- Encapsulation
- Inheritance
- Polymorphism
- Abstraction
- Constructors and Destructors
- Operator Overloading
- Templates and Generic Programming
- Exception Handling

## 1. Introduction to OOP

Object-Oriented Programming (OOP) is a programming paradigm that uses "objects" to design software. Objects represent real-world entities with attributes (data) and behaviors (methods/functions). OOP helps in organizing code, making it more modular, reusable, and easier to understand.

**Example**

```cpp
// Example of a simple class representing a Car
#include <iostream>
#include <string>
using namespace std;

class Car {
public:
    // Attributes
    string brand;
    string model;
    int year;

    // Method
    void displayInfo() {
        cout << "Brand: " << brand << ", Model: " << model << ", Year: " << year << endl;
    }
};

int main() {
    // Creating an object of Car
    Car car1;
    car1.brand = "Toyota";
    car1.model = "Corolla";
    car1.year = 2020;
    
    // Calling the method
    car1.displayInfo();

    return 0;
}
```

## 2. Classes and Objects

A class is a blueprint for creating objects. It defines the properties and behaviors that the objects created from the class will have. An object is an instance of a class.

**Example**

```cpp
#include <iostream>
#include <string>
using namespace std;

class Person {
public:
    string name;
    int age;

    void introduce() {
        cout << "Hi, my name is " << name << " and I am " << age << " years old." << endl;
    }
};

int main() {
    Person person1;
    person1.name = "Alice";
    person1.age = 30;
    
    person1.introduce();

    return 0;
}
```

## 3. Encapsulation

Encapsulation is the concept of bundling data and methods that operate on that data within a single unit, typically a class. It restricts direct access to some of the object's components, which is a means of preventing accidental interference and misuse of the methods and data.

**Example**

```cpp
#include <iostream>
#include <string>

class BankAccount {
private:
    std::string owner;
    double balance;

public:
    BankAccount(std::string owner, double balance) : owner(owner), balance(balance) {}

    void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
        }
    }

    void withdraw(double amount) {
        if (amount > 0 && amount <= balance) {
            balance -= amount;
        }
    }

    void displayBalance() {
        std::cout << "Owner: " << owner << ", Balance: $" << balance << std::endl;
    }
};

int main() {
    BankAccount account("John Doe", 1000.0);
    account.deposit(500.0);
    account.withdraw(200.0);
    account.displayBalance();

    return 0;
}
```

## 4. Inheritance

Inheritance allows a class to inherit properties and behaviors from another class. The class that inherits is called the derived class (or child class), and the class being inherited from is the base class (or parent class). This promotes class reusability.

**Example**

```cpp
#include <iostream>
#include <string>
using namespace std;

// Base class
class Animal {
public:
    std::string name;
    void eat() {
        cout << name << " is eating." << endl;
    }
};

// Derived class
class Dog : public Animal {
public:
    void bark() {
        cout << name << " is barking." << endl;
    }
};

int main() {
    Dog dog1;
    dog1.name = "Buddy";
    dog1.eat();    // Inherited method
    dog1.bark();   // Dog's own method

    return 0;
}
```
