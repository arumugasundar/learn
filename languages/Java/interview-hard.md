
# Interview - Hard

### Questions
1. [What are the key differences between ConcurrentHashMap and SynchronizedMap?](#1-what-are-the-key-differences-between-concurrenthashmap-and-synchronizedmap)
2. [Explain Java’s memory model (JMM). How does it impact multi-threading?](#2-explain-javas-memory-model-jmm-how-does-it-impact-multi-threading)
3. [What is a class loader in Java, and how does it work?](#3-what-is-a-class-loader-in-java-and-how-does-it-work)
4. [How does the Garbage Collector (GC) work in Java? What are its algorithms?](#4-how-does-the-garbage-collector-gc-work-in-java-what-are-its-algorithms)
5. [What are PhantomReference, WeakReference, and SoftReference in Java?](#5-what-are-phantomreference-weakreference-and-softreference-in-java)
6. [What is the ForkJoinPool framework, and how does it work?](#6-what-is-the-forkjoinpool-framework-and-how-does-it-work)
7. [What is deadlock, and how do you avoid it in Java?](#7-what-is-deadlock-and-how-do-you-avoid-it-in-java)
8. [Explain how to implement a custom class loader in Java.](#8-explain-how-to-implement-a-custom-class-loader-in-java)
9. [How do you optimize performance in Java applications?](#9-how-do-you-optimize-performance-in-java-applications)
10. [What are Java’s key concurrency utilities in the java.util.concurrent package?](#10-what-are-javas-key-concurrency-utilities-in-the-javautilconcurrent-package)

#### 1. What are the key differences between ConcurrentHashMap and SynchronizedMap?
- **ConcurrentHashMap**
    - Allows concurrent reads and writes.
    - Uses a lock on a portion of the map (bucket-level locking).
- **SynchronizedMap**
    - Synchronizes the entire map.
    - Slower due to full locking.

#### 2. Explain Java’s memory model (JMM). How does it impact multi-threading?
- Defines how threads interact through memory.
- Ensures happens-before relationship: if one action happens-before another, the first is visible and ordered.
- Key concepts: volatile, synchronized, and locks.

#### 3. What is a class loader in Java, and how does it work?
- Loads Java classes into the JVM at runtime.
- **Types**
    - **Bootstrap ClassLoader** - Loads core Java classes (java.lang, java.util).
    - **Extension ClassLoader** - Loads classes from ext directories.
    - **Application ClassLoader** - Loads classes from the application's classpath.
    - Follows the parent delegation model.

#### 4. How does the Garbage Collector (GC) work in Java? What are its algorithms?
- GC automatically manages memory by reclaiming unused objects.
- **Algorithms**
    - **Mark and Sweep** - Marks reachable objects and removes the unmarked.
    - **Generational GC** - Divides heap into young, old, and permanent generations.
    - **G1GC (Garbage First)** - Focuses on regions and minimizes pause times.

#### 5. What are PhantomReference, WeakReference, and SoftReference in Java?
- **SoftReference** - Retained until memory is low.
- **WeakReference** - Cleared during the next GC if no strong references exist.
- **PhantomReference** - Enqueues reference after object is finalized but before memory is reclaimed.

#### 6. What is the ForkJoinPool framework, and how does it work?
- Parallelizes large tasks into smaller subtasks using the divide-and-conquer approach.
- Uses a work-stealing algorithm to balance tasks among threads.

#### 7. What is deadlock, and how do you avoid it in Java?
- **Deadlock** - Occurs when two or more threads are waiting for each other’s locks indefinitely.
- **Avoidance**
    - Use lock ordering.
    - Use tryLock() from ReentrantLock.
    - Minimize synchronized blocks.

#### 8. Explain how to implement a custom class loader in Java.
- Extend the ClassLoader class.
- Override findClass(String name) to define custom loading logic.
- Use defineClass() to convert bytecode into a Class object.

#### 9. How do you optimize performance in Java applications?
- Use efficient data structures (e.g., HashMap over Hashtable).
- Minimize synchronization overhead.
- Use JVM profiling tools (e.g., VisualVM, JProfiler).
- Leverage lazy loading and caching.
- Optimize GC by tuning JVM parameters (-Xms, -Xmx).

#### 10. What are Java’s key concurrency utilities in the java.util.concurrent package?
- **Executors** - Manage thread pools.
- **Locks** - Fine-grained control over synchronization (ReentrantLock).
- **CountDownLatch** - Wait for threads to complete.
- **CyclicBarrier** - Synchronize threads at a common point.
- **BlockingQueue** - Thread-safe queue operations.
- **Atomic variables** - Support lock-free thread-safe operations