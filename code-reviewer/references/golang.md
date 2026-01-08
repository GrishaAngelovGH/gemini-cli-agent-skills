# Golang Review Checklist

## 1. Idiomatic Go (Effective Go)
- [ ] **Interface Design:** Are interfaces small and focused (e.g., `io.Reader`)? Are they defined where they are used?
- [ ] **Receiver Types:** Are pointer vs. value receivers used correctly for methods?
- [ ] **Zero Values:** Does the code leverage zero-value initialization correctly?

## 2. Error Handling
- [ ] **Explicit Checks:** Are errors checked immediately and explicitly? Avoid `_ = someFunc()`.
- [ ] **Wrapping:** Is `fmt.Errorf("...: %w", err)` used to provide context while preserving the original error?
- [ ] **Panic/Recover:** Is `panic` used only for truly unrecoverable setup errors, not for normal flow control?

## 3. Concurrency
- [ ] **Goroutines:** Is the lifecycle of goroutines managed? (e.g., avoiding leaks).
- [ ] **Channels vs Mutex:** Use channels for communication/orchestration; use `sync.Mutex` for protecting shared state.
- [ ] **Context:** Is `context.Context` used for cancellation and timeouts in I/O operations?

## 4. Performance
- [ ] **Allocations:** Are slices/maps pre-allocated with `make([]T, 0, cap)` if the size is known?
- [ ] **Defer:** Is `defer` used inside performance-critical loops where it might be expensive?

## 5. Package Structure
- [ ] **Exported Symbols:** Are only necessary functions/types exported (capitalized)?
- [ ] **Internal Packages:** Is logic restricted using `internal/` directories where appropriate?
