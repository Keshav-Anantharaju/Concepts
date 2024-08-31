# Object-Oriented Programming (OOP)

Object-Oriented Programming (OOP) is a programming paradigm centered around objects and classes. It aims to model real-world entities and their interactions, making code more modular, reusable, and easier to manage.

## 1. Classes and Objects

**Class:** A blueprint for creating objects. It defines a set of attributes and methods that the objects created from the class will have.
**Object:** An instance of a class. It contains data (attributes) and methods (functions) defined by its class.
Example:

```py
class Car:
    def __init__(self, make, model):
        self.make = make
        self.model = model

    def drive(self):
        print(f"The {self.make} {self.model} is driving.")

my_car = Car("Toyota", "Corolla")
my_car.drive()  # Output: The Toyota Corolla is driving.
```

### 1.1 Creating a class

Creating a class in Python is straightforward.

**Define the Class**: Use the `class` keyword followed by the class name. Class names in Python are typically written in CamelCase (e.g., `MyClass`).

Example:

```py
# Define the class
class Dog:
    pass
```

-   **`Note:`** `pass is a placeholder statement used to indicate that nothing should happen in a certain block of code. `

### 1.2 Constructor and property

Use the `__init__` method, also known as the constructor, to initialize the object’s attributes when it is created.
Example:

```py
# Define the class
class Dog:
    # Constructor method to initialize attributes
    def __init__(self, name, age):
        self.name = name  # Instance attribute
        self.age = age    # Instance attribute
```

### 1.3 Instance Method

-   Methods are functions defined inside a class that describe the behaviors of the objects. The first parameter of a method is always `self`, which refers to the instance of the class.
-   To access these properties within instance methods, use the self keyword.
    Example:

```py
# Define the class
class Dog:
    # Constructor method to initialize attributes
    def __init__(self, name, age):
        self.name = name  # Instance attribute
        self.age = age    # Instance attribute

    # Method to make the dog bark
    def bark(self):
        print(f"{self.name} says Woof!")

    # Method to get the dog's age
    def get_age(self):
        return self.age
```

### 1.4 Creating Instance or objects

```py
# Create an instance of the Dog class
my_dog = Dog("Buddy", 3)
```

This creates an instance of `Dog` named `my_dog`, with `name` set to "Buddy" and `age` set to 3.

### 1.5 Access the attributes and methods

```py
print(my_dog.name)  # Output: Buddy
print(my_dog.get_age())  # Output: 3
my_dog.bark()  # Output: Buddy says Woof!
```

## 2. Class and Objects memory management

-   **Classes**
    -   When a class is defined, Python creates a class object and stores it in memory.
    -   This class object includes the class’s attributes, methods, and other metadata.
    -   The class object is stored in a namespace, which could be the global namespace of a module or a local namespace within a function.
-   **Objects**
    -   When an object (or instance) is created from a class, Python allocates memory for that object, including space for its instance variables and a reference to its class.
    -   The memory location is managed by Python's memory manager and garbage collector.
    -   Objects are stored in a heap, which is a region of memory used for dynamic allocation.

## 3. Comparing two objects

-   To compare two objects in Python, use the `==` operator. This checks if the values of the objects are the same, not if they are the same instance.

    ```py
    class Dog:
        def __init__(self, name):
            self.name = name

    dog1 = Dog("Buddy")
    dog2 = Dog("Buddy")

    print(dog1 == dog2)  # Output: False, because they are different instances
    ```

-   To compare if two objects are the same instance, use `isinstance(object_name, class_name)`

    ```py
    class Dog:
        def __init__(self, name):
            self.name = name

    dog1 = Dog("Buddy")
    dog2 = Dog("Buddy")

    print(isinstance(dog1, Dog) == isinstance(dog1, Dog))  # Output: True
    ```

-   In order to check if the values of two objects are equal we can overide `__eq__()` method with defination in class.

    ```py
    class Dog:
        def __init__(self, name):
            self.name = name

        def __eq__(self, dog_object):
            return (self.name == dog_object.name)


    dog1 = Dog("Buddy")
    dog2 = Dog("Buddy")
    print(dog1 == dog2)
    ```

## 4. Types of variables

### 4.1 Class variable

