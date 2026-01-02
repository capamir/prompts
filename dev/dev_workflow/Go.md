# 🐹 Stage 2: Go Implementation Workflow (v2026.1)

## 🎯 Primary Objective

To implement approved architectural designs into a high-performance, maintainable, and idiomatic Go application. This document governs the Implementation and Validation phases [cite: Copilot Phase 4-5].

## 🚦 Rule of Engagement: The "Go Investigation"

Before generating any code, you must perform a Deep Investigation of:

Project Structure: Identify if the project follows /internal vs /pkg conventions or a flat structure.

go.mod & Dependencies: Check for current toolchain versions and core libraries to avoid duplicate dependencies.

Interfaces & Structs: Locate existing abstractions to ensure new code satisfies current contracts without breaking changes.

## 🏗 Go-Specific Implementation Standards

### 1. Idiomatic Rigor (The Go Proverbs)

Explicit Error Handling: Never ignore errors. Handle them immediately at the call site. Wrap errors with context: fmt.Errorf("context: %w", err).

No Magic: Avoid init() functions and global state. Use explicit dependency injection via constructors.

Interfaces: Use interfaces only when multiple implementations exist. "Accept interfaces, return structs."

### 2. Concurrency & Performance

Goroutines: Use concurrency only for truly independent, non-blocking tasks.

Channels vs. Mutex: Use channels for communication/orchestration and mutexes for state protection. "Don't communicate by sharing memory; share memory by communicating."

Resource Management: Always use defer for closing files, database connections, or releasing locks.

### 3. Structural Design

Internal vs Pkg: Keep private logic in internal/ to prevent external package leakage.

Composition: Use struct embedding sparingly; favor explicit composition to avoid fragile hierarchies.

Standard Library First: Exhaust the std library capabilities before reaching for external dependencies [cite: AGENTS Rule 23].

## 🧱 Atomic Task Specification (Go)

For every sub-task, generate a spec using this checklist:

Scope: Which package and specific files are being modified/created?

Signature: Define the exact function/method signatures and their types.

Concurrency: Does this task involve goroutines or shared state? Define the synchronization strategy.

Tests: Which _test.go file and specific test cases will validate this?

## 🧪 Validation & Testing (The Go Pyramid)

Table-Driven Tests: Use the standard Go pattern for testing multiple scenarios (happy and failure paths) in a single test function.

Race Detection: Always run tests with the -race flag to catch non-deterministic concurrency bugs.

Benchmarking: For performance-critical logic, provide Benchmark functions to justify implementation choices.

🏷 Git & Documentation Discipline

Commit Format: feat(pkg-name): <summary> or fix(internal/auth): <summary> [cite: git 3.1].

Comments: Use standard Go doc comments (// FunctionName ...). Explain why a complex algorithm is used, not just what it does.

Project Log: Update /docs/logs/init_log.txt after every validated task [cite: git 5.1].

## ✅ Completion Checklist (Rule 66)

[ ] go fmt and go vet pass without warnings.

[ ] All errors are handled explicitly.

[ ] golangci-lint (or similar linter) reports zero issues.

[ ] Concurrency is leak-free and verified by race detection.

Quick Start: "Go Workflow initialized. Architecture is approved. Please provide the specific ADR or Task ID we are starting. I will investigate the package boundaries and current interfaces before proposing Task 1.1."