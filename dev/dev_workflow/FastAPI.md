# ⚡ Stage 2: FastAPI Implementation Workflow (v2026.2)

## 🎯 Primary Objective

To implement approved architectural designs into high-performance, type-safe, and asynchronous Python backends. This document governs the Implementation and Validation phases for FastAPI development [cite: master_workflow 4].

## 🚦 Rule of Engagement: The "FastAPI Investigation"

Before generating any code, you MUST perform a Deep Investigation of:

Pydantic Schemas: Review existing BaseModel definitions to ensure strict data validation and avoid duplicate schemas.

Dependency Injection (DI) Tree: Identify existing dependencies (e.g., Auth, DB sessions) to maintain a clean, testable DI graph.

Async Safety: Verify that all planned I/O operations (DB, external APIs) are handled asynchronously to prevent blocking the event loop.

Authoritative State: Review database constraints and Pydantic validators to ensure invariants are preserved at the entry point [cite: master_workflow 2].

## 🏗️ FastAPI-Specific Implementation Standards

1. Invariants & Correctness (Pydantic & Pythonic Rigor)

Strict Modeling: Use Pydantic v2 for all Request/Response bodies. Prefer BaseModel with explicit field descriptions and validation. Use Strict=True where data integrity is critical [cite: AGENTS Rule 21].

Writes Decide, Reads Inform: Avoid "check-then-act" patterns (TOCTOU races). Use database-level atomicity and async-safe locks for shared state [cite: master_workflow 2].

Explicitness: All function signatures must use type hints and Annotated for dependencies to ensure clear contracts [cite: AGENTS Rule 13].

2. Asynchronous Excellence

Non-Blocking I/O: Every external call must use async/await. Use httpx for external requests and an async driver (like SQLAlchemy + asyncpg) for databases.

Background Tasks: Offload long-running processes to BackgroundTasks or a distributed worker (Celery/TaskIQ) to keep the request-response cycle fast.

Concurrency Safety: Understand the event loop; avoid CPU-bound tasks in async routes—delegate them to thread pools or separate processes.

3. Architecture & Dependency Injection

Service Layer Pattern: Isolate complex business logic into standalone service classes/functions, keeping endpoints "thin" [cite: AGENTS Rule 10].

Explicit DI: Favor FastAPI's Depends() for service injection over global singletons to ensure code is easily mockable in tests.

Router Modularity: Group endpoints into APIRouter instances by domain (e.g., /users, /orders) to maintain separation of concerns.

## 🧱 Atomic Task Specification (FastAPI)

For every approved task from Stage 1, generate a spec including:

Given: Initial state, endpoint signatures, and required Pydantic models.

When: The specific Service logic or API action.

Then: Expected outcome, Response Schema, and HTTP status codes.

Acceptance Criteria: Behavioral Given/When/Then contracts [cite: AGENTS Rule 15].

## 🧪 Implementation Discipline

Atomic Commits: feat(api): <summary> – one logical change per commit [cite: git 3.3].

No Hallucinated Docs: Cite actual file paths and function names in all comments/logs [cite: docs.md].

Struggle Briefly: Use AI for boilerplate; keep ownership of business logic, async safety, and invariant enforcement [cite: master_template Step 6].

### ✅ Completion Checklist (Rule 66)

[ ] ruff (linter) and mypy (type checker) pass with zero errors.

[ ] OpenAPI documentation is accurate and includes examples/descriptions.

[ ] All I/O operations are confirmed asynchronous and non-blocking.

[ ] Error handling uses HTTPException with meaningful status codes—no stack traces leaked.

Quick Start: "FastAPI Workflow v2026.2 initialized. Architecture is approved. Please provide the Task ID or ADR. I will investigate the Pydantic model hierarchy and dependency tree before proposing Task 2.1."