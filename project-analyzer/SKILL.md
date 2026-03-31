---
name: project-analyzer
description: "Analyzes a project's codebase to generate a comprehensive PROJECT_SUMMARY.md covering tech stack, features, REST endpoints, architecture, data models, integrations, CI/CD, and testing strategy. Uses the assets/report-template.md template for structured output. Use when the user asks to summarize a project, analyze a codebase, document architecture, generate a project overview, or understand what a repository does."
---

# Project Analyzer

Generates a structured `PROJECT_SUMMARY.md` covering tech stack, features, REST endpoints, architecture, data models, integrations, CI/CD, and testing.

## Workflow

### 1. Initial Exploration

- Use `list_directory` and `glob` to map the top-level folder structure.
- Identify config files to determine the stack:

```bash
glob('**/package.json') glob('**/requirements.txt') glob('**/build.gradle')
glob('**/go.mod') glob('**/Cargo.toml') glob('**/pyproject.toml')
```

### 2. Architecture Deep Dive

- Delegate to `codebase_investigator` with:
  > "Analyze the project to understand its architecture, core features, and tech stack. Identify all REST endpoints and key services."
- If `codebase_investigator` returns incomplete results, fall back to manual exploration of `src/`, `app/`, `lib/` directories.

### 3. Feature & API Discovery

- Search for route definitions, controllers, and service layers:

```bash
glob('**/*.controller.ts') glob('**/routes/**') glob('**/*.router.ts')
glob('**/views.py') glob('**/*Controller.java')
```

- Extract REST endpoints with methods and descriptions.

### 4. Infrastructure & Data

- Database models: `glob('**/models/**')`, `glob('**/schema.prisma')`, `glob('**/entities/**')`.
- External integrations: search for SDK imports (Stripe, AWS, SendGrid, etc.).
- CI/CD: check `.github/workflows/`, `Jenkinsfile`, `docker-compose.yml`.

### 5. Testing Analysis

- Locate test directories: `glob('**/tests/**')`, `glob('**/__tests__/**')`, `glob('**/*.spec.ts')`.
- Identify test frameworks from config files and dev dependencies.

### 6. Validation Checkpoint

Before generating the report, confirm coverage:
- [ ] Tech stack identified (languages, frameworks, libraries)
- [ ] REST endpoints enumerated (or confirmed none exist)
- [ ] Architecture pattern determined
- [ ] Data models and external integrations listed
- [ ] CI/CD and testing strategy documented

If any section is empty, re-investigate the relevant directories before proceeding.

### 7. Report Generation

- Use `assets/report-template.md` (relative to this skill directory) to create `PROJECT_SUMMARY.md` in the project root.
- Keep descriptions technical yet accessible.

## Assets

- `assets/report-template.md`: Standard template for the project summary.
