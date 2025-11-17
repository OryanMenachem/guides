SOLID Principles - Summary

---

# SOLID Principles in Short

## S – Single Responsibility Principle (SRP)

- **Definition:** Each class should have one, and only one, reason to change.
- **Benefit:** Easier to understand, maintain, and test.
- **Example:** Separate `Invoice` (calculates total) from `InvoicePrinter` (prints invoice).

## O – Open/Closed Principle (OCP)

- **Definition:** Software entities should be open for extension but closed for modification.
- **Benefit:** Add new functionality without changing existing code.
- **Example:** Add new discount types implementing a `Discount` interface without changing current logic.

## L – Liskov Substitution Principle (LSP)

- **Definition:** Subtypes must be substitutable for their base types.
- **Benefit:** Avoids broken code and unexpected behavior.
- **Example:** A `Sparrow` class can replace `Bird` without issues; `Penguin` cannot if `Bird` requires flying.

## I – Interface Segregation Principle (ISP)

- **Definition:** Many client-specific interfaces are better than one general-purpose interface.
- **Benefit:** Classes implement only what they need, reducing unnecessary dependencies.
- **Example:** `Human` implements `Workable` and `Eatable`; `Robot` implements only `Workable`.

## D – Dependency Inversion Principle (DIP)

- **Definition:** Depend on abstractions, not on concretions.
- **Benefit:** Increases flexibility, easier to swap implementations, facilitates testing.
- **Example:** `App` depends on `IDatabase` interface instead of directly creating `MySQLDatabase`.

---

# SOLID Questions and Answers

**1. What is the main goal of SOLID principles?**

- Make code flexible, readable, maintainable, and testable by properly dividing responsibilities and reducing dependencies.

**2. Why is it important that each class has only one responsibility (SRP)?**

- Easier to understand, change, and test. Multiple responsibilities lead to fragile, tightly coupled code.

\*\*3. What does 'open for extension, closed for modification' (OCP) mean? Give a short example.

- You can add new functionality without modifying existing code, e.g., adding new discount types.

\*\*4. How to implement OCP effectively in TypeScript?

- Use interfaces or abstract classes; new classes implement or extend existing abstractions.

\*\*5. What happens if a subclass does not behave like its parent (LSP)?

- The code expecting the parent may break or behave unexpectedly, e.g., `Penguin` cannot fly but inherits `Bird`.

\*\*6. How does ISP help keep code flexible and maintainable?

- Classes implement only what they need, reducing unnecessary methods and dependencies.

\*\*7. Difference between ISP and SRP?

- SRP: focuses on class responsibility. ISP: focuses on interface granularity and relevance to implementing classes.

\*\*8. Why depend on abstractions, not implementations (DIP)?

- Makes code flexible, allows swapping implementations, easier unit testing with mocks.

\*\*9. Real project case where violating DIP makes testing hard?

- Class `UserService` creates `new MySQLDatabase()` internally, cannot test without real DB. Solution: inject interface.

\*\*10. In a system with many direct dependencies, which SOLID principles help most?

- Dependency Inversion: reduce direct dependency on concrete classes.
- Interface Segregation: break large interfaces into smaller, relevant ones.
