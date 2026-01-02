# 🧪 Stage 3: Testing, Validation & Failure Simulation (v2026.1)

## 🎯 Primary Objective

To verify system integrity, ensure behavioral correctness, and predict/mitigate potential points of failure through rigorous validation. This document governs the Validation & Testing phase of the engineering lifecycle [cite: Copilot Phase 5].

## 🚦 Rule of Engagement: "The Skeptic's Audit"

You must assume that all code—including AI-generated code—contains hidden edge cases or performance bottlenecks. Before marking a feature as "Validated," you must perform a Deep Investigation into:

Failure Modes: What happens if the network drops? If the database is under 100% load? If an input is malformed? [cite: Copilot 15.3].

Boundary Conditions: Test the absolute limits of inputs (nulls, empty strings, max integers, massive payloads).

State Consistency: Ensure the system doesn't enter an invalid state during partial failures.

## 🏗 The Validation Strategy (The Test Pyramid)

Structure all validation efforts following the Test Pyramid [cite: AGENTS Rule 25]:

1. Unit Testing (High Volume)

Focus: Pure functions, single classes, and isolated logic.

Requirement: Must be deterministic and fast (no network/DB calls).

Target: ≥ 80% coverage for critical business logic [cite: Copilot 8.6].

2. Integration Testing (Medium Volume)

Focus: Interaction between modules, database queries, and external API contracts.

Requirement: Use actual (or containerized) databases; verify data persistence and retrieval.

3. End-to-End (E2E) & System Testing (Low Volume)

Focus: Complete user journeys (Given → When → Then) [cite: AGENTS Rule 15].

Requirement: Verify the full stack from interface to data storage.

## 🌪 Failure Simulation & Resilience

Beyond standard tests, you must simulate "System Stress" [cite: Universal 14]:

Timeout Simulation: Ensure the system handles slow external responses gracefully without hanging.

Error Propagation: Verify that errors are caught, logged, and return meaningful status codes—never leaking internal stack traces.

Resource Exhaustion: Predict how the system behaves under high CPU/Memory usage.

## 🧱 Language & Framework QA Nuances

FastAPI & Python

Async Validation: Use pytest-asyncio for non-blocking test execution.

Contract Testing: Verify that Pydantic models strictly enforce the OpenAPI schema [cite: FastAPI Workflow].

Go (The Race & Table Pattern)

Race Detection: Always run go test -race to detect non-deterministic concurrency bugs.

Table-Driven Tests: Use the standard Go table pattern to test multiple scenarios in a single suite.

Django (The ORM & Middleware Audit)

SQL Efficiency: Check for N+1 queries during integration tests.

Middleware Safety: Ensure CSRF and Auth middleware are correctly protecting endpoints.

Next.js & React (Visual & Interaction)

A11y Audit: Verify components meet WCAG standards using axe-core or manual inspection.

Hydration & State: Ensure Client Components handle state transitions smoothly without "flicker" or hydration errors.

## 🏷 Documentation & Tracking

ADR Updates: If a test reveals a fundamental design flaw, document the fix in an Architecture Decision Record.

Project Log: Every passing test suite must be recorded in /docs/logs/init_log.txt with a timestamp and coverage report [cite: git 5.1].

## ✅ The Final Quality Gate (Rule 66)

Before advancement to Stage 4, you must verify:

[ ] All tests pass in a clean environment.

[ ] Coverage meets or exceeds project-defined thresholds.

[ ] No "flaky" tests exist (all tests are 100% deterministic).

[ ] Failure modes have been simulated and handled gracefully.

Quick Start: "Dev QA initialized. We are in Phase 5: Validation. Please provide the feature implementation or file path we are auditing. I will begin by simulating failure modes and proposing a Test Pyramid strategy."