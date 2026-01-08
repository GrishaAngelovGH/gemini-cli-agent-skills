# Node.js Review Checklist

## 1. Runtime & Event Loop
- [ ] **Blocking Code:** Avoid synchronous methods (e.g., `fs.readFileSync`) in I/O-heavy paths.
- [ ] **Event Loop Health:** Are there any long-running loops or heavy computations that could block the event loop?

## 2. Resource Management
- [ ] **Streams:** Are streams used for processing large data sets (e.g., file uploads, logs)?
- [ ] **Buffers:** Is `Buffer` used correctly for binary data?
- [ ] **Memory Leaks:** Check for growing global arrays, unclosed event listeners, or closures holding large objects.

## 3. Error Handling
- [ ] **Global Handlers:** Are `uncaughtException` and `unhandledRejection` handled properly?
- [ ] **Error Objects:** Always throw `Error` objects (or subclasses) to preserve stack traces.

## 4. Environment & Security
- [ ] **Env Vars:** Are environment variables used for configuration? Are they validated at startup?
- [ ] **Package Management:** Check `package.json` for unnecessary or vulnerable dependencies.
- [ ] **CORS/Headers:** Are security headers (e.g., Helmet) used in web servers?
