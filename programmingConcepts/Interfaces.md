What is an Interface in Programming?

An Interface is a fundamental concept in object-oriented programming (OOP) that defines a contract or
specification for classes without implementing the actual behavior. It specifies what a class should do,
but not how it should do it.

Key Characteristics

1. Contract Definition: An interface defines a set of methods, properties, events, or indexers that
implementing classes must provide
2. No Implementation: Interfaces contain only declarations, no implementation code
3. Multiple Inheritance: A class can implement multiple interfaces (unlike single inheritance with
classes)
4. Polymorphism: Enables different classes to be used interchangeably through a common interface

Basic Syntax Examples

### Java

```java
  // Define interface
  interface Animal {
      void makeSound();
      void move();
  }

  // Implement interface
  class Dog implements Animal {
      public void makeSound() {
          System.out.println("Woof!");
      }

      public void move() {
          System.out.println("Running on four legs");
      }
  }
```

### C#

```csharp
  // Define interface
  public interface IShape {
      double CalculateArea();
      double CalculatePerimeter();
  }

  // Implement interface
  public class Circle : IShape {
      private double radius;

      public double CalculateArea() {
          return Math.PI * radius * radius;
      }

      public double CalculatePerimeter() {
          return 2 * Math.PI * radius;
      }
  }
```

### TypeScript

```typescript
  // Define interface
  interface Vehicle {
      start(): void;
      stop(): void;
      speed: number;
  }

  // Implement interface
  class Car implements Vehicle {
      speed: number = 0;

      start(): void {
          console.log("Car started");
      }

      stop(): void {
          console.log("Car stopped");
      }
  }
```

Types of Interfaces

### 1. Marker/Tag Interfaces

Interfaces with no methods (used for marking classes):

```java
  interface Serializable { } // Marker interface
```

### 2. Functional Interfaces (Single Abstract Method)

Interfaces with exactly one abstract method:

```java
  @FunctionalInterface
  interface Calculator {
      int calculate(int a, int b);
  }
```

### 3. Default Methods (Java 8+)

Interfaces can have default implementations:

```java
  interface Logger {
      void log(String message);

      default void logError(String error) {
          log("ERROR: " + error);
      }
  }
```

### 4. Property Interfaces

Define properties without implementation:

```typescript
  interface Person {
      name: string;
      age: number;
      readonly id: number; // Read-only property
  }
```

Why Use Interfaces?

### 1. Abstraction

Hide implementation details while exposing functionality:

```java
  interface Database {
      void connect();
      void query(String sql);
      void disconnect();
  }

  class MySQLDatabase implements Database { /* implementation */ }
  class PostgreSQLDatabase implements Database { /* implementation */ }
```

### 2. Loose Coupling

Reduce dependencies between components:

```java
  interface PaymentProcessor {
      boolean processPayment(double amount);
  }

  class ShoppingCart {
      private PaymentProcessor processor;

      public ShoppingCart(PaymentProcessor processor) {
          this.processor = processor; // Dependency injection
      }

      public void checkout(double total) {
          if (processor.processPayment(total)) {
              // Success
          }
      }
  }
```

### 3. Polymorphism

Treat different objects uniformly:

```java
  interface Drawable {
      void draw();
  }

  class Circle implements Drawable { /* draws circle */ }
  class Square implements Drawable { /* draws square */ }
  class Triangle implements Drawable { /* draws triangle */ }

  // Can store all in same collection
  List<Drawable> shapes = new ArrayList<>();
  shapes.add(new Circle());
  shapes.add(new Square());
  shapes.add(new Triangle());

  // All can be drawn the same way
  for (Drawable shape : shapes) {
      shape.draw();
  }
```

### 4. Testing (Mocking)

Easy to create test doubles:

```java
  interface EmailService {
      void sendEmail(String to, String subject, String body);
  }

  // Real implementation
  class SMTPEmailService implements EmailService {
      public void sendEmail(String to, String subject, String body) {
          // Connect to SMTP server and send
      }
  }

  // Mock for testing
  class MockEmailService implements EmailService {
      public void sendEmail(String to, String subject, String body) {
          // Just record that email would be sent
          System.out.println("Mock: Email would be sent to " + to);
      }
  }
```

Interface vs Abstract Class

| Aspect               | Interface                                 | Abstract Class                              |
|----------------------|-------------------------------------------|---------------------------------------------|
| Implementation       | No implementation (only declarations)     | Can have both abstract and concrete methods |
| Multiple Inheritance | A class can implement multiple interfaces | A class can extend only one abstract class  |
| Fields               | Can only have constants (static           | Can have instance variables                 |
| Constructor          | No constructors                           | Can have constructors                       |
| Access Modifiers     | Methods are public by default             | Can have various access modifiers           |
| State                | Stateless (no instance variables)         | Can maintain state                          |



Real-World Example: Plugin Architecture

```java
  // Plugin interface
  interface Plugin {
      String getName();
      void initialize();
      void execute();
      void cleanup();
  }

  // Different plugins implementing same interface
  class LoggerPlugin implements Plugin {
      public String getName() { return "Logger"; }
      public void initialize() { /* setup logging */ }
      public void execute() { /* log messages */ }
      public void cleanup() { /* close log files */ }
  }

  class AnalyticsPlugin implements Plugin {
      public String getName() { return "Analytics"; }
      public void initialize() { /* connect to analytics service */ }
      public void execute() { /* track events */ }
      public void cleanup() { /* flush data */ }
  }

  // Plugin manager that works with any Plugin
  class PluginManager {
      private List<Plugin> plugins = new ArrayList<>();

      public void registerPlugin(Plugin plugin) {
          plugins.add(plugin);
      }

      public void runAll() {
          for (Plugin plugin : plugins) {
              plugin.initialize();
              plugin.execute();
              plugin.cleanup();
          }
      }
  }
```

Best Practices

1. Name Interfaces Clearly: Use adjectives (e.g., Comparable, Runnable) or nouns with "I" prefix (e.g.,
IShape, IDatabase)
2. Keep Interfaces Focused: Follow Interface Segregation Principle - many client-specific interfaces are
better than one general-purpose interface
3. Program to Interfaces: Depend on abstractions (interfaces) rather than concrete implementations
4. Use for Cross-Cutting Concerns: Define interfaces for logging, caching, validation, etc.

Modern Variations

### Traits/Mixins (in languages like PHP, Scala, Rust)

Similar to interfaces but can include implementation:

```php
  trait Loggable {
      public function log($message) {
          echo date('Y-m-d H:i:s') . ": $message\n";
      }
  }

  class User {
      use Loggable; // Mix in the trait
  }
```

### Protocols (in Swift)

```swift
  protocol Vehicle {
      var speed: Double { get set }
      func start()
      func stop()
  }
```

### Duck Typing (in Python, Ruby)

"If it walks like a duck and quacks like a duck, it's a duck" - no explicit interface declaration
needed:

```python
  # No explicit interface, just expected methods
  def process_vehicle(vehicle):
      vehicle.start()
      vehicle.accelerate(50)
      vehicle.stop()
```

In summary, an interface is a powerful abstraction mechanism that enables:
- Defining clear contracts between components
- Achieving loose coupling and high cohesion
- Enabling polymorphism and code reuse
- Facilitating testing and maintainability
- Supporting design patterns like Strategy, Adapter, and Factory

Interfaces are essential for building scalable, maintainable, and testable software systems.
