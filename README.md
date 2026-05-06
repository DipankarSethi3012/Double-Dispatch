# Double Dispatch

A Java implementation demonstrating the **Double Dispatch** design pattern, a behavioral pattern that enables operations on complex object structures while maintaining clean separation of concerns.

## 📖 Overview

Double Dispatch is a technique used to invoke overloaded methods based on the runtime types of two objects. This pattern is particularly useful when you need to perform operations that depend on the types of multiple objects, such as simulating interactions between different game entities or handling operations on various data structures.

The pattern works by leveraging Java's method overloading combined with polymorphism to achieve dynamic dispatch based on two object types rather than just one.

## 🎯 What is Double Dispatch?

In traditional method overloading, Java determines which method to call based on the compile-time type of the object. With Double Dispatch, we can determine method behavior based on the runtime types of **two** objects.

### Key Concepts:
- **First Dispatch**: Calling a method on the first object (polymorphism)
- **Second Dispatch**: That method calls another method on the second object, passing itself as an argument (using `this`)

## 💡 Use Cases

- **Game Engines**: Handling collisions between different entity types
- **Graphics Rendering**: Operating on different shape types
- **Type-Based Operations**: Performing actions that depend on multiple object types
- **Visitor Pattern**: Implementing flexible visitors for complex object hierarchies
- **Multiple Dispatch Simulation**: Simulating languages with native multiple dispatch support

## 🏗️ Project Structure

```
Double-Dispatch/
├── DoubleDispatchDemo.java    # Main demonstration file
└── README.md                   # This file
```

## 🚀 Getting Started

### Prerequisites
- Java 8 or higher
- A Java IDE (IntelliJ IDEA, Eclipse, VS Code) or command line

### Compilation

```bash
javac DoubleDispatchDemo.java
```

### Execution

```bash
java DoubleDispatchDemo
```

## 📝 Example Implementation

A typical Double Dispatch scenario might involve:

```java
// Base entity interface
interface Entity {
    void interact(Entity other);
}

// Different entity types
class Player implements Entity {
    @Override
    public void interact(Entity other) {
        other.acceptInteraction(this);
    }
    
    public void acceptInteraction(Monster monster) {
        // Handle player-monster interaction
    }
}

class Monster implements Entity {
    @Override
    public void interact(Entity other) {
        other.acceptInteraction(this);
    }
    
    public void acceptInteraction(Player player) {
        // Handle monster-player interaction
    }
}
```

## ��� How It Works

1. Call `entity1.interact(entity2)` - First dispatch based on entity1's type
2. Inside the method, call `entity2.acceptInteraction(this)` - Second dispatch based on entity2's type
3. The correct method handles the specific type combination

## 📚 Benefits

✅ **Clean Code**: Avoids massive if-else chains for type checking  
✅ **Maintainability**: Easy to add new types and interactions  
✅ **Extensibility**: Follows the Open/Closed Principle  
✅ **Type Safety**: Uses compile-time type checking  

## ⚠️ When NOT to Use

- Simple one-type operations (just use regular polymorphism)
- When performance is critical (slight overhead from method calls)
- For only 1-2 type combinations (if-else might be simpler)

## 🔗 Related Patterns

- **Visitor Pattern**: Similar concept, often used together
- **Strategy Pattern**: For encapsulating behaviors
- **Factory Pattern**: Often used to create entities

## 📖 References

- [Design Patterns: Elements of Reusable Object-Oriented Software](https://en.wikipedia.org/wiki/Design_Patterns) by Gang of Four
- [Java Design Patterns](https://www.digitalocean.com/community/tutorials/design-pattern-in-java)
- [Double Dispatch Wikipedia](https://en.wikipedia.org/wiki/Double_dispatch)

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

## 👨‍💻 Author

**Dipankar Sethi** - [@DipankarSethi3012](https://github.com/DipankarSethi3012)

## 🤝 Contributing

Contributions are welcome! Feel free to:
- Fork the repository
- Create a feature branch
- Submit pull requests
- Report issues

## 📧 Contact

For questions or suggestions, feel free to reach out via GitHub issues or contact the repository owner.

---

**Last Updated**: May 6, 2026
