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
#include <iostream>
#include <string>
using namespace std;

class Person {
public:
    std::string name;
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
