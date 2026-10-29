# Accounts Receivable Tracking API

A planned Java backend for customer receivables, partial payments and SQL reporting, with a staged path toward reliable messaging and richer financial operations.

**Current status: specification only. No application, build, migrations, tests, CI workflow or deployment has been implemented or verified. Current implementation target: Phase 1.**

One company, USD only, REST API without a frontend. The application records money received elsewhere; it does not execute payments or issue tax invoices. Use the code `USD` in API/data; `$` is presentation only. Customer records have name and optional email; there is no jurisdiction-specific tax identifier.

## Start here

1. Read [AGENTS.md](AGENTS.md) for the collaboration contract.
2. Read the [documentation index](docs/README.md), [phase roadmap](docs/roadmap.md) and [Phase 1 scope](docs/scope.md).
3. Read [current progress](docs/development/progress.md) before choosing work.
4. Implement only the next requested [Phase 1 milestone](docs/development/milestones.md).

Conversation may be in Polish. All implementation artifacts must be in English: code, identifiers, comments, API messages, tests, documentation, configuration labels and commit messages.

## Three phases, one evolving product

| Phase | Result | Intended discussion depth |
| --- | --- | --- |
| **1 — Core** | Customers, receivables, partial payments, SQL balances/aging, roles, tests and repeatable demo | Strong junior |
| **2 — Async reliability** | PaymentRecorded → outbox → Kafka → durable payment confirmation; duplicates and recovery | Junior/mid |
| **3 — Concept** | Allocations across receivables, full reversals, request idempotency and collection contacts | Mid-oriented design |

These labels describe scope/learning targets, not guaranteed seniority or recruitment outcomes. Phase 1 is independently portfolio-ready when its acceptance checks pass. Later phases are not required before applying.

## Planned Phase 1 stack

Java 25, Spring Boot 4.x, Spring MVC, Spring Security, Spring Data JPA/Hibernate, Spring JDBC, PostgreSQL, Flyway, Bean Validation, JUnit Jupiter, AssertJ, selective Mockito, Testcontainers, MockMvc, OpenAPI/Swagger UI, Maven Wrapper, Docker Compose, GitHub Actions and Actuator.

Phase 2 adds Spring Kafka, a broker, Kafka Testcontainers and two tables. See [architecture](docs/architecture.md) and [Phase 2](docs/phase-2.md). Planned dependencies are not evidence of implementation.

## Editable database model

- [draw.io — three pages, one complete schema per phase](docs/diagrams/accounts-receivable-tracking.drawio)
- [Phase 1 preview — 4 tables](docs/diagrams/schema-v1.png)
- [Phase 2 preview — 6 tables](docs/diagrams/schema-v2.png)
- [Phase 3 preview — 10-table conceptual target](docs/diagrams/schema-v3.png)
- [Core database contract](docs/database.md), [Phase 2 additions](docs/phase-2.md), [Phase 3 concepts and migration](docs/phase-3-concept.md)

Blue/gray tables are core, amber tables enter in Phase 2, violet tables enter in Phase 3, and the changed Phase 3 payments table is marked explicitly. Phase 3 replaces the direct payment-to-receivable link with allocations; it is not a schema to create during Phase 1.

## Delivery and completion

Phase 1 has [30 bounded milestones](docs/development/milestones.md), each with acceptance checks and a learning question. They are work sessions, not a promise of 30 equal calendar days. [Phase 1 acceptance](docs/acceptance.md) defines the application-ready stop point.

Phase 2 has a separate 10-slice outline and reliability gate. Phase 3 remains conceptual until a concrete need is selected. The [roadmap](docs/roadmap.md) explains how to choose based on learning goals and recruitment feedback without repeatedly starting over.

## Running and testing

Not available yet. Verified commands, actual dependency versions and observed results will be recorded as implementation proceeds. Document/diagram checks do not substitute for application tests.

## Repository identity

- Directory/repository: `accounts-receivable-tracking-api`
- Maven group: `dev.bartmilo`
- Maven artifact: `accounts-receivable-tracking-api`
- Java base package: `dev.bartmilo.receivables`

No Git repository or remote has been created by the documentation tasks.
