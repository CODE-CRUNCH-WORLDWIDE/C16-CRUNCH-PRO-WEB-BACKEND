# C16 · Crunch Pro — Python Web Backend

> A 12-week open-source course on building production-grade Python web backends with **Django** and **FastAPI** — from your first view to a deployed, observable, multi-tenant service.

[![License: GPL v3](https://img.shields.io/badge/License-GPL%20v3-blue.svg)](LICENSE)
[![Python 3.11+](https://img.shields.io/badge/python-3.11+-blue.svg)](https://www.python.org/downloads/)
[![Built in the open](https://img.shields.io/badge/built-in%20the%20open-B98F3E.svg)](https://github.com/CODE-CRUNCH-CLUB)

This is the senior-engineer track for Python on the web. It assumes you have completed **C1 · Code Crunch Convos** (or have equivalent Python proficiency) and the equivalent of Week 9 of C1 (basic Flask). C16 takes you from "I made a Flask app" to "I run a Python web service in production."

---

## What you will be able to do at the end of 12 weeks

- Design and ship a **Django application** with auth, admin, templates, forms, the ORM, migrations, signals, the test client, and a production-grade settings layout.
- Design and ship a **FastAPI service** with Pydantic models, dependency injection, async views, background tasks, OpenAPI docs, and JWT auth.
- Operate **PostgreSQL** comfortably: schema design, indexes, transactions, JSONB, full-text search, EXPLAIN ANALYZE.
- Write **integration tests** that hit a real database in <1s and run in CI on every PR.
- Set up **Redis** as a cache, queue broker (Celery / Arq), and rate limiter.
- Deploy with **Docker + Gunicorn/Uvicorn**, behind **Nginx**, with **HTTPS**, **structured logging**, and **Prometheus metrics**.
- Pick the right tool: when to use Django, when to use FastAPI, and when to use them together.
- Read and contribute to real open-source Django/FastAPI codebases without intimidation.

---

## Standards & equivalency

> C16 stands in for a university's server-side web programming course.

**University equivalent.** Server-Side Web Programming — `COP 4813`, `CS 4485`, `SWE 432`. Coverage: full.

C16 carries no credit, no transcript entry, no accreditation and no proctored exam. The equivalence is one of **content and skill**: everything an accredited section of that course teaches, taught here at the same depth or deeper, and assessed. What a registrar records is not something an open repository can give you.

| University outcome | Where this course teaches it | Depth |
| --- | --- | --- |
| Explain the HTTP request/response cycle and the client–server architecture of the web, and construct a request and a response directly | [Week 01](curriculum/week-01-http-and-the-modern-python-web/) | deeper |
| Build a server-side application on a web framework: URL routing, view code, server-rendered templates | [Week 03](curriculum/week-03-views-templates-forms-auth/) | same |
| Model application data, persist it through a data-access layer, and evolve the schema with migrations | [Week 02](curriculum/week-02-django-models-orm-admin/) | same |
| Design a relational schema, query it, and reason about indexing and query cost | [Week 04](curriculum/week-04-postgresql-for-app-developers/) | deeper |
| Retrieve and shape related data efficiently through the data-access layer instead of in application code | [Week 05](curriculum/week-05-django-orm-deep-dive/) | deeper |
| Implement user authentication, session management and access control, and defend the application against common web attacks | [Week 03](curriculum/week-03-views-templates-forms-auth/) | same |
| Design and implement a documented HTTP/JSON API that a second client can consume | [Week 07](curriculum/week-07-fastapi-fundamentals/) | deeper |
| Validate inbound data and serialise outbound data against a declared contract | [Week 07](curriculum/week-07-fastapi-fundamentals/) | deeper |
| Move long-running work out of the request/response cycle, and schedule recurring work | [Week 06](curriculum/week-06-migrations-jobs-caching/) | deeper |
| Implement server-push communication between browser and server | [Week 08](curriculum/week-08-websockets-sse-and-background-jobs/) | deeper |
| Apply caching and other performance techniques to a server application, and measure the result | [Week 09](curriculum/week-09-caching-with-redis/) | deeper |
| Test a server-side application, including tests that exercise the database and the HTTP layer | [Week 07](curriculum/week-07-fastapi-fundamentals/) | same |
| Deploy a server-side application to a production-like environment and operate it | [Week 12](curriculum/week-12-capstone-production-backend/) | same |
| Complete and defend a substantial server-side application project | [Week 12](curriculum/week-12-capstone-production-backend/) | same |

Every row above points at a week that **assigns work** on that outcome — an exercise, a challenge, homework, a quiz item or the week's mini-project — not merely a week that mentions it.

**The industry bar.** What an employer expects of somebody paid to run a Python web service, and where this course makes the learner do it. Two rows below say plainly where C16 does less than the bar asks.

| What the job expects | Where this course does it |
| --- | --- |
| Work lands as a commit in a repository the learner owns, not a file on a desktop | Week 01's acceptance list requires a public repository, a `.gitignore` and a README a stranger can follow — [`curriculum/week-01-http-and-the-modern-python-web/mini-project/README.md`](curriculum/week-01-http-and-the-modern-python-web/mini-project/README.md); every later mini-project builds on that repository |
| You read code you did not write and form a judgement on it | Week 02 sends the learner into a running open-source Django project to locate and fix an N+1 — [`curriculum/week-02-django-models-orm-admin/challenges/challenge-01-spot-the-n-plus-1.md`](curriculum/week-02-django-models-orm-admin/challenges/challenge-01-spot-the-n-plus-1.md); Week 11 hands over a service carrying three planted tenant-isolation bugs — [`curriculum/week-11-multi-tenancy/challenges/challenge-01-rls-leak-hunt.md`](curriculum/week-11-multi-tenancy/challenges/challenge-01-rls-leak-hunt.md) |
| Tests exist, and the command to run them is written down | `python manage.py test` in Week 01's acceptance list; `pytest -q` over `httpx.AsyncClient` in [`curriculum/week-07-fastapi-fundamentals/mini-project/README.md`](curriculum/week-07-fastapi-fundamentals/mini-project/README.md); `assertNumQueries(1)` on every panel of [`curriculum/week-05-django-orm-deep-dive/mini-project/README.md`](curriculum/week-05-django-orm-deep-dive/mini-project/README.md) |
| A performance claim is backed by a measured number, not an assertion | Week 04 ships a before/after `EXPLAIN ANALYZE` write-up with the index migration — [`curriculum/week-04-postgresql-for-app-developers/mini-project/README.md`](curriculum/week-04-postgresql-for-app-developers/mini-project/README.md); Week 09 requires a load-test baseline and a `BENCHMARK.md` — [`curriculum/week-09-caching-with-redis/mini-project/README.md`](curriculum/week-09-caching-with-redis/mini-project/README.md) |
| Dependencies are isolated per project and pinned | Week 01's mini-project rules require a virtual environment and a pinned `pyproject.toml` or `requirements.txt`; Week 07 pins every test dependency to an exact minor version |
| A pipeline runs the work on every push | Week 12's deploy lecture writes out both workflows — tests on every push, deploy only on green — and wires the deploy token as a secret: [`curriculum/week-12-capstone-production-backend/lecture-notes/02-deploy-to-a-free-tier.md`](curriculum/week-12-capstone-production-backend/lecture-notes/02-deploy-to-a-free-tier.md). It is one section of one lecture in the final week, not a unit of its own, and Week 06's forward reference to CI "in Week 11" does not land — Week 11 is multi-tenancy. |
| Failure is read from real output rather than guessed at | Partly. Week 07's worked solutions quote a real FastAPI 422 response body field by field, and Week 04 works from real query plans throughout. C16 carries no `Common bugs to catch` section and no captured tracebacks; the error text it does quote is protocol and validation output, not exceptions. |
| The service is operated, not only written — deploy, roll back, rotate a secret, evict a tenant | Week 12 requires each of those four as a section of `docs/runbook.md`, exercised against the live service — [`curriculum/week-12-capstone-production-backend/README.md`](curriculum/week-12-capstone-production-backend/README.md) |
| It runs from a clean clone by following the README | Graded explicitly in Week 01 ("`runserver`, `check`, `test` all clean on a fresh clone") and again in [`curriculum/week-03-views-templates-forms-auth/mini-project/README.md`](curriculum/week-03-views-templates-forms-auth/mini-project/README.md) |

**Beyond both bars.** Clearing the two floors is entry, not success. Open any of these and check in under a minute.

| What we add | Which bar it beats | Where it lives |
| --- | --- | --- |
| Week 01 forbids the framework's own scaffolding: the learner writes `manage.py`, `settings.py`, `wsgi.py` and `asgi.py` by hand, after reading a raw HTTP/1.1 exchange off a socket with `nc` | both | [`curriculum/week-01-http-and-the-modern-python-web/mini-project/README.md`](curriculum/week-01-http-and-the-modern-python-web/mini-project/README.md) |
| Every week's quiz publishes its answer key in the same file as the questions — nothing withheld until a deadline | both | [`curriculum/week-09-caching-with-redis/quiz.md`](curriculum/week-09-caching-with-redis/quiz.md) |
| Worked, explained solutions to the week's exercises, published beside them rather than after a submission window | both | [`curriculum/week-07-fastapi-fundamentals/exercises/SOLUTIONS.md`](curriculum/week-07-fastapi-fundamentals/exercises/SOLUTIONS.md) |
| Two frameworks against one database, with the boundary written down and defended — Django owns the admin and the migrations, FastAPI owns the typed async API | both | [`curriculum/week-12-capstone-production-backend/lecture-notes/01-the-capstone-architecture.md`](curriculum/week-12-capstone-production-backend/lecture-notes/01-the-capstone-architecture.md) |
| Three search backends measured against each other on fifty hand-labelled queries, with precision-at-5 reported per backend and the choice defended on the numbers | university | [`curriculum/week-10-search-fts-opensearch-meilisearch/challenges/challenge-01-three-backend-relevance-harness.md`](curriculum/week-10-search-fts-opensearch-meilisearch/challenges/challenge-01-three-backend-relevance-harness.md) |
| Tenant isolation enforced in the database with `FORCE ROW LEVEL SECURITY`, then attacked: three planted leaks to find, reproduce with a request, and close with a test that fails before the fix | both | [`curriculum/week-11-multi-tenancy/challenges/challenge-01-rls-leak-hunt.md`](curriculum/week-11-multi-tenancy/challenges/challenge-01-rls-leak-hunt.md) |
| Two job runners implemented on the same workload and benchmarked head to head, with a written defence of the choice a reviewer could disagree with on the merits | industry | [`curriculum/week-08-websockets-sse-and-background-jobs/challenges/challenge-02-celery-vs-arq-on-a-real-task.md`](curriculum/week-08-websockets-sse-and-background-jobs/challenges/challenge-02-celery-vs-arq-on-a-real-task.md) |
| The learner ends holding a running service on a public URL and a runbook for operating it, not a grade only a registrar can see | both | [`curriculum/week-12-capstone-production-backend/lecture-notes/02-deploy-to-a-free-tier.md`](curriculum/week-12-capstone-production-backend/lecture-notes/02-deploy-to-a-free-tier.md) |

**Gaps we declare.** None against the server-side web programming outcome set — every outcome above maps to a week that assigns work on it. Four honest shortfalls sit outside that set and are recorded here rather than left to be discovered: weeks 01–06 ship no worked exercise solutions and say so on their exercise index, so the published-answer guarantee holds for the quizzes everywhere but for the exercises only from Week 07 on; C16 carries no `Under the hood` blocks, so the depth sits inline where a reader must pass through it rather than folded away; it carries no `Common bugs to catch` sections quoting captured exception text; and continuous integration is one section of Week 12's deploy lecture rather than a unit of its own. C16 also does not teach browser-side code — it renders server-side HTML and serves JSON, and points at C8 for the client — and it does not teach container orchestration or infrastructure-as-code, which belong to C15.

---

## Prerequisites

You should have completed, or be able to do everything in, **C1 · Code Crunch Convos** weeks 1–11. Specifically you need:

- Comfortable with **functions, classes, exceptions, decorators, generators**.
- Used **pip + venv** or a similar dependency manager.
- Written a **basic Flask app** (Week 9 of C1) — `@app.route`, templates, forms.
- Worked with **SQL** at the SELECT/INSERT/JOIN level (Week 10 of C1).
- Written **pytest** unit tests with at least one fixture (Week 11 of C1).
- Used **Git/GitHub** to push branches and open PRs.

If you cannot do any one of those, do that week of C1 first. C16 will not slow down to re-teach them.

---

## What this course is NOT

- **Not a frontend course.** We render server-side HTML in Django (Jinja2 in FastAPI) and serve JSON APIs. For React/Vue/Svelte, see C8.
- **Not a tutorial graveyard.** Every week builds on the previous week's project. By Week 12 you have a single deployable, tested service — not 12 disconnected toy apps.
- **Not a framework comparison.** We use Django *and* FastAPI together because in real life you do too. Django ships the admin, the ORM, and the conventions; FastAPI ships the async APIs and the typed contracts. We teach you when each is right.
- **Not vendor-locked.** No AWS-specific lessons. No Heroku buttons. Everything runs on a $5/month VPS, locally on Docker Compose, or free-tier on Fly.io/Railway. Pick what you like.

---

## Weekly breakdown

| Phase | Weeks | Outcome |
|-------|-------|---------|
| **Phase 1 — HTTP & Django basics** | 01 – 03 | Ship a working Django blog with auth, admin, tests |
| **Phase 2 — Data & the ORM** | 04 – 06 | PostgreSQL, migrations, complex queries, performance |
| **Phase 3 — FastAPI & APIs** | 07 – 09 | A typed, async JSON API consumed by your Django app |
| **Phase 4 — Production** | 10 – 12 | Docker, CI/CD, monitoring, security hardening, capstone |

See [`curriculum/SYLLABUS.md`](curriculum/SYLLABUS.md) for the full week-by-week plan.

---

## How to start

1. Confirm you meet the prerequisites above.
2. Open [`curriculum/SYLLABUS.md`](curriculum/SYLLABUS.md) and read it cover to cover (20 min).
3. Go to [`curriculum/week-01-http-and-the-modern-python-web/`](curriculum/week-01-http-and-the-modern-python-web/) and start.
4. Each week is self-contained: a README orients you, lectures explain the concepts, exercises drill the muscles, challenges stretch you, the quiz checks comprehension, the homework hits real-world scenarios, and the mini-project lets you ship.
5. Push your work to a public GitHub repo. Future-you (and future employers) will thank you.

---

## Weekly cadence

Same as all Code Crunch tracks (~36 hrs/week full-time, scalable down to 9 hrs/week part-time):

| Component | Full-time | Half-time | Part-time |
|-----------|----------:|----------:|----------:|
| Lectures / readings | 6h | 6h | 6h |
| Hands-on exercises | 8h | 4h | 2h |
| Coding challenges | 4h | 2h | 1h |
| Quiz + readings | 3h | 1.5h | 1h |
| Homework problems | 6h | 3h | 1.5h |
| Mini-project | 7h | 3.5h | 1.5h |
| Self-study & review | 2h | 1h | 0.5h |
| **Total / week** | **36h** | **21h** | **13.5h** |
| **Length** | 12 weeks | 20 weeks | ~9 months |

---

## What you ship

By the end of Week 12, your GitHub will contain a single deployable application: **`crunchwriter`** — a multi-author publishing platform with:

- Django admin for editorial staff
- Server-rendered marketing/article pages
- FastAPI for the public read API and webhooks
- PostgreSQL with full-text search
- Redis cache + Celery background image processing
- Stripe-style webhook handling
- JWT auth for the API, session auth for the admin
- Dockerfile + docker-compose + GitHub Actions CI
- Deployed to a $5/mo VPS or free Fly.io tier
- 80%+ test coverage with a fast integration test suite
- Prometheus `/metrics` endpoint and structured JSON logs

That's the thing you point employers at.

---

## Tools we use

Every tool is **free** and **open-source**. No proprietary IDEs, no paid SaaS dependencies for the course itself.

| Tool | Role | Why |
|------|------|-----|
| **Python 3.11+** | Language | Modern speedups, better error messages |
| **Django 5.x** | Full-stack framework | Admin, ORM, templates, batteries-included |
| **FastAPI** | Async API framework | Pydantic-typed, OpenAPI for free |
| **PostgreSQL 16** | Database | Real SQL, real concurrency, JSONB |
| **Redis 7** | Cache / queue | Industry standard |
| **Celery** | Background jobs (Django side) | The canonical Python job runner |
| **Arq** | Background jobs (FastAPI side) | Async-native, Redis-backed |
| **Pytest** | Testing | The standard |
| **Ruff** | Linter / formatter | Fast, replaces black + flake8 |
| **mypy** | Type checking | Catches bugs before runtime |
| **Docker / Compose** | Local dev + deployment | One-command spin-up |
| **GitHub Actions** | CI/CD | Free for public repos |
| **Fly.io / Railway / VPS** | Hosting | Cheap, real, your choice |
| **VS Code** | Editor | Free, great Python support |

---

## License

GPL-3.0. See [LICENSE](LICENSE). You may fork, adapt, teach, and remix. Improvements back to the project are welcomed via PR.

---

## Next track

After C16, the natural progressions are:

- **C15 · Crunch DevOps** — take the service you built and learn to operate it at scale (Kubernetes, observability, IaC).
- **C17 · Crunch Pro Python Advanced** — go deep on async internals, performance, C extensions, and the parts of Python that separate senior from staff.

---

*C16 is part of the Code Crunch open-source curriculum.* [Master catalog ↗](../MASTER-CURRICULUM.md)
