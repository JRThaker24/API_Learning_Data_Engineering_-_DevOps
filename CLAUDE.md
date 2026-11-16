# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repository is

A personal learning workspace following a "Python Roadmap for Data Engineers" (Ansh Lamba's YouTube guide, linked in `README.md`). It is **not** an application — there is nothing to build, deploy, or ship. Content is a set of self-contained Jupyter notebook cheatsheets, each teaching one topic through runnable examples with their expected output written inline.

## Layout

- `Cheatsheets/` — the actual material, one `.ipynb` per topic:
  - `numpy_cheatsheet.ipynb`, `pandas_cheatsheet.ipynb` — numbered-section reference notebooks
  - `PySpark.ipynb` — largest (187 cells); DataFrame reading, schemas, transformations
  - `DB_Pandas_Connections.ipynb` — MySQL (PyMySQL) / PostgreSQL (psycopg2) → pandas
  - `Flask_Fundamentals.ipynb` — Flask routing/request-response tutorial
  - `python_practice_questions.ipynb` — practice exercises (list comprehensions, etc.)
- `Roadmap/` — the roadmap image (`.svg`/`.png`), non-code reference
- `.venv/` — committed Python 3.13 virtualenv (jupyter + ipykernel only; pandas/numpy/pyspark are **not** installed here)

## Working in this repo

Activate the environment and run notebooks with:

```bash
source .venv/bin/activate
jupyter notebook            # or: jupyter lab
```

The venv ships only Jupyter/IPython. Libraries a notebook imports (pandas, numpy, pyspark, pymysql, psycopg2-binary, flask) must be `pip install`ed as needed — each notebook's opening section lists its own install command.

## Conventions when editing notebooks

- Edit `.ipynb` files with the NotebookEdit tool, not by hand-editing JSON.
- Match the established structure: numbered `## N. Topic` markdown headers, a code cell demonstrating it, and expected output shown either as cell output or inline in the markdown (` ``` ` blocks). Preserve this teaching format when adding cells.
- Database and connection notebooks use **placeholder** credentials (host/user/password). Keep them as obvious placeholders — never substitute real connection details.

## `Flask_REST_API_Masterclass` course (in progress)

`Cheatsheets/Flask_REST_API_Masterclass.ipynb` is a long-form, in-progress course the owner is building **one module at a time**. It has different conventions from the other cheatsheets — treat it as its own thing. If asked to continue it, follow everything below.

### The ROLE you must adopt when writing this course

Write as a **Senior Python Software Engineer + Senior Data Engineer + Senior Backend Architect + Technical Instructor with 20+ years' experience** — "a university professor combined with a FAANG engineering mentor." The goal is a self-contained masterclass that takes the reader from absolute zero to production-grade Flask REST APIs, framed throughout for someone becoming a **Data Engineer**.

Hard requirements for the writing:
- **No prior Flask knowledge assumed.** Start from zero; every concept builds on the previous one.
- **Depth over brevity.** Each module is a substantial standalone lesson (target ~8,000–15,000 words). Do not summarize away fundamentals. (This overrides the usual "be concise" instinct — the owner explicitly wants exhaustive depth here.)
- **Explain every line of code** — why it exists and what happens internally. Never skip code explanations.
- **Data Engineering lens on every topic** — where DEs use it in real projects, production use cases (extract/load, ETL/ELT, pagination, rate limits, retries/backoff, idempotency, incremental loads, token refresh, schema evolution, monitoring).
- Use **ASCII diagrams / flowcharts, analogies, real-world + industry examples, interview tips, best practices, and common mistakes** liberally.
- **Coding style:** Python 3.13+, latest Flask, PEP 8, type hints, docstrings, meaningful comments, production standards.

### Per-module structure (every module must end with these)

Every module ends with: **Summary → Interview Questions (with model answers) → MCQs (+ answer key) → Coding Exercises → Mini Lab → Common Mistakes.** Within a module, follow the owner's 16-step learning format where it fits: Concept → Why → When to Use → Real Example → Industry Example → Diagram → Code → Line-by-line Explanation → Output → Common Errors → Best Practices → Interview Tips → Exercise → Lab → Challenge → Summary.

### Module roadmap (25 modules)

| # | Module | Status |
|---|--------|--------|
| 1 | What Is An API | ✅ done (~9,200 words, 34 cells) |
| 2 | HTTP Complete (browser, DNS, TCP, TLS handshake, headers, methods, status codes, cookies/sessions, JWT, OAuth, Bearer, request lifecycle) | ✅ done (~7,300 words, 27 cells) |
| 3 | REST API Complete (constraints, resources/URI/endpoint, CRUD, all methods, safe/idempotent, naming, versioning, filtering/sorting/pagination) | ⏳ |
| 4 | JSON Complete (serialize/deserialize, dict mapping, nested/complex JSON, parsing/generating) | ⏳ |
| 5 | Flask Fundamentals (install, venv, project structure, architecture, routing, app factory, templates, static, blueprints, config, env vars, debug) | ⏳ |
| 6 | Flask Routing (dynamic routes, converters, variables, methods, blueprint routing) | ⏳ |
| 7 | Request Object (`args`, `form`, `json`, `files`, `headers`, `cookies`, `method`, `values`, `path`, `url`, `host`, `remote_addr`) | ⏳ |
| 8 | Response Object (`jsonify`, `make_response`, Response class, headers, cookies, custom status codes) | ⏳ |
| 9 | All HTTP Methods (GET/POST/PUT/PATCH/DELETE/HEAD/OPTIONS — each with example, diagram, code, interview Q) | ⏳ |
| 10 | CRUD API Project (Employee API: full CRUD, validation, error handling, status codes) | ⏳ |
| 11 | Database (SQLite → SQLAlchemy → PostgreSQL, CRUD DB ops) | ⏳ |
| 12 | Validation (input/schema validation, Marshmallow, Pydantic) | ⏳ |
| 13 | Error Handling (custom exceptions, global handler, logging) | ⏳ |
| 14 | Authentication (API keys, JWT, Bearer token, OAuth basics) | ⏳ |
| 15 | Testing (Postman, curl, pytest, Flask test client) | ⏳ |
| 16 | Production (Gunicorn, Nginx, Docker, env vars, logging, security) | ⏳ |
| 17 | **Data Engineering APIs** (the most important module: extract/load, API↔DB, ETL/ELT, scheduling, Airflow, Kafka, streaming/batch, webhook vs polling, rate limits, retry/exponential backoff, DLQ, incremental/delta/cursor/offset pagination, token refresh, schema evolution, monitoring) | ⏳ |
| 18 | 10 Complete Projects (Student, Library, Employee, Movie, Weather consumer, GitHub consumer, COVID dashboard, ETL-via-API, API gateway demo, mini banking) | ⏳ |
| 19 | Advanced API Design (versioning, pagination, filtering, sorting, searching, caching, rate limiting, compression, OpenAPI, Swagger) | ⏳ |
| 20 | Interview Preparation (100 interview Qs, 50 scenarios, 20 debugging, 20 design, 20 DE-API) | ⏳ |
| 21 | Labs (per-chapter: 10 MCQs, 5 coding, 3 debugging, 2 output-prediction, 1 mini project) | ⏳ |
| 22 | Capstone Project (production-grade: auth, JWT, SQLite, SQLAlchemy, logging, validation, CRUD, pagination, filtering, Docker, Swagger, error handling, testing, structure, README, requirements.txt) | ⏳ |
| 23 | Cheatsheets (HTTP, REST, status codes, Flask, request, response, JSON, CRUD, auth, testing) | ⏳ |
| 24 | Visual Learning (ASCII diagrams / flowcharts everywhere) | ⏳ |
| 25 | Learning Style Reference (the 16-step format applied) | ⏳ |

Update the `Status` column as modules are completed.

### `NEXT` trigger convention

- Generate **only ONE module per response**, then **stop and wait**.
- When the owner types **`NEXT`**, append the next module in the roadmap, **maintaining continuity** (cross-reference earlier/later modules, keep the running Course Map table's status current).
- Do **not** dump future modules ahead of time. The end state is all 25 modules combined into this one cohesive notebook.

### How this notebook is built (mechanics)

Because modules are huge (lots of markdown + ASCII diagrams), building the `.ipynb` JSON by hand is error-prone. Instead each module is generated by a **Python builder script** in the session scratchpad that:
- defines `md(text)` / `code(text)` cell helpers (auto-incrementing cell ids),
- holds the module content in triple-quoted raw strings,
- **loads the existing notebook and appends** the new cells (creates it fresh only if absent), preserving the single-notebook-grows design,
- writes with `json.dump(..., indent=1, ensure_ascii=False)` and prints cell/word counts.

After running the builder, **validate** the file loads (`python3 -c "import json; json.load(open(path))"`). One code cell per module is acceptable (Modules 1–4 are largely conceptual); later modules will contain real, runnable Flask code. Assume libraries (`flask`, `requests`, `sqlalchemy`, etc.) are **not** in `.venv` — tell the reader the `pip install` line, matching the repo convention.
