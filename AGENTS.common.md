# AGENTS.md

## Project Purpose

Briefly describe what this repository does and who uses it.

## Project Structure

* `src/` contains application/source code.
* `scripts/` contains operational scripts.
* `tests/` contains automated tests.
* `docs/` contains setup, security, and troubleshooting documentation.
* `samples/` contains sanitized examples only.

## Commands

Use these commands when applicable:

* Setup:
* Test:
* Lint:
* Format:
* Build:

Do not invent commands. If a command is missing, inspect the repo and explain what is available.

## Change Rules

* Prefer small, reviewable changes.
* Do not perform unrelated cleanup.
* Preserve existing behavior unless the task explicitly asks for a behavior change.
* Show the intended files and approach before large changes.
* After changes, summarize modified files and validation performed.

## Security Rules

* Never hardcode passwords, API keys, tokens, private keys, or connection strings.
* Never commit real `.env` files, logs with secrets, exported credentials, or production config.
* Use `.env.example` with placeholder values only.
* Do not weaken authentication, authorization, TLS, logging protections, or validation without explicit approval.
* Mask sensitive values in logs and examples.
* Treat all input as untrusted unless explicitly proven otherwise.
* Validate input at system boundaries.
* Prefer allowlists over blocklists.
* Use parameterized queries, prepared statements, safe APIs, and context-appropriate output encoding.
* Avoid shell execution unless absolutely necessary.
* If command execution is required, use argument arrays instead of string commands and validate all inputs.
* Use least privilege for credentials, service accounts, permissions, and access scopes.

## Strictly Forbidden Security Anti-Patterns

Agents must not do any of the following:

* Hardcode credentials.
* Log sensitive data.
* Use plaintext protocols for sensitive data.
* Build queries or commands through string concatenation with untrusted input.
* Disable security features to make something work.
* Trust client-side validation alone.
* Store passwords without proper hashing.
* Implement custom cryptography.
* Pull code from untrusted sources.
* Add unnecessary dependencies.
* Document actual secrets, tokens, passwords, private keys, or sensitive production values.

## Security Escalation

Agents must stop and request guidance before making changes that:

* Modify authentication or authorization behavior.
* Add, remove, expose, rotate, or change how secrets are handled.
* Weaken an existing security control.
* Introduce uncertainty around access control, data exposure, or credential handling.
* Require a workaround that could reduce security.

## Documentation Requirements

Agents must update project documentation when making changes that affect behavior, configuration, setup, deployment, APIs, data models, database schema, user workflows, or troubleshooting steps.

Documentation should be written in the `/docs` directory unless the repository already has a more specific documentation location.

## Documentation Location

Use the following structure when applicable:

* `/docs/README.md`

  * Documentation index and overview.

* `/docs/setup.md`

  * Local setup, dependencies, environment variables, and install steps.

* `/docs/database.md`

  * Database schema, migrations, tables, relationships, and seed data.

* `/docs/features.md`

  * User-facing features and workflows.

* `/docs/api.md`

  * API routes, request and response formats, validation rules, and errors.

* `/docs/security.md`

  * Security assumptions, secrets handling, validation, authentication, and authorization notes.

* `/docs/troubleshooting.md`

  * Common problems, fixes, and operational notes.

If a new documentation file is created, update `/docs/README.md` to link to it.

## When Documentation Must Be Updated

Agents must update documentation when they:

* Add, remove, or change a feature.
* Add, remove, or change database tables, columns, indexes, constraints, or migrations.
* Add or modify configuration options.
* Add or modify environment variables.
* Change setup, install, build, test, or deployment steps.
* Add or modify API routes.
* Change validation rules.
* Change authentication or authorization behavior.
* Add security-sensitive behavior.
* Add background jobs, scheduled tasks, integrations, or external services.
* Change user-facing workflows.

## Documentation Expectations

Documentation must be:

* Accurate.
* Concise.
* Written in plain language.
* Updated in the same change as the code.
* Consistent with the actual implementation.
* Useful to someone setting up, maintaining, or troubleshooting the project.

Agents must not document planned behavior as if it already exists.

If a feature is partially implemented, documentation must clearly say what is complete and what is not.

## Database Documentation

When database changes are made, update `/docs/database.md` with:

* Tables added or changed.
* Columns and data types.
* Primary keys.
* Foreign keys.
* Unique constraints.
* Check constraints.
* Indexes.
* Migration or initialization process.
* Example records when helpful.

## Security Documentation

When security-related changes are made, update `/docs/security.md` with:

* Secrets handling requirements.
* Authentication and authorization behavior.
* Input validation rules.
* Injection-prevention measures.
* Transport and security assumptions.
* Any known security limitations.

Do not include actual secrets, tokens, passwords, private keys, or sensitive production values in documentation.

## Validation

Before finishing, run the relevant tests or explain why they could not be run.

If linting, formatting, build, or type-check commands exist, run the relevant checks for the change or explain why they were not run.

## Agent Workflow

Before modifying files:

* Identify the files that need to change.
* Explain the reason for the change.
* Avoid unrelated cleanup.
* Preserve existing behavior unless the task explicitly requires changing it.

Before finishing a task:

* Check whether documentation should be updated.
* Update the relevant file in `/docs` when documentation is required.
* If documentation is not updated, explain why no documentation update was needed.
* Summarize what changed.
* List files changed.
* List tests or validation performed.

Agents should not leave documentation updates as a future task unless explicitly instructed by a human.
