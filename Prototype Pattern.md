- The Prototype Pattern is a creational design pattern that allows you to create new objects by copying an existing object, known as a "prototype".
- This pattern is particularly useful when the cost of creating an object is more expensive than copying it, or when objects need to be created with varying states or configurations.
- Key components of the Prototype Pattern:
	- **Prototype Interface**:
		- This is an interface or abstract class that declares a method for cloning itself. It defines a common interface for all concrete prototypes.
	- **Concrete Prototypes**:
		- These are concrete classes that implement the prototype interface.
		- Each concrete prototype provides its own implementation of the cloning method.
		- These objects serve as templates for creating new instances.
	- **Client**:
		- The client is responsible for creating new objects by requesting clones of existing prototype objects.
		- It interacts with the prototype manager to obtain copies of prototypes.
	- **Prototype Manager (optional)**:
		- In some implementations, a prototype manager or registry may be used to store and manage a collection of prototypes.
		- This makes it easy for clients to access and clone prototypes.

```
// Prototype interface
interface AnimalPrototype {
    AnimalPrototype clone();
    void sound();
}

// Concrete prototype for Dog
class Dog implements AnimalPrototype {
    @Override
    public AnimalPrototype clone() {
        return new Dog();
    }

    @Override
    public void sound() {
        System.out.println("Woof!");
    }
}

// Concrete prototype for Cat
class Cat implements AnimalPrototype {
    @Override
    public AnimalPrototype clone() {
        return new Cat();
    }

    @Override
    public void sound() {
        System.out.println("Meow!");
    }
}

// Client
public class AnimalClient {
    public static void main(String[] args) {
        // Create prototype instances
        AnimalPrototype dogPrototype = new Dog();
        AnimalPrototype catPrototype = new Cat();

        // Clone and use prototypes
        AnimalPrototype newDog = dogPrototype.clone();
        newDog.sound();

        AnimalPrototype newCat = catPrototype.clone();
        newCat.sound();
    }
}
```

#LowLevelDesign #DesignPattern #CreationalPatterns #PrototypePattern #Example 