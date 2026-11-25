# Design Patterns: Details

Each pattern below has three parts: the **problem** it solves, **why it belongs in its category**, and **how it solves the problem**.

The category rule is simple. Each group is defined by the main thing its patterns deal with:

- **Creational:** how objects are created.
- **Structural:** how classes and objects are composed into larger structures.
- **Behavioral:** how objects communicate and divide responsibilities.

## Creational: how objects get created

These patterns hide or control the `new` step, so the rest of the code doesn't depend on concrete classes.

### Factory Method

- **Problem:** Callers need an object but should not decide its concrete class.
- **Why Creational:** Its whole purpose is to change which class gets instantiated, so it is about creation.
- **How it solves it:** A creator method returns a product through an interface, and subclasses override it to choose the concrete type.

### Abstract Factory

- **Problem:** Related objects must match each other, such as a Dark theme's button, checkbox, and window.
- **Why Creational:** It creates families of objects, and the point is which concrete objects get created together.
- **How it solves it:** One factory interface creates each product in a family, so swapping the factory swaps the whole family consistently.

### Builder

- **Problem:** Objects with many optional fields lead to constructors with long, confusing parameter lists.
- **Why Creational:** It is a step-by-step construction process for one object. The goal is to control how the object is assembled.
- **How it solves it:** Fields are set through methods one step at a time, and `build()` returns the finished object.

### Singleton

- **Problem:** Some resources, such as a config or connection pool, should exist only once.
- **Why Creational:** It controls how many instances can be created, which is a creation rule.
- **How it solves it:** The constructor is private, and a static accessor always returns the same instance. Caveat: this is effectively global state, which makes testing harder.

## Structural: how objects fit together

These patterns arrange classes and objects into larger structures. The question is how the parts connect, not how they are made or how they behave over time.

### Adapter

- **Problem:** A library's interface does not match what your code expects.
- **Why Structural:** It joins two existing interfaces together so they can work as one structure.
- **How it solves it:** A wrapper implements the interface your code expects and translates each call to the library's API.

### Decorator

- **Problem:** Adding features through subclasses explodes into too many combinations, such as coffee with milk, sugar, or both.
- **Why Structural:** It composes objects by wrapping them in layers that share one interface.
- **How it solves it:** Each wrapper adds its behavior and delegates to the object it wraps, so features stack at runtime.

### Composite

- **Problem:** You need to treat a single item and a group of items the same way, such as files and folders.
- **Why Structural:** It builds a tree of objects, which is a structural shape.
- **How it solves it:** Leaves and groups share one interface, and a group forwards the operation to its children recursively.

### Facade

- **Problem:** A subsystem has many classes, and callers must know how they work together.
- **Why Structural:** It organizes a group of classes behind one simpler structure.
- **How it solves it:** One class offers a few simple methods and coordinates the subsystem behind them.

### Proxy

- **Problem:** You need to control access to an object, for example to load it lazily, check permissions, or cache results.
- **Why Structural:** The proxy sits in the object structure, standing in place of the real object with the same interface.
- **How it solves it:** The proxy decides when or whether to forward calls, and adds the control logic.

### Bridge

- **Problem:** Two dimensions of variation multiply into a class explosion, such as shapes × colors or remotes × devices.
- **Why Structural:** It splits one class hierarchy into two linked hierarchies, which is a structural decision.
- **How it solves it:** The abstraction holds a reference to an implementation interface, so each side can change independently.

### Flyweight

- **Problem:** A program creates a huge number of near-identical objects, such as characters in a document, and runs out of memory.
- **Why Structural:** It changes how objects are structured in memory by separating shared parts from per-instance parts.
- **How it solves it:** Shared state lives in reusable objects, and per-instance state is passed in at call time.

## Behavioral: how objects communicate and share work

These patterns define how objects interact, which one does a job, and how control flows between them.

### Strategy

- **Problem:** One task has several algorithms, such as sorting methods or payment options, and the choice changes at runtime.
- **Why Behavioral:** It decides which algorithm runs, which is a question of behavior.
- **How it solves it:** Each algorithm implements a shared interface, and the context holds whichever one is selected.

### Observer

- **Problem:** When one object changes, many others must react, and the publisher should not need to know who they are.
- **Why Behavioral:** It defines how objects notify each other of events.
- **How it solves it:** The subject keeps a list of subscribers and notifies each one when its state changes.

### Command

- **Problem:** You need undo, redo, queuing, or logging of actions.
- **Why Behavioral:** It turns an action into an object, so the action itself can be passed around and executed later.
- **How it solves it:** Each request becomes an object with `execute()` (and optionally `undo()`), which can be stored and replayed.

### State

- **Problem:** An object's behavior depends on its current status, such as an order that is pending, shipped, or delivered, and the code fills up with `if` checks.
- **Why Behavioral:** It changes how the object behaves over time, based on what state it is in.
- **How it solves it:** Each state is its own class with its own behavior, and the object switches states. This differs from Strategy because states control their own transitions.

### Iterator

- **Problem:** Callers need to walk through a collection without knowing how it is stored.
- **Why Behavioral:** It defines how traversal happens, which is about how objects interact with a collection.
- **How it solves it:** A separate iterator object exposes `hasNext()` and `next()`, hiding the internal structure.

### Mediator

- **Problem:** Many objects talk to each other directly, creating tangled dependencies.
- **Why Behavioral:** It defines how objects communicate, moving that communication into one place.
- **How it solves it:** Objects send messages through a central mediator, so each one only knows the mediator.

### Chain of Responsibility

- **Problem:** A request must pass through several checks or handlers, such as middleware, approval levels, or logging.
- **Why Behavioral:** It defines how a request flows and who handles it.
- **How it solves it:** Each handler either handles the request or passes it to the next handler in the chain.

### Template Method

- **Problem:** Several processes share the same steps, but a few steps differ, such as exporting data to CSV or JSON.
- **Why Behavioral:** It fixes the order of an algorithm and lets subclasses change specific steps, which is about how behavior is divided.
- **How it solves it:** The base class defines the full sequence of steps, and subclasses override only the varying ones.

### Visitor

- **Problem:** You need to add new operations over a stable set of classes, such as an expression tree that must support printing and type checking, without editing every class.
- **Why Behavioral:** It moves operations out of the classes into visitor objects, so the behavior is defined separately from the data.
- **How it solves it:** Each element accepts a visitor and calls the visitor method for its own type, so new operations live in new visitor classes.

### Memento

- **Problem:** You need to save and restore an object's state, such as for undo, without exposing its internals.
- **Why Behavioral:** It captures and restores behavior-related state over time, supporting undo and history.
- **How it solves it:** The object creates a snapshot (memento), a separate caretaker stores it, and the object can later restore itself from it.
