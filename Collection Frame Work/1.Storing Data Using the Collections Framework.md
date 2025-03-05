# Introducing the Collections Framework

The Collections Framework is the most widely used API of the JDK. Whatever the application you are working on is, odds are that you will need to store and process data in memory at some point.

## History

The history of data structures goes back nearly as far back as computing itself. The Collections Framework is an implementation of the concepts on how to store, organize, and access data in memory that were developed long before the invention of Java. The Collections Framework does this in a very efficient way.

The Collections Framework was first introduced in **Java SE 2 (1998)** and has been rewritten twice since then:

- **Java SE 5** – Added **generics**.
- **Java SE 8** – Introduced **lambda expressions** and **default methods in interfaces**.

These are the most significant updates, but almost every JDK version includes changes to the Collections Framework.

## Key Concepts

You will learn about the most useful **data structures** in the Collections Framework and the **patterns** for manipulating them in your application.

### Structure of the Collections Framework

1. **Interfaces** – Define different ways of storing data in containers.
2. **Implementations** – Each interface has at least one concrete implementation.
3. **Choosing the Right Implementation** – The best choice depends on how you need to store and manipulate data.

By understanding these implementations, you can make efficient use of the Collections Framework in your applications.

# Finding Your Way in the Collections Framework

The Collections Framework contains many interfaces and classes, which can be overwhelming at first. However, some structures are used much more frequently than others.

## Key Concepts

- **Commonly Used Structures**: `List`, `ArrayList`, `Map`, etc.
- **Understanding the Big Picture**: The framework consists of interfaces and implementations.
- **Choosing the Right Interface**:
    - Storing and iterating over objects?
    - Using a queue for FIFO operations?
    - Retrieving objects via keys?
    - Accessing elements by index?
    - Sorting elements?
    - Avoiding duplicates or `null` values?

- **Choosing the Right Implementation**:
    - Will access be iterative or random?
    - Will objects remain mostly unchanged?
    - Is performance critical for lookups?
    - Will the structure be accessed concurrently?

## Categories in the Collections Framework

1. **Collections**: Store objects and allow iteration.
    - Root Interface: `Collection`
    - Extends: `Iterable` (not part of the Collections Framework)

2. **Maps**: Store key-value pairs.
    - Root Interface: `Map`
    - No direct relation to `Collection`.

3. **Queues & Stacks**: Model FIFO (First-In-First-Out) and LIFO (Last-In-First-Out) operations.
    - Part of the `Collection` hierarchy.

4. **Iterators**: Objects that iterate over collections.
    - Essential for traversing elements.

## Summary

The Collections Framework provides solutions for different storage and retrieval needs. The main categories are:

- **Collection** (storing & iterating)
- **Map** (key-value storage)
- **Queue** (FIFO operations)
- **Iterator** (traversing elements)

Understanding these structures will help you efficiently manage data in Java applications.
