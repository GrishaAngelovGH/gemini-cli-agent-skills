# Python Review Checklist

## 1. Idiomatic Python (Pythonic Code)
- [ ] **PEP 8:** Does the code follow PEP 8 style guidelines (naming, indentation, whitespace)?
- [ ] **Comprehensions:** Are list/dict/set comprehensions used instead of simple loops where appropriate?
- [ ] **Context Managers:** Are `with` statements used for resource management (files, network connections)?
- [ ] **Truthiness:** Is truthiness used idiomatically (e.g., `if items:` instead of `if len(items) > 0:`)?

## 2. Type Hinting & Documentation
- [ ] **Type Hints:** Are function signatures annotated with type hints (PEP 484)?
- [ ] **Docstrings:** Do modules, classes, and functions have descriptive docstrings (PEP 257)?

## 3. Performance & Efficiency
- [ ] **Generators:** Are generators used for processing large datasets to save memory?
- [ ] **Built-ins:** Are built-in functions and standard libraries used effectively (e.g., `itertools`, `collections`)?

## 4. Error Handling
- [ ] **Exceptions:** Are specific exceptions caught? Avoid `except Exception:`.
- [ ] **Logging:** Is the `logging` module used instead of `print()`?

## 5. AsyncIO
- [ ] **Await/Async:** In async code, are all I/O-bound calls awaited? Is there blocking code inside an async def?
