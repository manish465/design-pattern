- The Builder Pattern is a creational design pattern that is used to construct a complex object step by step.
- It separates the construction of a complex object from its representation, allowing the same construction process to create different representations.
- This pattern is particularly useful when an object has a large number of optional properties or configurations, and you want to create instances of the object with specific combinations of those properties.
- Key components of the Builder Pattern:
	- **Builder Interface**:
		- This is an interface that defines the methods for constructing the parts of the complex object.
		- These methods are typically named after the properties or configurations that need to be set.
	- **Concrete Builders**:
		- Concrete builder classes implement the builder interface and provide specific implementations for constructing the complex object.
		- Each concrete builder is responsible for setting values for the object's properties.
	- **Product**:
		- The product is the complex object being constructed.
		- It often has multiple properties, some of which may be optional.
	- **Director (optional)**:
		- In some implementations of the Builder Pattern, a director class may be used to coordinate the construction process using a specific sequence of builder methods.
		- This is particularly useful when there are multiple ways to construct the same complex object.

```
// Product: Computer
class Computer {
    private String processor;
    private int memory;
    private int storage;
    private String graphicsCard;
    private String operatingSystem;

    public Computer(String processor, int memory, int storage, String graphicsCard, String operatingSystem) {
        this.processor = processor;
        this.memory = memory;
        this.storage = storage;
        this.graphicsCard = graphicsCard;
        this.operatingSystem = operatingSystem;
    }

    public void display() {
        System.out.println("Processor: " + processor);
        System.out.println("Memory: " + memory + " GB");
        System.out.println("Storage: " + storage + " GB SSD");
        System.out.println("Graphics Card: " + graphicsCard);
        System.out.println("Operating System: " + operatingSystem);
    }
}

// Builder Interface
interface ComputerBuilder {
    ComputerBuilder setProcessor(String processor);
    ComputerBuilder setMemory(int memory);
    ComputerBuilder setStorage(int storage);
    ComputerBuilder setGraphicsCard(String graphicsCard);
    ComputerBuilder setOperatingSystem(String operatingSystem);
    Computer build();
}

// Concrete Builder
class HighEndComputerBuilder implements ComputerBuilder {
    private String processor;
    private int memory;
    private int storage;
    private String graphicsCard;
    private String operatingSystem;

    @Override
    public ComputerBuilder setProcessor(String processor) {
        this.processor = processor;
        return this;
    }

    @Override
    public ComputerBuilder setMemory(int memory) {
        this.memory = memory;
        return this;
    }

    @Override
    public ComputerBuilder setStorage(int storage) {
        this.storage = storage;
        return this;
    }

    @Override
    public ComputerBuilder setGraphicsCard(String graphicsCard) {
        this.graphicsCard = graphicsCard;
        return this;
    }

    @Override
    public ComputerBuilder setOperatingSystem(String operatingSystem) {
        this.operatingSystem = operatingSystem;
        return this;
    }

    @Override
    public Computer build() {
        return new Computer(processor, memory, storage, graphicsCard, operatingSystem);
    }
}

// Client code
public class Main {
    public static void main(String[] args) {
        ComputerBuilder highEndBuilder = new HighEndComputerBuilder();

        Computer highEndComputer = highEndBuilder
                .setProcessor("Intel Core i9")
                .setMemory(32)
                .setStorage(1000)
                .setGraphicsCard("NVIDIA RTX 3080")
                .setOperatingSystem("Windows 10")
                .build();

        System.out.println("High-End Computer:");
        highEndComputer.display();
    }
}
```

#LowLevelDesign #DesignPattern #CreationalPatterns #BuilderPattern #Example 