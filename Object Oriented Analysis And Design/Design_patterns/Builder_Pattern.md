# Builder Pattern

## Introduction

The Builder Pattern is a creational design pattern that provides a way to construct complex objects step by step. It allows you to produce different types and representations of an object using the same construction process. The Builder Pattern is particularly useful when creating an object that requires a lot of configurations or when an object consists of many parts that need to be assembled.

## Where to Use

Use the Builder Pattern in the following scenarios:

- When you need to construct an object that requires numerous parameters or complex configuration.
- When you want to create different representations of the same type of object.
- When the construction process must allow for different sequences or combinations of steps.
- When the creation of an object is complex and needs to be separated from its representation.

## Code Explanation

### Builder Pattern Implementation

#### Step 1: Define the Product

```java
// Product class
public class House {
    private String foundation;
    private String structure;
    private String roof;
    private boolean hasGarage;
    private boolean hasSwimmingPool;

    public void setFoundation(String foundation) {
        this.foundation = foundation;
    }

    public void setStructure(String structure) {
        this.structure = structure;
    }

    public void setRoof(String roof) {
        this.roof = roof;
    }

    public void setHasGarage(boolean hasGarage) {
        this.hasGarage = hasGarage;
    }

    public void setHasSwimmingPool(boolean hasSwimmingPool) {
        this.hasSwimmingPool = hasSwimmingPool;
    }

    @Override
    public String toString() {
        return "House [foundation=" + foundation + ", structure=" + structure + ", roof=" + roof 
                + ", hasGarage=" + hasGarage + ", hasSwimmingPool=" + hasSwimmingPool + "]";
    }
}


```

### Step 2:  Define the Builder Interface
```java
// Builder interface
public interface HouseBuilder {
    void buildFoundation();
    void buildStructure();
    void buildRoof();
    void buildGarage();
    void buildSwimmingPool();
    House getHouse();
}
```

#### Step 3: Implement Concrete Builders

```java
// Concrete Builder for a simple house
public class SimpleHouseBuilder implements HouseBuilder {
    private House house;

    public SimpleHouseBuilder() {
        this.house = new House();
    }

    @Override
    public void buildFoundation() {
        house.setFoundation("Concrete Foundation");
    }

    @Override
    public void buildStructure() {
        house.setStructure("Wooden Structure");
    }

    @Override
    public void buildRoof() {
        house.setRoof("Wooden Roof");
    }

    @Override
    public void buildGarage() {
        house.setHasGarage(false);
    }

    @Override
    public void buildSwimmingPool() {
        house.setHasSwimmingPool(false);
    }

    @Override
    public House getHouse() {
        return this.house;
    }
}

// Concrete Builder for a luxury house
public class LuxuryHouseBuilder implements HouseBuilder {
    private House house;

    public LuxuryHouseBuilder() {
        this.house = new House();
    }

    @Override
    public void buildFoundation() {
        house.setFoundation("Concrete and Steel Foundation");
    }

    @Override
    public void buildStructure() {
        house.setStructure("Steel Structure");
    }

    @Override
    public void buildRoof() {
        house.setRoof("Concrete Roof");
    }

    @Override
    public void buildGarage() {
        house.setHasGarage(true);
    }

    @Override
    public void buildSwimmingPool() {
        house.setHasSwimmingPool(true);
    }

    @Override
    public House getHouse() {
        return this.house;
    }
}

```

#### Step 4: Define the Director

```java
// Director class
public class ConstructionEngineer {
    private HouseBuilder houseBuilder;

    public ConstructionEngineer(HouseBuilder houseBuilder) {
        this.houseBuilder = houseBuilder;
    }

    public House constructHouse() {
        houseBuilder.buildFoundation();
        houseBuilder.buildStructure();
        houseBuilder.buildRoof();
        houseBuilder.buildGarage();
        houseBuilder.buildSwimmingPool();
        return houseBuilder.getHouse();
    }
}


```

#### Step 5: Client Code

