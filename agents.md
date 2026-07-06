## Security: Secrets, Input Handling, and Injection Prevention

### Secrets Management

- **Never store secrets in plaintext**
  - Includes passwords, API keys, tokens, private keys, connection strings
  - Do not hardcode secrets in:
    - Source code
    - Config files
    - Scripts
    - Test data

- **Use secure secret storage**
  - Environment variables (baseline)
  - Secret managers (preferred for production):
    - HashiCorp Vault
    - AWS Secrets Manager / Parameter Store
    - Azure Key Vault
    - GCP Secret Manager

- **Do not log secrets**
  - Never output secrets to logs, console, or error messages
  - Mask sensitive values (e.g., `****`)

- **Do not transmit secrets insecurely**
  - Always use encrypted transport (TLS/HTTPS, SSH)
  - Never send secrets via:
    - Plain HTTP
    - Email
    - Chat logs
    - Query strings in URLs

- **Rotation and scope**
  - Prefer short-lived credentials
  - Use least-privilege access
  - Do not reuse credentials across environments

---

### Input Validation

- **Treat all input as untrusted**
  - Includes user input, API input, file input, environment variables

- **Validate at boundaries**
  - Enforce strict schemas (types, formats, ranges)
  - Reject invalid input early

- **Prefer allowlists over blocklists**
  - Define what is allowed instead of trying to block bad patterns

- **Normalize inputs**
  - Trim whitespace, enforce encoding (UTF-8), canonicalize paths

- **Use strong typing where possible**
  - Avoid loosely typed parsing

---

### Injection Attack Prevention

- **Never directly concatenate untrusted input into:**
  - SQL queries
  - Shell/command execution
  - File paths
  - HTML/JavaScript output
  - LDAP/XPath/NoSQL queries

- **Use safe APIs**
  - Parameterized queries / prepared statements
  - ORM frameworks with built-in protections
  - Escaping/encoding libraries for output contexts

- **Command execution**
  - Avoid shell execution unless absolutely necessary
  - If required:
    - Use argument arrays (not string commands)
    - Validate and sanitize all inputs

- **Output encoding**
  - Encode based on context:
    - HTML encoding for web output
    - JSON encoding for APIs
    - URL encoding for query parameters

---

### Authentication & Authorization Safety

- **Do not:**
  - Implement custom cryptography
  - Store passwords without hashing

- **Always:**
  - Use strong hashing (bcrypt, argon2, scrypt)
  - Enforce secure authentication flows (OAuth, SSO, etc.)
  - Validate authorization on every request

---

### Dependency & Supply Chain Security

- Avoid adding new dependencies unless necessary
- Prefer well-maintained, widely used libraries
- Check for known vulnerabilities before introducing packages
- Do not pull code from untrusted sources

---

### Secure Defaults

- Default to:
  - Deny over allow
  - Least privilege
  - Minimal exposure

- Ensure:
  - Debug modes are disabled in production
  - Sensitive endpoints are protected
  - Configuration does not expose internal details

---

### When to Escalate

Agents must stop and request guidance if:
- A change involves authentication, authorization, or secrets
- Security implications are unclear
- A workaround would weaken security controls

---

### Anti-Patterns (Strictly Forbidden)

- Hardcoding credentials
- Logging sensitive data
- Using plaintext protocols for sensitive data
- Building queries or commands via string concatenation
- Disabling security features to “make it work”
- Trusting client-side validation alone

## Documentation Requirements

Agents must update project documentation when making changes that affect behavior, configuration, setup, deployment, APIs, data models, database schema, user workflows, or troubleshooting steps.

Documentation should be written in the `/docs` directory unless the repository already has a more specific documentation location.

### Documentation Location

Use the following structure when applicable:

- `/docs/README.md`
  - Documentation index and overview

- `/docs/setup.md`
  - Local setup, dependencies, environment variables, and install steps

- `/docs/database.md`
  - Database schema, migrations, tables, relationships, and seed data

- `/docs/features.md`
  - User-facing features and workflows

- `/docs/api.md`
  - API routes, request/response formats, validation rules, and errors

- `/docs/security.md`
  - Security assumptions, secrets handling, validation, authentication, and authorization notes

- `/docs/troubleshooting.md`
  - Common problems, fixes, and operational notes

If a new documentation file is created, update `/docs/README.md` to link to it.

---

### When Documentation Must Be Updated

Agents must update documentation when they:

- Add, remove, or change a feature
- Add, remove, or change database tables, columns, indexes, constraints, or migrations
- Add or modify configuration options
- Add or modify environment variables
- Change setup, install, build, test, or deployment steps
- Add or modify API routes
- Change validation rules
- Change authentication or authorization behavior
- Add security-sensitive behavior
- Add background jobs, scheduled tasks, integrations, or external services
- Change user-facing workflows

---

### Documentation Expectations

Documentation must be:

- Accurate
- Concise
- Written in plain language
- Updated in the same change as the code
- Consistent with the actual implementation
- Useful to someone setting up, maintaining, or troubleshooting the project

Agents must not document planned behavior as if it already exists.

If a feature is partially implemented, documentation must clearly say what is complete and what is not.

---

### Database Documentation

When database changes are made, update `/docs/database.md` with:

- Tables added or changed
- Columns and data types
- Primary keys
- Foreign keys
- Unique constraints
- Check constraints
- Indexes
- Migration/init process
- Example records when helpful

---

### Security Documentation

When security-related changes are made, update `/docs/security.md` with:

- Secrets handling requirements
- Authentication and authorization behavior
- Input validation rules
- Injection-prevention measures
- Transport/security assumptions
- Any known security limitations

Do not include actual secrets, tokens, passwords, private keys, or sensitive production values in documentation.

---

### Agent Workflow

Before finishing a task, agents must check whether documentation should be updated.

If documentation is required, agents must either:

1. Update the relevant file in `/docs`, or
2. Explain why no documentation update was needed

Agents should not leave documentation updates as a future task unless explicitly instructed by a human.