-   Class variable are shared among all instances/objects of a class.
-   They are defined within the class but outside any methods.

### 4.2 Instance Variables

-   Instance variable are unique to each instance/objects.
-   They are defined within methods, typically in the `__init__` method.

    Examlple:

    ```py
    class Dog:
    species = "Canis familiaris"  # Class variable

    def __init__(self, name):
        self.name = name  # Instance variable

    dog1 = Dog("Buddy")
    print(dog1.species)  # Output: Canis familiaris
    print(dog1.name)     # Output: Buddy
    ```

### 4.3 Updating class variables

-   Class variables are updated using the class name or within class methods.

    Example:

    ```py
    class Dog:
        species = "Canis familiaris"

        @classmethod
        def update_species(cls, new_species):
            cls.species = new_species

    Dog.update_species("Canis lupus")
    print(Dog.species)  # Output: Canis lupus
    ```

## 5. Types of methods

### 5.1 Instance Method:

-   Instance method operates on an property of the class and can access property and class variables.
-   It is defined with self as its first parameter.

### 5.2 Class Method:

-   Operates on the class itself rather than instances.
-   It is defined with `@classmethod` and `cls` as its first parameter.

### 5.3 Static Method:

-   Does not operate on an instance or class.
-   It is defined with `@staticmethod`.
-   It behaves like a regular function but belongs to the class's namespace.

    Example:

    ```py
    class Dog:
    species = "Canis familiaris"

    def __init__(self, name):
        self.name = name

    def instance_method(self):
        return f"{self.name} is a {self.species}"

    @classmethod
    def class_method(cls):
        return f"Species: {cls.species}"

    @staticmethod
    def static_method():
        return "Static method called"

    dog = Dog("Buddy")
    print(dog.instance_method())  # Output: Buddy is a Canis familiaris
    print(Dog.class_method())     # Output: Species: Canis familiaris
    print(Dog.static_method())    # Output: Static method called
    ```

    **Note:** Decorators are functions that modify the behavior of other functions or methods.

### 5.4 Accessors and Mutators

-   **Accessors (getters):** are methods that get the value of an attribute.
-   **Mutators (setters):** Methods that set the value of an attribute.

## 6. Nested class

-   A nested class is defined within another class.
-   It is often used to logically group classes that are only used within the outer class.
    Example:

    ```py
    class OuterClass:
        class InnerClass:
            def __init__(self, value):
                self.value = value

        def __init__(self, inner_value):
            self.inner = self.InnerClass(inner_value) # accessing nested class properties

    outer = OuterClass(42) # initializing nested class properties
    print(outer.inner.value)  # Output: 42
    ```

## 7. Inheritance in Python

**Inheritance** allows a class (child class) to inherit attributes and methods from another class (parent class).

-   This promotes code reuse and organization.

### 7.1 Types of Inheritance:

1. **Single Inheritance:**

    - A child class inherits from one parent class.
    - Example:

        ```python
        class Animal:
            def speak(self):
                return "Animal sound"

        class Dog(Animal):
            def speak(self):
                return "Bark"

        dog = Dog()
        print(dog.speak())  # Output: Bark
        ```

2. **Multilevel Inheritance:**

    - A child class inherits from a parent class, which in turn inherits from another class.
    - Example:

        ```python
        class Animal:
            def speak(self):
                return "Animal sound"

        class Dog(Animal):
            def speak(self):
                return "Bark"

        class Puppy(Dog):
            def speak(self):
                return "Yip"

        puppy = Puppy()
        print(puppy.speak())  # Output: Yip
        ```

3. **Multiple Inheritance:**

    - A child class inherits from more than one parent class.
    - Example:

        ```python
        class Canine:
            def bark(self):
                return "Bark"

        class Mammal:
            def feed_baby_with_milk(self):
                return "Feeding with milk"

        class Dog(Canine, Mammal):
            pass

        dog = Dog()
        print(dog.bark())  # Output: Bark
        print(dog.feed_baby_with_milk())  # Output: Feeding with milk
        ```

### 7.2 Constructor Inheritance:

