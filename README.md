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

## 5. Polymorphism

Polymorphism means "many forms". In OOP, it allows methods to do different things based on the object is acting upon, even if the method calls are the same. This can be achieved through method overriding and method overloading.

**Example(Method Overriding)**

```cpp
#include <iostream>
#include <string>
using namespace std;

class Animal {
public:
    virtual void makeSound() {
        cout << "Some generic animal sound" << endl;
    }
};

class Dog : public Animal {
public:
    void makeSound() override {
        cout << "Bark" << endl;
    }
};

class Cat : public Animal {
public:
    void makeSound() override {
        cout << "Meow" << endl;
    }
};

int main() {
    Animal* animal1 = new Dog();
    Animal* animal2 = new Cat();

    animal1->makeSound();  // Outputs: Bark
    animal2->makeSound();  // Outputs: Meow

    delete animal1;
    delete animal2;

    return 0;
}
```

## 6. Abstraction

Abstraction is the concept of hiding the complex implementation details and showing only the necessary features of an object. This can be achieved using abstract classes and interfaces.

**Example**

```cpp
#include <iostream>
#include <string>
using namespace std;

class AbstractDevice {
public:
    virtual void turnOn() = 0;  // Pure virtual function
    virtual void turnOff() = 0; // Pure virtual function
};

class Fan : public AbstractDevice {
public:
    void turnOn() override {
        cout << "Fan is turned on" << endl;
    }

    void turnOff() override {
        cout << "Fan is turned off" << endl;
    }
};

int main() {
    Fan myFan;
    myFan.turnOn();
    myFan.turnOff();

    return 0;
};
```

## 7. Constructors and Destructors

Constructors are special methods that are called when an object is instantiated. They are used to initialize objects. Destructors are called when an object is destroyed and are used to release resources.\

**Example**

```cpp
#include <iostream>
#include <string>
using namespace std;

class Book {
public:
    std::string title;

    // Constructor
    Book(std::string t) : title(t) {
        cout << "Book \"" << title << "\" created." << endl;
    }

    // Destructor
    ~Book() {
        cout << "Book \"" << title << "\" destroyed." << endl;
    }
};

int main() {
    Book myBook("The Great Gatsby");

    return 0;
}
```

## 8. Operation Overloading

Operator overloading allows you to define custom behaviors for operators when they are used with user-defined types(classes). This makes the code more intuitive and easier to read.

```cpp
#include <iostream>
using namespace std;

class Complex {
public:
    int real, imag;

    Complex(int r = 0, int i = 0) : real(r), imag(i) {}

    // Overload + operator
    Complex operator + (const Complex& obj) {
        return Complex(real + obj.real, imag + obj.imag);
    }

    void display() {
        cout << real << " + " << imag << "i" << endl;
    }
};

int main() {
    Complex c1(3, 4), c2(1, 2);
    Complex c3 = c1 + c2;
    c3.display(); // Outputs: 4 + 6i

    return 0;
}
```


## 9. Templates and Generic Programming

Templates allow you to write generic and reusable code. You can create a single function or class to work with different data types.

**Example**

```cpp
#include <iostream>

template <typename T>
class Calculator {
public:
    T add(T a, T b) {
        return a + b;
    }

    T subtract(T a, T b) {
        return a - b;
    }
};

int main() {
    Calculator<int> intCalc;
    cout << "10 + 5 = " << intCalc.add(10, 5) << endl;
    cout << "10 - 5 = " << intCalc.subtract(10, 5) << endl;

    Calculator<double> doubleCalc;
    cout << "10.5 + 5.5 = " << doubleCalc.add(10.5, 5.5) << endl;
    cout << "10.5 - 5.5 = " << doubleCalc.subtract(10.5, 5.5) << endl;

    return 0;
}
```


## 10. Exception Handling

Exception handling is a way to manage error or exceptional situations in your program. It helps in maintaining the normal flow of the program even when errors occur.


```cpp
#include <iostream>
#include <exception>

int main() {
    try {
        int num1 = 10;
        int num2 = 0;

        if (num2 == 0) {
            throw runtime_error("Division by zero error");
        }

        int result = num1 / num2;
        cout << "Result: " << result << endl;
    } catch (const std::runtime_error& e) {
        cerr << "Runtime error: " << e.what() << endl;
    }

    return 0;
}

```
