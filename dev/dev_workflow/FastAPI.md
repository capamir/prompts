# ⚡ Stage 2: FastAPI Implementation Workflow (v2026.1)

## 🎯 Primary Objective

To implement approved architectural designs into high-performance, type-safe, and asynchronous Python backends. This document governs the Implementation and Validation phases for FastAPI development [cite: Copilot Phase 4-5].

## 🚦 Rule of Engagement: The "FastAPI Investigation"

Before generating any code, you must perform a Deep Investigation of:

Pydantic Schemas: Review existing BaseModel definitions to ensure strict data validation and avoid duplicate schemas.

Dependency Injection (DI) Tree: Identify existing dependencies (e.g., Auth, DB sessions) to maintain a clean, testable DI graph.

Async Safety: Verify that all planned I/O operations (DB, external APIs) are handled asynchronously to prevent blocking the event loop.

Middleware & Routers: Check the current routing structure and middleware stack for cross-cutting concerns (CORS, Logging, Auth).

## 🏗 FastAPI-Specific Implementation Standards

### 1. Pydantic v2+ & Type Safety

Strict Modeling: Use Pydantic v2 for all Request/Response bodies. Prefer BaseModel with explicit field descriptions and validation.

Type Annotations: Use Python's Annotated type for dependencies and complex metadata to keep function signatures clean.

Schema Evolution: Ensure response models are explicit (response_model) to prevent leaking internal database fields.

### 2. Asynchronous Excellence

Non-Blocking I/O: Every external call must use async/await. Use httpx for external requests and an async driver (like SQLAlchemy + aiopg/asyncpg) for databases.

Background Tasks: Offload long-running processes to BackgroundTasks or Celery, keeping the request-response cycle fast.

### 3. Architecture & Dependency Injection

Router Modularity: Group endpoints into APIRouter instances by domain (e.g., /users, /orders).

Explicit DI: Favor FastAPI's Depends() for service injection over global singletons to ensure code is easily mockable in tests [cite: AGENTS Rule 13].

Service Layer Pattern: Isolate complex business logic into standalone service classes/functions, keeping endpoints thin.

## 🧱 Atomic Task Specification (FastAPI)

For every sub-task, generate a spec including:

Endpoint Signature: Method (GET/POST/etc.), Path, and explicit input/output Schemas.

Dependency Chain: List all required dependencies (Auth, DB, Custom).

Business Logic: Define the data transformation or service call required.

Validation: Specify the pytest file and the expected OpenAPI schema change.

## 🧪 Validation & Testing (The Python Pyramid)

Async Unit Tests: Use pytest-asyncio and httpx.AsyncClient to test endpoints and services.

OpenAPI Compliance: Verify that the generated /docs (Swagger) matches the implementation and requirements.

Static Analysis: Enforce type checking with mypy and linting with ruff to catch errors before runtime.

🏷 Git & Documentation Discipline

Commit Format: feat(api): <summary> or fix(schema): <summary> [cite: git 3.1].

Google Style Docstrings: Use standard Python docstrings for every endpoint and service function.

Project Log: Update /docs/logs/init_log.txt after every passing test suite [cite: git 5.1].

## ✅ Completion Checklist (Rule 66)

[ ] ruff and mypy pass with zero errors.

[ ] OpenAPI documentation is accurate and includes examples.

[ ] All I/O operations are confirmed asynchronous.

[ ] No print() statements; use standard Python logging.

[ ] Error handling uses HTTPException with meaningful status codes and detail.

Quick Start: "FastAPI Workflow initialized. Architecture is approved. Please provide the specific Endpoint ID or ADR we are building. I will investigate the Pydantic model hierarchy and dependency tree before proposing Task 1.1."