-   In Python, constructors are inherited by the child class.
-   The child class can override the constructor by defining its own.
-   Example:

    ```python
    class Animal:
        def __init__(self, name):
            self.name = name

    class Dog(Animal):
        def __init__(self, name, breed):
            super().__init__(name)
            self.breed = breed

    dog = Dog("Buddy", "Golden Retriever")
    print(dog.name)  # Output: Buddy
    print(dog.breed)  # Output: Golden Retriever
    ```

### 7.3 `super` Keyword:

-   The `super()` function is used to call a method from the parent class.
-   It's often used to call the parent class's constructor in the child class.
-   Example:

    ```python
    class Animal:
        def __init__(self, name):
            self.name = name

    class Dog(Animal):
        def __init__(self, name, breed):
            super().__init__(name)
            self.breed = breed

    dog = Dog("Buddy", "Golden Retriever")
    ```


### 7.4 Method Resolution Order (MRO):

-   MRO determines the order in which classes are looked up for a method or attribute.
-   Python uses the C3 Linearization algorithm for MRO.
-   MRO can be viewed using the `mro()` method or `__mro__` attribute.
-   Example:

    ```python
    class A:
        def show(self):
            return "A"

    class B(A):
        def show(self):
            return "B"

    class C(B, A):
        pass

    obj = C()
    print(obj.show())  # Output: B
    print(C.mro())     # Output: [<class '__main__.C'>, <class '__main__.B'>, <class '__main__.A'>, <class 'object'>]
    ```


## 8. Polymorphism in Python

**Polymorphism** refers to the ability of different objects to respond to the same function or method call in different ways.

### 8.1 Duck Typing:

-   In Python, the type or class of an object is less important than the methods it defines. This is known as duck typing ("If it looks like a duck and quacks like a duck, it must be a duck").
-   Example:

    ```python
    class Dog:
        def sound(self):
            return "Bark"

    class Cat:
        def sound(self):
            return "Meow"

    def make_sound(animal):
        return animal.sound()

    dog = Dog()
    cat = Cat()
    print(make_sound(dog))  # Output: Bark
    print(make_sound(cat))  # Output: Meow
    ```

### 8.2 Method Overloading:

-   Python does not support method overloading by default. However, this can be achieved by default arguments or checking the type of arguments.
-   Example:

    ```python
    class Math:
        def add(self, a, b, c=None):
            if c:
                return a + b + c
            else:
                return a + b

    math = Math()
    print(math.add(2, 3))       # Output: 5
    print(math.add(2, 3, 4))    # Output: 9
    ```

### 8.3 Operator Overloading:

-   Python allows operators to be overloaded, i.e, to define how operators behave for custom objects.
-   Example:

    ```python
    class Point:
        def __init__(self, x, y):
            self.x = x
            self.y = y

        def __add__(self, other):
            return Point(self.x + other.x, self.y + other.y)

        def __str__(self):
            return f"Point({self.x}, {self.y})"

    p1 = Point(1, 2)
    p2 = Point(3, 4)
    p3 = p1 + p2
    print(p3)  # Output: Point(4, 6)
    ```

#### 8.4 Method Overriding:

-   Method overriding allows a child class to provide a specific implementation of a method that is already defined in its parent class.
-   Example:

    ```python
    class Animal:
        def sound(self):
            return "Some sound"

    class Dog(Animal):
        def sound(self):
            return "Bark"

    dog = Dog()
    print(dog.sound())  # Output: Bark
    ```

## 9. Abstract Methods and Abstract Base Classes

**Abstract Methods** are methods declared in a base class but have no implementation. They must be implemented in any subclass.

**Abstract Base Classes (ABC)** provide a way to define abstract classes. An abstract class cannot be instantiated, and its abstract methods must be defined in a child class.

### 9.1 Creating Abstract Classes:

-   Python provides the `abc` module to define abstract base classes.
-   Example:

    ```python
    from abc import ABC, abstractmethod

    class Animal(ABC):
        @abstractmethod
        def sound(self):
            pass

    class Dog(Animal):
        def sound(self):
            return "Bark"

    dog = Dog()
    print(dog.sound())  # Output: Bark
    ```

In the example above, `Animal` is an abstract class because it contains an abstract method `sound()`. Any subclass of `Animal` must implement the `sound()` method.
