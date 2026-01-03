# 🐍 Stage 2: Django Implementation Workflow (v2026.2)

## 🎯 Primary Objective

To implement approved architectural designs into a stable, secure, and idiomatic Django application. This document governs the Implementation and Validation phases for backend development [cite: master_workflow 4].

## 🚦 Rule of Engagement: The "Django Investigation"

Before generating any code, you MUST perform a Deep Investigation of:

Authoritative State: Review models.py and DB constraints to ensure invariants are enforced at the database level [cite: master_workflow 2].

Existing Service Layer: Check services.py or selectors.py to maintain separation of concerns.

Migration History: Verify the current state of migrations to avoid schema drift.

## 🏗️ Django-Specific Implementation Standards

1. Invariants & Correctness (Backend First)

** Authoritative Constraints:** Prefer DB-level unique indexes and constraints for data invariants [cite: master_workflow 2, 8.1].

Atomic Operations: Use transaction.atomic() for any operation involving multiple database writes.

Writes Decide, Reads Inform: Avoid "check-then-act" logic (TOCTOU races). Use update() with filters or select_for_update() [cite: master_workflow 2, 8.2].

2. Architecture: Fat Models, Thin Views, Services

Business Logic: Must live in the Service Layer (services.py). Views handle only request/response; Models handle only data definitions [cite: AGENTS Rule 10].

Strict Typing: Use Python type hints and Pydantic/Ninja schemas for all API contracts to ensure explicit behavior [cite: AGENTS Rule 21].

3. Performance & API Integrity

ORM Optimization: Always use .select_related() and .prefetch_related() to eliminate N+1 queries.

Idempotency: Make retryable API operations safe to call multiple times [cite: master_workflow 11].

## 🧱 Atomic Task Specification (Django)

For every approved task from Stage 1, generate a spec including:

Given: Initial DB state and context.

When: The specific ORM/Service action.

Then: Expected outcome and DB state.

Acceptance Criteria: Behavioral Given/When/Then contracts [cite: AGENTS Rule 15].

## 🧪 Implementation Discipline

Atomic Commits: feat(<app>): <summary> – one logical change per commit [cite: git 3.3].

No Hallucinated Docs: Cite actual file paths and function names in all comments/logs [cite: docs.md].

Struggle Briefly: Use AI for boilerplate; keep ownership of business logic [cite: master_template Step 6].

### ✅ Completion Checklist (Rule 66)

[ ] No hardcoded secrets (use .env).

[ ] All I/O is documented and handled (timeouts, retries).

[ ] Migrations are generated and reversible.

[ ] No print() statements; use standard logging.

Quick Start: "Django Workflow v2026.2 initialized. Architecture is approved. Please provide the Task ID or ADR. I will investigate the models.py and services.py boundaries before proposing Task 2.1."