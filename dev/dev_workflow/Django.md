# 🐍 Stage 2: Django Implementation Workflow (v2026.1)

## 🎯 Primary Objective

To implement approved architectural designs into a stable, secure, and idiomatic Django application. This document governs the Implementation and Validation phases [cite: Copilot Phase 4-5].

## 🚦 Rule of Engagement: The "Django Investigation"

Before generating any code, you must perform a Deep Investigation of:

models.py & apps.py: To ensure alignment with the database schema and app registry.

settings.py: To check for installed apps, middleware, and environment variables.

Current Migrations: To avoid state drift or conflicting schema changes.

## 🏗 Django-Specific Implementation Standards

### 1. The "Fat Model / Service Layer" Choice

Small Apps: Keep logic in Models (Fat Models).

Complex Apps: Use a services.py or selectors.py layer to keep Business Logic separate from the Database and Views [cite: AGENTS Rule 10].

Views: Views must remain "Thin," handling only request parsing and response formatting.

### 2. Data Integrity & Types

Django Ninja/Pydantic: Use for API definitions to ensure strict type validation similar to Go [cite: AGENTS Rule 21].

Type Hints: All functions must include Python type hints for clarity and IDE support.

ORM Excellence: Use .select_related() and .prefetch_related() to prevent N+1 query problems.

### 3. Safety & Security

Migrations: Every model change must include a plan for makemigrations. Never skip migration files.

Input Sanitization: Trust nothing. Use Django Forms or Pydantic for all external input validation [cite: AGENTS Rule 42].

Environment Variables: Never hardcode SECRET_KEY, DEBUG, or DB credentials [cite: AGENTS Rule 24].

## 🧱 Atomic Task Specification (Django)

For every sub-task, generate a spec using this checklist:

Scope: Which specific App and Files are being modified?

Logic: What is the specific ORM or Business logic change?

Migrations: Does this require a schema update?

Tests: Which TestCase class or pytest function validates this?

## 🧪 Validation & Testing (The Django Pyramid)

Unit Tests: Test models and service functions in isolation (mock external APIs).

Integration Tests: Test Views and API endpoints using the Django Client or RequestFactory.

Schema Check: Verify python manage.py check and makemigrations --check pass.

## 🏷 Git & Documentation Discipline

Commit Format: feat(app-name): <summary> or fix(models): <summary> [cite: git 3.1].

Docstrings: Use PEP 257 docstrings for every class, method, and view.

Project Log: Update /docs/logs/init_log.txt after every validated task [cite: git 5.1].

## ✅ Completion Checklist (Rule 66)

[ ] flake8 / ruff / black formatting passes.

[ ] All new migrations are tested and reversible.

[ ] No print() statements; use logging.

[ ] coverage meets the 80% threshold for the modified app.

Quick Start: "Django Workflow initialized. Architecture is approved. Please provide the specific Feature ID or ADR we are implementing. I will investigate the existing app structure before proposing Task 1.1."