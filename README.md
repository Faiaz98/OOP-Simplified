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

# SOLID Principles

The SOLID princes are five guidelines that help make your code more maintainable, reusable, and scalable.

## 1. Single Responsible Principle (SRP)
### A class should only have one reason to change.

- Real-life Analogy: Think of a chef in a restaurant. The chef only cooks food and doesn't handle billing or customer seating. Similarly, a class should focus on one task.
- Code Example:

```cpp
class Order{
public:
   void addItem(const string& item) {
       items.push_back(item); 
   }
private:
   vector<string> items;
};

class InvoiceGenerator{
public:
    void generateInvoice(const Order& order) {
        //logic for generating invoice
     }
};
```

Here, ```Order``` handles only order-related tasks, and ```InvoiceGenerator```handles billing.


## 2. Open/Closed Principle (OCP)
### A class should be open for extension but closed for modification.

- Real-life Analogy: Imagine a gaming console where you can add new games (extensions) without redesigning the console.
- Code Example:

```cpp
class Discount{
public:
    virtual double calculate(double amount) = 0;
};

class SeasonalDiscount : public Discount {
public:
  double calculate(double amount) override {
    return amount * 0.9; //10% discount
  }
};

class FestivalDiscount : public Discount {
public:
    double calculate(double amount) override {
        return amount * 0.8; // 20% discount
    }
};
```

You can add new discounts without modifying the original ```Discount``` class.

## 3. Liskov Substitution Principle (LSP)
### Objects of a superclass should be replaceable with objects of a subclass without affecting the program.

- Real-life Analogy: If you replace a wired mouse with a wireless one, your computer should work the same way.
- Code Example:

```cpp
class Bird {
public:
    virtual void fly() {
        std::cout << "Flying high!" << std::endl;
    }
};

class Sparrow : public Bird {};
class Penguin : public Bird {
    void fly() override {
        throw std::runtime_error("Penguins can't fly!");
    }
};
```

Here ```Penguin``` violates LSP because it doesn't behave like a ```Bird```. To fix this, create a better hierarchy like FlyingBird and NonFlyingBird.

## 4. Interface Segregation Principle (ISP)
### A class should not be forced to implement methods it doesn't use.

- Real-life Analogy: A food delivery app shouldn't force restaurants to implement a feature for bike delivery if they only do takeout.
- Code Example:

```cpp
class PaymentMethod {
public:
    virtual void payOnline() = 0;
    virtual void payCash() = 0;
};

class OnlinePayment : public PaymentMethod {
public:
    void payOnline() override {
        // Online payment logic
    }
    void payCash() override {
        throw std::runtime_error("Cash not supported");
    }
};

```

### Instead, split interfaces:

```cpp
class OnlinePayment {
public:
    virtual void payOnline() = 0;
};

class CashPayment {
public:
    virtual void payCash() = 0;
};
```

## 5. Dependency Inversion Principle (DIP)
### High-level modules should not depend on low-level modules. Both should depend on abstractions.

- Real-life Analogy: A remote control (high-level) works with different devices like TVs or AC (low-level) using universal signals (abstraction).
- Code Example:


```cpp
class NotificationService {
public:
    virtual void sendNotification(const std::string& message) = 0;
};

class EmailService : public NotificationService {
public:
    void sendNotification(const std::string& message) override {
        std::cout << "Email: " << message << std::endl;
    }
};

class SMSService : public NotificationService {
public:
    void sendNotification(const std::string& message) override {
        std::cout << "SMS: " << message << std::endl;
    }
};

class Alert {
    NotificationService& notifier;
public:
    Alert(NotificationService& service) : notifier(service) {}
    void triggerAlert() {
        notifier.sendNotification("ALERT! Check immediately.");
    }
};

```

The ```Alert``` class depends on an abstraction (```NotificationService```), making it flexible to work with both ```EmailService``` and ```SMSService```.
