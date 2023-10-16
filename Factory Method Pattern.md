- The Factory Method Pattern is a creational design pattern that provides an interface for creating objects, but it lets subclasses alter the type of objects that will be created.
- It promotes the idea of "deferring the instantiation of an object to its subclasses".
- This pattern is useful when you have a class that cannot anticipate the type of objects it needs to create or when you want to delegate the responsibility of object creation to its subclasses.
- Key components of the Factory Method Pattern:
	- **Creator Interface**:
		- This is an abstract class or interface that declares a method (the factory method) for creating objects.
		- The creator class may also contain some default implementation shared by all its concrete subclasses.
	- **Concrete Creator Classes**:
		- These are subclasses of the creator interface that provide specific implementations for the factory method. Each concrete creator class is responsible for creating a particular type of object.
	- **Product Interface**:
		- This is an abstract class or interface that defines the common interface for all products created by the factory method.
	- **Concrete Product Classes**:
		- These are the actual classes that implement the product interface. They represent the specific types of objects that the factory method creates.


```
// Product interface
interface Product {
    void create();
}

// Concrete product
class ConcreteProductA implements Product {
    @Override
    public void create() {
        System.out.println("Product A is created");
    }
}

// Concrete product
class ConcreteProductB implements Product {
    @Override
    public void create() {
        System.out.println("Product B is created");
    }
}

// Creator interface
interface Creator {
    Product factoryMethod();
}

// Concrete creator
class ConcreteCreatorA implements Creator {
    @Override
    public Product factoryMethod() {
        return new ConcreteProductA();
    }
}

// Concrete creator
class ConcreteCreatorB implements Creator {
    @Override
    public Product factoryMethod() {
        return new ConcreteProductB();
    }
}

public class Main {
    public static void main(String[] args) {
        Creator creatorA = new ConcreteCreatorA();
        Product productA = creatorA.factoryMethod();
        productA.create();

        Creator creatorB = new ConcreteCreatorB();
        Product productB = creatorB.factoryMethod();
        productB.create();
    }
}
```

#LowLevelDesign #DesignPattern #CreationalPatterns #FactoryMethodPattern #Example 