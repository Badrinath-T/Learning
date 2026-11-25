# Design Patterns: Overview

## Why group patterns into categories?

Design patterns can look like nothing more than classes and interfaces. The grouping is not arbitrary. Each category is based on the main concern the pattern addresses.

| Category | Concern | Core question | Key idea |
|---|---|---|---|
| Creational | Object creation | Who creates the object, and how? | Encapsulate instantiation logic |
| Structural | Object composition | How do objects fit together into larger structures? | Encapsulate relationships (whole-part, wrappers, bridges) |
| Behavioral | Object interaction | Who does what, and how do they communicate? | Encapsulate interaction and responsibility distribution |

All three categories use the same tools (classes and interfaces). They differ in the design problem they solve.

## 1. Creational: object creation

Avoid hard-coding `new` everywhere. Ask: should the object be created directly, or through a factory, builder, or singleton?

- **Factory Method**: delegates object creation to subclasses.
- **Abstract Factory**: creates families of related objects.
- **Builder**: constructs an object step by step.
- **Singleton**: allows only one instance.

## 2. Structural: object composition

Combine classes and objects into larger structures without tight coupling. Ask: how do I glue objects together without making them tightly coupled?

- **Adapter**: converts one interface into another.
- **Decorator**: adds behavior dynamically by wrapping, without inheritance.
- **Composite**: treats tree-shaped hierarchies uniformly.
- **Proxy**: a placeholder that controls access to another object.

## 3. Behavioral: object interaction

Define how objects communicate and how responsibilities are distributed. Ask: who does what, and how do they talk to each other?

- **Observer**: notifies dependents when state changes.
- **Strategy**: swaps algorithms at runtime.
- **Command**: encapsulates a request as an object.
- **Chain of Responsibility**: passes a request along a chain of handlers.

## Analogy

- **Creational** is how you hire: recruiters, contractors, HR rules.
- **Structural** is how you organize: teams, departments, reporting lines. These patterns design the static architecture of the object graph.
- **Behavioral** is how people work together: processes, meetings, communication. These patterns design the dynamic flow of messages between objects.
