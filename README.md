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
