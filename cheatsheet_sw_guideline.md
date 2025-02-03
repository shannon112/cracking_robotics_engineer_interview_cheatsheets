# YAGNI, DRY, KISS, TDA
```c++
YAGNI: Avoid unneeded features. // 簡單 乾淨 clean
KISS: Simpler is better. // 簡單 乾淨 clean`
DRY: Centralize functionality. // 別重複 抽出來變utils可reuse  
TDA: Let objects act, not expose. Encapsulation. // 對外簡單一個run or exe, 別把一整串pipeline的function分開來讓user在外面call
```

- **YAGNI (You Aren’t Gonna Need It)**  
  - **Definition**: Only implement features when you absolutely need them, not based on assumptions about future requirements.  
  - **Advantage**: Reduces **waste**, improves **focus**, and enhances **agility** by preventing over-engineering.  
  - **Example**: Avoid adding a complex caching mechanism in an app until profiling shows it is necessary to optimize performance.
  - <img src="https://github.com/user-attachments/assets/53eeb1e2-0212-40ea-8ff4-40c1b4340a15" width=400/>
- **DRY (Don’t Repeat Yourself)**  
  - **Definition**: Avoid duplication of logic by centralizing code that has a single, clear purpose.  
  - **Advantage**: Improves **maintainability**, reduces **errors**, and ensures **consistency** across the codebase.  
  - **Example**: A utility function is reused across different modules instead of duplicating the same logic in each module.
  - <img src="https://github.com/user-attachments/assets/4c517e3f-5f46-4742-be48-bc8e817d2664" width=400/>
- **KISS (Keep It Simple, Stupid)**  
  - **Definition**: Design as simply as possible, avoiding unnecessary complexity. Simple is easier to understand, maintain, and debug.  
  - **Advantage**: Enhances **readability**, **scalability**, and **ease of debugging** while reducing risks of hidden bugs.  
  - **Example**: Prefer a straightforward `for` loop over a highly complex recursive algorithm when both achieve the same result.
- **TDA (Tell, Don’t Ask)**  
  - **Definition**: Objects should perform tasks using their internal state without exposing details unnecessarily. Focus on **delegating responsibilities** to objects instead of querying and acting externally.  
  - **Advantage**: Improves **encapsulation**, reduces **coupling**, and encourages **object-oriented thinking**.  
  - **Example**: Instead of querying a `Cart` object for items and computing the total externally, the `Cart` class should provide a `calculateTotal()` method to handle the logic internally.

# OOP 4 Characteristics
```
封裝（Encapsulation)
繼承（Inheritance)
多型（Polymorphism) 
抽象 (Abstraction)
```

- **Summary (Key Takeaways)**:  
  - **Encapsulation**: Protect and bundle. **Security.**  `包起來 有層級 有權限 安全`
  - **Inheritance**: Reuse and extend. **Code reuse.** `繼承 同名 且 相同的功能 重複使用`
  - **Polymorphism**: One interface, multiple implementations. **Flexibility.** `多型 同名 但 特化的功能 彈性擴展`
  - **Abstraction**: Focus on what, not how. **Simplicity.** `對外簡單一個run or exe`

- **Encapsulation**  
  - **Definition**: Encapsulation bundles data (fields) and methods (functions) into a single unit (class) and restricts direct access to internal data using access modifiers (`private`, `protected`, `public`).  
  - **Advantage**: Improves **security**, **modularity**, and **maintainability** by controlling access and isolating functionality.  
  - **Example**: A `BankAccount` class exposes only methods like `deposit()` or `withdraw()` while keeping the `balance` field private to prevent unauthorized modifications.

- **Inheritance**  
  - **Definition**: Enables a new class (child) to acquire properties and behaviors of an existing class (parent), creating a hierarchy.  
  - **Advantage**: Promotes **reusability**, **extendability**, and easier **hierarchical organization**.  
  - **Example**: A `Vehicle` base class is inherited by `Car` and `Bike`, reusing common attributes like `speed` and methods like `start()`.

- **Polymorphism**  
  - **Definition**: Allows entities like methods or objects to behave in multiple ways. Achieved via method overriding (runtime polymorphism) and method overloading (compile-time polymorphism).  
  - **Advantage**: Improves **flexibility**, **scalability**, and **readability** by handling different use cases with a uniform interface.  
  - **Example**: A `Shape` class has a `draw()` method. Subclasses like `Circle` and `Square` override `draw()` to provide specific implementations.

- **Abstraction**  
  - **Definition**: Hides complex implementation details while exposing only the necessary functionalities through abstract classes or interfaces.  
  - **Advantage**: Enhances **simplicity**, **focus**, and **interoperability** by reducing complexity and providing a clean interface.  
  - **Example**: A `Payment` interface declares methods like `processPayment()` without specifying how the payment is processed, leaving the implementation to concrete classes like `CreditCardPayment` or `PayPalPayment`.


# OOP SOLID 5 Princples 
```
SRP — Single Responsibility Principle
OCP — Open Closed Principle
LSP — Liskov Substitution Principle
ISP — Interface Segregation Principle
DIP — Dependency Inversion Principle
```
```c++
SRP: One job per class. **Focus.** // 一個Func做一件事
OCP: Add, don’t change. **Scalability.** // 別動Base 但可以疊Derived
LSP: Subtypes replace base types. **Consistency.** // 別亂繼承Parent 需要是合理的Child 實作parent的func才有意義
ISP: Use only what’s needed. **Efficiency.**  // 別繼承一Parent大堆功能 但用到的少 要精簡 拆開
DIP: Depend on abstractions. **Flexibility.** // 去依靠interface 別往往Base靠
```

- **SRP — Single Responsibility Principle**
  - **Definition**: A class should have only one reason to change, meaning it should only perform one responsibility.
  - **Advantage**: Improves **maintainability** and reduces coupling. Each responsibility is isolated, making it easier to debug and extend.
  - **Example**: A `Logger` class handles logging, and a `FileHandler` class manages file operations, avoiding mixing responsibilities.
- **OCP — Open/Closed Principle**
  - **Definition**: Software entities (classes, modules, functions) should be **open for extension** but **closed for modification**.
  - **Advantage**: Promotes **scalability** by allowing new features to be added without altering existing code, reducing the risk of bugs.
  - **Example**: Using a base `Shape`, and extending it with `Circle` or `Rectangle` classes rather than modifying the base class.
- **LSP — Liskov Substitution Principle**
  - **Definition**: Subtypes must be substitutable for their base types without altering the correctness of the program.
  - **Advantage**: Ensures **consistency** and prevents unexpected behavior, promoting robustness.
  - **Example**: `Bird` base class with a `fly()` method shouldn't be extended by a `Penguin` class unless it's overridden meaningfully.
  - ![圖片](https://github.com/user-attachments/assets/48244641-29ca-44cf-8c20-82663297e7eb)
- **ISP — Interface Segregation Principle**
  - **Definition**: A class should not be forced to implement interfaces it does not use. Instead, prefer smaller, specific interfaces.
  - **Advantage**: Reduces **bloat** and improves **flexibility** by focusing on what a class truly needs.
  - **Example**: Splitting an interface into smaller ones like `Printer` and `Scanner` ensures a device only impl the required feature.
  - ![圖片](https://github.com/user-attachments/assets/184e0e54-b376-45dc-bc06-fe52ec3b86e3)
- **DIP — Dependency Inversion Principle**
  - **Definition**: High-level shouldn't depend on low-level. Both should depend on abstractions which shouldn't depend on details.
  - **Advantage**: Encourages **decoupling** and flexibility, making the system more adaptable to changes.
  - **Example**: Instead of a `PaymentProcessor` class directly depending on a `PayPalService` class, it depends on a `PaymentService` interface, allowing different payment services to be used interchangeably.
  - ![圖片](https://github.com/user-attachments/assets/6c2c1b3c-6d53-46d6-ab25-d6ea7452137a)