```java
public class BuilderPatternExample {
    public static void main(String[] args) {
        // Build a simple house
        HouseBuilder simpleHouseBuilder = new SimpleHouseBuilder();
        ConstructionEngineer engineer1 = new ConstructionEngineer(simpleHouseBuilder);
        House simpleHouse = engineer1.constructHouse();
        System.out.println(simpleHouse);

        // Build a luxury house
        HouseBuilder luxuryHouseBuilder = new LuxuryHouseBuilder();
        ConstructionEngineer engineer2 = new ConstructionEngineer(luxuryHouseBuilder);
        House luxuryHouse = engineer2.constructHouse();
        System.out.println(luxuryHouse);
    }
}

```

## Real World Example

Consider building a computer with different configurations. Using the Builder Pattern, you can have different builders for assembling gaming computers, workstations, or budget PCs.


```java
// Product class
public class Computer {
    private String CPU;
    private String GPU;
    private String RAM;
    private String storage;
    private boolean hasLiquidCooling;
    private boolean hasWiFiCard;

    public void setCPU(String CPU) {
        this.CPU = CPU;
    }

    public void setGPU(String GPU) {
        this.GPU = GPU;
    }

    public void setRAM(String RAM) {
        this.RAM = RAM;
    }

    public void setStorage(String storage) {
        this.storage = storage;
    }

    public void setHasLiquidCooling(boolean hasLiquidCooling) {
        this.hasLiquidCooling = hasLiquidCooling;
    }

    public void setHasWiFiCard(boolean hasWiFiCard) {
        this.hasWiFiCard = hasWiFiCard;
    }

    @Override
    public String toString() {
        return "Computer [CPU=" + CPU + ", GPU=" + GPU + ", RAM=" + RAM 
                + ", storage=" + storage + ", hasLiquidCooling=" + hasLiquidCooling 
                + ", hasWiFiCard=" + hasWiFiCard + "]";
    }
}

// Builder interface
public interface ComputerBuilder {
    void buildCPU();
    void buildGPU();
    void buildRAM();
    void buildStorage();
    void buildCoolingSystem();
    void buildWiFiCard();
    Computer getComputer();
}

// Concrete Builder for Gaming Computer
public class GamingComputerBuilder implements ComputerBuilder {
    private Computer computer;

    public GamingComputerBuilder() {
        this.computer = new Computer();
    }

    @Override
    public void buildCPU() {
        computer.setCPU("High-end CPU");
    }

    @Override
    public void buildGPU() {
        computer.setGPU("High-end GPU");
    }

    @Override
    public void buildRAM() {
        computer.setRAM("16GB RAM");
    }

    @Override
    public void buildStorage() {
        computer.setStorage("1TB SSD");
    }

    @Override
    public void buildCoolingSystem() {
        computer.setHasLiquidCooling(true);
    }

    @Override
    public void buildWiFiCard() {
        computer.setHasWiFiCard(true);
    }

    @Override
    public Computer getComputer() {
        return this.computer;
    }
}

// Director class
public class ComputerEngineer {
    private ComputerBuilder computerBuilder;

    public ComputerEngineer(ComputerBuilder computerBuilder) {
        this.computerBuilder = computerBuilder;
    }

    public Computer constructComputer() {
        computerBuilder.buildCPU();
        computerBuilder.buildGPU();
        computerBuilder.buildRAM();
        computerBuilder.buildStorage();
        computerBuilder.buildCoolingSystem();
        computerBuilder.buildWiFiCard();
        return computerBuilder.getComputer();
    }
}

// Client code
public class ComputerStore {
    public static void main(String[] args) {
        // Build a gaming computer
        ComputerBuilder gamingComputerBuilder = new GamingComputerBuilder();
        ComputerEngineer engineer = new ComputerEngineer(gamingComputerBuilder);
        Computer gamingComputer = engineer.constructComputer();
        System.out.println(gamingComputer);

        // Other computer configurations can be built similarly
    }
}

```