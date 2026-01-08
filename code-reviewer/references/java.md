# Java Review Checklist

## 1. Effective Java Patterns
- [ ] **Immutability:** Are classes immutable where possible? (e.g., `final` fields, no setters).
- [ ] **Streams & Optionals:** Are `Stream` API and `Optional` used idiomatically to replace loops and null checks?
- [ ] **Builders/Factories:** Are creational patterns used for complex objects?

## 2. Concurrency & Threading
- [ ] **Thread Safety:** Is shared mutable state properly synchronized or using `java.util.concurrent` classes (e.g., `ConcurrentHashMap`)?
- [ ] **Virtual Threads (Java 21+):** Is the code leveraging virtual threads for I/O bound tasks where appropriate?
- [ ] **Atomic Variables:** Are `AtomicInteger`, `AtomicReference`, etc., used for lock-free synchronization?

## 3. Resource Management
- [ ] **Try-with-resources:** Are all `AutoCloseable` resources (streams, connections) closed using try-with-resources?
- [ ] **Memory:** Are there potential memory leaks (e.g., static collections growing indefinitely, unclosed listeners)?

## 4. Exception Handling
- [ ] **Specificity:** Are specific exceptions caught rather than generic `Exception`?
- [ ] **Logging:** Are exceptions logged with their stack trace? Avoid swallowing exceptions.
- [ ] **Custom Exceptions:** Are custom exceptions used for domain-specific errors?

## 5. Testing & Documentation
- [ ] **JUnit/Mockito:** Are unit tests using modern assertions (e.g., AssertJ) and proper mocking?
- [ ] **Javadoc:** Is public API properly documented with Javadoc?
