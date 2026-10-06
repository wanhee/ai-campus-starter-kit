# 🤖 Enterprise Engineering Rules & Guardrails (AGENTS.md)
> This document defines the non-negotiable architectural and security standards for this repository.
> All human and AI contributors must strictly adhere to these rules before committing any code.

---

## 1. Security & Credentials Guardrails
- **CWE-798 (No Hardcoded Secrets)**:
  - NEVER hardcode API keys, JWT secrets, passwords, or tokens in source code.
  - Always read from environment variables (`os.getenv()` in Python, `process.env` in JS/TS).
  - Use `.env.example` to document required variable keys without values.
- **CWE-89 (SQL Injection Prevention)**:
  - NEVER concatenate or format strings (`f"..."`, `+`) into raw SQL queries.
  - Always use parameterized queries (`cursor.execute("SELECT ... WHERE id = ?", (id,))`).
  - Use ORM or query builder with type checking.
- **CWE-327 (Cryptographic Standards)**:
  - NEVER use plain MD5 or SHA-1 for passwords or integrity signatures.
  - Use salted SHA-256 (`hashlib.sha256(password + salt)`) or modern bcrypt/Argon2.
- **Supply Chain Security**:
  - Only import established, verified third-party packages.
  - Do NOT invent or import hallucinated package names (Slopsquatting defense).

---

## 2. Performance & Time Complexity SLAs
- **Loop Complexity**:
  - Avoid nested $O(N^2)$ loops over unbounded user collections.
  - For repeated lookups, convert Lists to Hash Sets (`set()`) or Dictionaries (`dict`) for $O(1)$ operations.
- **Database Indexing & Concurrency (CWE-400)**:
  - Any column frequently queried in `WHERE`, `ORDER BY`, or `JOIN` must be indexed.
  - Verify query execution plans with `EXPLAIN` to prevent Full Table Scans.
  - SQLite default Rollback Journal blocks concurrent writers and leads to `database is locked` (HTTP 500) errors under high concurrency. Always enable Write-Ahead Logging (`PRAGMA journal_mode=WAL;`) and configure a busy timeout (`PRAGMA busy_timeout=5000;`) to ensure non-blocking concurrent writes.

---

## 3. Reliability & Exception Handling
- **No Bare Except**:
  - NEVER write bare `except:` or `except Exception: pass` without logging.
  - Always catch specific exception types (`KeyError`, `ValueError`, `HTTPError`) and handle them cleanly.
- **API Contracts**:
  - All public endpoints must return consistent JSON schemas with appropriate HTTP status codes (200, 400, 401, 404, 500).

---

## 4. Harness & Verification Requirements
- Every new feature or bugfix must pass:
  1. `check_harness.py` (Security AST Linter & Benchmark)
  2. Automated Unit Tests with $\ge 85\%$ test coverage
