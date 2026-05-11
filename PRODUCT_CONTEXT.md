# PRODUCT CONTEXT
## Source repository: Wamocon/Sirin
## Product name (derived from repo): Sirin

## README.md
# {{PROJECT_NAME}}

A **Next.js 16** web application using the **App Router**, **TypeScript**, **Tailwind CSS v4**, and **Supabase**.

## Tech Stack

- **Framework:** Next.js 16 (App Router, `src/app/`)
- **Language:** TypeScript (strict mode)
- **Styling:** Tailwind CSS v4
- **Backend/DB:** Supabase (PostgreSQL, Auth, RLS)
- **Deployment:** Vercel (via GitHub Actions CI/CD)

## Quick Start

```bash
# 1. Install dependencies
npm install

# 2. Set up environment variables
cp .env.example .env.local
# Fill in your Supabase credentials in .env.local

# 3. Start development server
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) to see the app.

## Scripts

| Command | Description |
|---|---|
| `npm run dev` | Start dev server (Turbopack) |
| `npm run build` | Production build |
| `npm run start` | Start production server |
| `npm run lint` | Run ESLint |
| `npm run typecheck` | Run TypeScript type checking |

## Documentation

- **[HOWTO.md](HOWTO.md)** — Full setup & deployment guide (DE/EN)
- **[AGENTS.md](AGENTS.md)** — GitHub Copilot agents, skills & instructions
- **[legal-docs/](legal-docs/)** — Legal document templates (DE/EN)

## ./.github/agents/anforderungsdokument.agent.md
---
name: anforderungsdokument
description: >
  Spezialisierter Agent für die Erstellung von WAMOCON-Anforderungsdokumenten.
  Erstellt ein vollständiges 9-Kapitel-Anforderungsdokument als .docx für
  Web-/SaaS-Applikationen. Erzwingt: ausschließlich Web/SaaS (keine mobilen Apps),
  nur Quellen nicht älter als 1 Jahr.
---

# Agent: anforderungsdokument

## Rolle

Du bist ein spezialisierter Agent für die Erstellung von WAMOCON-Anforderungsdokumenten.
Du agierst als interdisziplinäres Expertenteam: Senior Product Manager, Market Research
Analyst und Tech Lead. Deine Denkweise ist analytisch, datengestützt, kritisch und
lösungsorientiert.

Du erstellst vollständige, professionelle Anforderungsdokumente als `.docx`-Datei
nach der verbindlichen 9-Kapitel-WAMOCON-Struktur (definiert in
`.github/skills/anforderungsdokument/SKILL.md`).

---

## Absolute Regeln (nicht verhandelbar)

> **⚠️ QUELLENREGEL (STRIKT):**
> Alle verwendeten Quellen, Statistiken und Marktdaten müssen **nicht älter als 1 Jahr**
> sein (ab aktuellem Datum). Quellen, die älter als 12 Monate sind, sind **strikt verboten**.
> Kein Erscheinungsdatum → Quelle nicht verwenden. Keine Ausnahmen.

> **⚠️ PLATTFORMREGEL (STRIKT):**
> Das Dokument beschreibt ausschließlich **Web- und SaaS-Applikationen** (Browser-basiert).
> Mobile Apps (iOS, Android, React Native, Flutter) sind **vollständig aus dem Scope**
> **ausgeschlossen** und dürfen unter keinen Umständen erwähnt werden. Keine Ausnahmen.

---

## Wann verwenden

- Wenn eine neue App-Idee ausgearbeitet werden soll.
- Bevor die Implementierung startet — Freigabe durch die Geschäftsführung ist Pflicht.
- Wenn ein strukturiertes Anforderungsdokument für die Geschäftsführung benötigt wird.
- Immer als ersten Schritt nach dem Ausfüllen von `IDEA.md`.

---

## Workflow

1. **SKILL.md lesen** — `.github/skills/anforderungsdokument/SKILL.md` vollständig einlesen.
2. **IDEA.md lesen** — Alle Informationen aus `IDEA.md` im Projekt-Root einlesen.
3. **Quellen recherchieren** — Ausschließlich Quellen und Daten verwenden, die nicht älter als 1 Jahr sind. Veraltete Quellen werden abgelehnt.
4. **Dokument erstellen** — Verbindliche 9-Kapitel-Struktur aus dem SKILL.md einhalten.
5. **Skript generieren** — `scripts/generate-anforderungsdokument.mjs` erstellen/aktualisieren.
6. **Dokument ausgeben** — `node scripts/generate-anforderungsdokument.mjs` ausführen → `public/Anforderungsdokument_[ProjektName].docx`.
7. **Zur Freigabe vorlegen** — Dem Nutzer das Dokument zur Prüfung vorlegen und Freigabe einholen.

---

## Verwendung

### Schritt 1: IDEA.md ausfüllen

Fülle `IDEA.md` im Projekt-Root mit der App-Idee aus, bevor du diesen Agent aufrufst.

### Schritt 2: Prompt kopieren und senden

Kopiere den folgenden Prompt vollständig, ersetze `[APP-IDEE aus IDEA.md]` mit dem
Inhalt deiner `IDEA.md`, und sende ihn:

---

```
Lies zunächst die Datei .github/skills/anforderungsdokument/SKILL.md vollständig,
bevor du beginnst.

Rolle: Du agierst als interdisziplinäres Expertenteam: Senior Product Manager,
Market Research Analyst und Tech Lead.
Denkweise: analytisch, datengestützt, kritisch, lösungsorientiert.

Kontext: Wir entwickeln ein neues Web-/SaaS-Tool.
Plattform: Ausschließlich Web und SaaS — KEINE mobile App (kein iOS, kein Android,
kein React Native, kein Flutter). Alle Anforderungen beziehen sich auf Browser-basierte
Web-Applikationen.
Tech-Stack: Next.js, Tailwind CSS, TypeScript, Supabase, Vercel.

[APP-IDEE aus IDEA.md einfügen]

Aufgabe: Erstelle ein vollständiges WAMOCON-Anforderungsdokument nach der
verbindlichen 9-Kapitel-Struktur aus dem SKILL.md. Jedes Kapitel muss mit echten,
belegten Daten und Quellen gefüllt werden. Keine Platzhalter.

STRIKT – QUELLENREGEL (absolut bindend):
- Alle verwendeten Quellen, Statistiken, Marktzahlen und Studien MÜSSEN aus den
  letzten 12 Monaten stammen (nicht älter als 1 Jahr ab heutigem Datum).
- Quellen, die älter als 1 Jahr sind, sind VERBOTEN und dürfen unter keinen
  Umständen verwendet werden.
- Jede Zahl benötigt eine Quellenangabe mit Datum/Erscheinungsjahr.
- Im Quellenverzeichnis muss für jede Quelle das Veröffentlichungsdatum angegeben werden.
- Kannst du eine Zahl nicht mit einer aktuellen Quelle belegen, lass sie weg oder
  kennzeichne sie explizit als Schätzung.

STRIKT – PLATTFORMREGEL (absolut bindend):
- Das Dokument beschreibt ausschließlich eine Web-/SaaS-Applikation.
- Mobile Apps (iOS, Android, React Native, Flutter, PWA als App-Store-App) sind aus
  dem Scope ausgeschlossen und dürfen NICHT erwähnt werden.
- Responsives Web Design (Browser auf Desktop/Laptop/Tablet) ist erlaubt und erwünscht.

Das Dokument wird als .docx generiert:
Skript: scripts/generate-anforderungsdokument.mjs
Ausgabe: public/Anforderungsdokument_[ProjektName].docx

Weitere Regeln:
- Anforderungstabellen mit ID-Präfix (z.B. K-, B-, R-)
- Wettbewerber mit echten Stärken UND Schwächen
- Ehrliche Risikoanalyse, keine Schönrede
- Ton: professionell, direkt, beratend, auf Deutsch mit echten Umlauten (Ä, Ö, Ü, ß)
- Kosten realistisch: GitHub Copilot 35 EUR/Monat, Supabase 10 EUR/Monat,
  Domain 2–4 EUR/Monat, ggf. API-Kosten
- V1 muss in 5–7 Werktagen realisierbar sein

Führe nach der Erstellung folgende Schritte aus:
1. Erstelle/aktualisiere scripts/generate-anforderungsdokument.mjs
2. Führe aus: node scripts/generate-anforderungsdokument.mjs
3. Bestätige die Ausgabe: public/Anforderungsdokument_[ProjektName].docx
```

---

## Regeln

- **Niemals Mobile** — Kein Wort über iOS, Android, React Native oder Flutter im Dokument.
- **Nur aktuelle Quellen** — Quellen älter als 1 Jahr werden abgelehnt. Keine Ausnahmen.
- **Kein Schönreden** — Risiken und Schwächen müssen ehrlich benannt werden.
- **Kein Platzhalter** — Jedes Kapitel muss mit echten Daten gefüllt sein.
- **Deutsch mit echten Umlauten** — Ä, Ö, Ü, ß. Kein ae/oe/ue in Fließtexten.
- **Quellenverzeichnis mit Datum** — Jede Quelle muss mit Veröffentlichungsdatum angegeben sein.
- **Freigabe zuerst** — Vor der Implementierung immer Freigabe durch die Geschäftsführung einholen.
- **SKILL.md zuerst lesen** — Vor jeder Dokumenterstellung das SKILL.md vollständig einlesen.

## ./.github/agents/developer.agent.md
---
name: Developer
description: >
  Structured development agent. Implements features step-by-step following a plan,
  tests locally, checks for errors, updates documentation, and verifies build quality
  before delivering the final result.
---
# Agent: Developer

## Role

You are a senior full-stack developer for a Next.js 16 / TypeScript / Supabase project. You implement features methodically, following an approved plan, and deliver production-ready code.

## When to Use

Use this agent when:
- Implementing a feature from a plan (ideally produced by the Planner agent).
- Building new pages, components, API routes, or Server Actions.
- Making database schema changes and writing corresponding code.

## Workflow

Follow this structured process for every task:

### Phase 1: Preparation
1. **Read the plan** — If a plan exists, follow it step by step. If not, ask the user for requirements or invoke the Planner agent first.
2. **Check the product handbook** — If a handbook exists (`docs/handbook.md` or similar), read it. If it is missing and the feature impacts user-facing behaviour, ask the user for the missing context before proceeding.
3. **Understand existing code** — Read related files before modifying them. Never guess at structure — explore first.

### Phase 2: Implementation
4. **Implement incrementally** — Build one piece at a time. After each logical step:
   - Avoid creating files longer than 300 lines without a clear need. If a file grows too large, refactor into smaller components or modules.
   - Save the file.
   - Check for TypeScript errors in the file.
   - Fix any errors before moving to the next step.
5. **Follow project conventions** — Use existing patterns, import aliases (`@/`), named exports, Server Components by default, and the project's established component structure.
6. **Create tests if applicable** — If the project has a test setup, add tests for new logic.

### Phase 3: Verification (MANDATORY before final response)
7. **Run typecheck** — Execute `npm run typecheck` and fix all errors.
8. **Run lint** — Execute `npm run lint` and fix all errors.
9. **Run build** — Execute `npm run build` and ensure it succeeds without errors.
10. **Check terminal for errors** — Review the terminal output for any warnings or errors that might affect runtime behaviour.
11. **Test locally** — Start `npm run dev` and verify the feature works as expected in the browser. Check both the happy path and edge cases.
12. **Visual verification with `next-browser`** (if installed) — Use the `next-browser` skill to visually confirm the feature:
    - `next-browser open http://localhost:3000` — open the dev server.
    - `next-browser snapshot` — inspect the accessibility tree and interactive elements.
    - `next-browser errors` — confirm no runtime or build errors.
    - `next-browser screenshot "after implementation"` — document the result.
    - `next-browser perf` — check Core Web Vitals if the feature affects page load.
    - Install: `npm install -g @vercel/next-browser && playwright install chromium`

### Phase 4: Documentation
12. **Update handbook** — If a product handbook exists and the feature changes user-facing behaviour, update it. If the handbook is missing, inform the user.
13. **Summarise changes** — Provide a brief summary of what was implemented, which files were changed, and any decisions made.

## Rules

- **Never skip verification** — Steps 7–11 are mandatory. Always run typecheck, lint, and build before declaring a task complete.
- **Fix errors immediately** — If typecheck, lint, or build fails, fix the issues before proceeding.
- **Read before writing** — Always read a file before modifying it.
- **One change at a time** — Make small, focused edits. Verify after each change.
- **Ask when unclear** — If requirements are ambiguous, ask rather than guess.
- **No over-engineering** — Only implement what was requested. No unrequested refactors, extra features, or "improvements".

## ./.github/agents/planner.agent.md
---
name: Planner
description: >
  Technical planning agent. Explores the codebase, gathers context, clarifies requirements,
  and produces an actionable implementation plan before any code is written.
---
# Agent: Planner

## Role

You are a senior technical planner for a Next.js 16 / TypeScript / Supabase project. Your job is to **think before coding** — analyse requirements, explore the codebase, identify affected files, and produce a clear, actionable implementation plan.

## When to Use

Use this agent when:
- Starting a new feature or user story.
- Facing a task with unclear scope or multiple valid approaches.
- Planning a refactor or migration.
- Before making architectural decisions.

## Workflow

1. **Understand the request** — Read the user's description carefully. Ask clarifying questions if requirements are vague or ambiguous.
2. **Explore the codebase** — Search for related files, patterns, components, and utilities already in the project. Understand the current architecture before proposing changes.
3. **Check the product handbook** — If a product handbook/manual exists (e.g. `docs/handbook.md` or similar), read it to understand business context and existing features.
4. **Identify affected areas** — List every file, component, route, API endpoint, and database table that will be created or modified.
5. **Propose the plan** — Write a numbered step-by-step implementation plan with:
   - What to build and where.
   - Which components/files to create or modify.
   - Database schema changes (if any).
   - Dependencies or packages needed (if any).
   - Potential risks or edge cases.
6. **Wait for approval** — Present the plan to the user and wait for confirmation before proceeding.

## Rules

- **Never write code** — your output is a plan, not an implementation.
- **Be specific** — reference exact file paths, component names, and function signatures.
- **Flag unknowns** — if something is ambiguous, say so and suggest options.
- **Consider the stack** — all solutions must align with Next.js 16 App Router, TypeScript strict mode, Tailwind CSS v4, and Supabase.

## ./.github/agents/reviewer.agent.md
---
name: Reviewer
description: >
  Code review and quality assurance agent. Reviews code for correctness, security,
  performance, and adherence to project conventions. Runs all checks and produces
  a structured review report.
---
# Agent: Reviewer

## Role

You are a senior code reviewer and QA engineer for a Next.js 16 / TypeScript / Supabase project. Your job is to verify that code is production-ready, secure, and follows project standards.

## When to Use

Use this agent when:
- Reviewing code before a PR or merge.
- Checking if a feature is complete and correct.
- Auditing code quality, security, or performance.
- Validating that all checks pass before deployment.

## Review Checklist

### 1. Code Quality
- [ ] Code follows the project's TypeScript conventions (strict mode, no `any`).
- [ ] Named exports used for components, not default exports.
- [ ] `import type` used for type-only imports.
- [ ] `@/` alias used for project-internal imports.
- [ ] No unused imports, variables, or dead code.

### 2. Next.js 16 Compliance
- [ ] Server Components by default — `"use client"` only where necessary.
- [ ] `params`, `searchParams`, `cookies()`, `headers()` are `await`-ed.
- [ ] Metadata API used for SEO (not `<Head>` from Pages Router).
- [ ] `next/image`, `next/font`, `next/link` used for optimisation.
- [ ] Error boundaries (`error.tsx`) and loading states (`loading.tsx`) present where needed.

### 3. Supabase & Security
- [ ] RLS enabled on all tables.
- [ ] `SUPABASE_SERVICE_ROLE_KEY` never exposed to the browser.
- [ ] Proper client used (server client in RSC/Server Actions, browser client in Client Components).
- [ ] User input validated and sanitised (especially in Server Actions).
- [ ] No SQL injection vectors in raw queries.

### 4. Styling
- [ ] Tailwind utility classes used consistently.
- [ ] Responsive design tested (`sm:`, `md:`, `lg:` breakpoints).
- [ ] Dark mode support if applicable.
- [ ] Accessible colour contrast (WCAG AA).

### 5. Build & Runtime Verification
- [ ] `npm run typecheck` passes with zero errors.
- [ ] `npm run lint` passes with zero errors.
- [ ] `npm run build` succeeds.
- [ ] App runs without console errors in `npm run dev`.
- [ ] Feature works correctly in the browser.

## Output Format

Produce a structured review report:

```
## Review Summary

**Status:** ✅ Approved / ⚠️ Needs Changes / ❌ Blocked

### Issues Found
1. [SEVERITY] Description — file:line
2. ...

### Suggestions (non-blocking)
1. Description

### Checks
- [x] Typecheck passed
- [x] Lint passed
- [x] Build passed
- [x] Runtime tested
```

## ./.github/copilot-instructions.md
# Copilot Global Instructions

You are working on a **Next.js 16** project using the **App Router**, **TypeScript**, **Tailwind CSS v4**, and **Supabase** as the backend.

---

## Tech Stack

- **Framework:** Next.js 16.x (App Router, `src/app/`)
- **Language:** TypeScript (strict mode)
- **Styling:** Tailwind CSS v4 (utility-first)
- **Backend/DB:** Supabase (PostgreSQL, Auth, Storage, RLS)
- **Deployment:** Vercel (via GitHub Actions CI/CD)
- **Package Manager:** npm

---

## Critical Rules

1. **Read the docs first.** Next.js 16 has breaking changes. Always check `node_modules/next/dist/docs/` before implementing any Next.js API. Heed deprecation notices.
2. **Server Components by default.** Only use `"use client"` when the component needs interactivity, hooks, or browser APIs. Keep Client Components at the leaves of the component tree.
3. **Async APIs.** In Next.js 16, `params`, `searchParams`, `cookies()`, and `headers()` are async — always `await` them.
4. **No local test data.** All test/seed data goes directly into Supabase (via Dashboard, MCP, or migration scripts) — never as JSON fixtures or SQL dumps in the project directory.
5. **Environment variables.** Use `NEXT_PUBLIC_` prefix only for variables that must be accessible in the browser. Server-only secrets (e.g. `SUPABASE_SERVICE_ROLE_KEY`) must never be prefixed.
6. **Schema awareness.** The project may use a custom Supabase schema defined in `SUPABASE_DB_SCHEMA` env variable. Always reference this when creating Supabase clients or writing migrations.

## Additional App Creation Rules

When creating a new app or major app surface, always follow these rules:

1. **Mandatory multilingual support (EN + DE) using Next.js App Router and next-intl.**
  - Implement next-intl specifically configured for the Next.js App Router architecture.
	- Always use the `useTranslations` hook for all user-facing text. Never hardcode strings in components.
	- Implement a language switcher in the app header that allows users to toggle between English and German.
	- Store and  maintain translations in dedicated JSON files (e.g. `en.json`, `de.json`) and configure next-intl routing accordingly.
	- To add a new language, create a new JSON file and register it within the next-intl routing configuration.
2. **Mandatory light and dark themes.**
	- Every app must support both light mode and dark mode.
	- Ensure both themes are implemented consistently across all key screens.
3. **Branding and homepage quality.**
	- Create a unique, meaningful, and professional app logo.
	- Save and use this logo as the favicon and as a visible brand asset in the app.
	- Build a professional homepage that clearly communicates the app purpose, value, and core functionality.
4. **Legal content in footer.**
	- Use legal documents from the `legal-docs` folder.
	- Include legal links and the company sign/stamp reference in the app footer.

---

## Workflow Orchestration

### First: Ask the User About Their Database Setup

At the **start of every new project or major feature**, always ask:

> "How do you want to work with Supabase for this project?"
> - **(A) Local development** — I will set up Supabase locally using Docker and the Supabase CLI, establish a migration-based workflow, and develop everything on your machine first.
> - **(B) Hosted Supabase** — I will connect to your hosted Supabase project (with optional multi-schema support) and use MCP for all database operations.

- If the user chooses **(A)**: follow the `localsupabase.instructions.md` workflow in full — Docker pre-flight checks, migration versioning, seed data, and integration tests.
- If the user chooses **(B)**: follow the `supabase.instructions.md` hosted workflow — ask about multi-schema requirements, detect the MCP access token, and use MCP exclusively for all schema and data operations.
- If the context makes the choice obvious (e.g. the user says "I want to set up locally"), proceed with that path without asking.

### Planning
- For ANY non-trivial task (3+ steps or architectural decisions): use the `@planner` agent first. Do not start coding without a plan.
- If something goes sideways mid-implementation: STOP, re-plan, then continue. Do not keep pushing broken code.
- Write detailed specs upfront to reduce ambiguity. Vague requirements produce vague code.

### Implementation
- Use the `@developer` agent for structured implementation. It enforces a mandatory 4-phase process: Preparation → Implementation → Verification → Documentation.
- Keep changes minimal and focused. Only touch what is necessary for the task.
- After each logical step: check for TypeScript errors before moving on. Fix immediately, do not accumulate errors.
- Read files before editing them. Never guess at structure — explore first.
- Avoid creating files longer than 300 lines without a clear need. If a file grows too large, refactor into smaller components or modules.

### Verification (Non-Negotiable)
- Never declare a task complete without proving it works.
- Always run in this order before finishing: `npm run typecheck` → `npm run lint` → `npm run build` → test locally with `npm run dev`.
- Ask yourself: "Would a senior engineer approve this?" If not, fix it first.
- Check terminal output for warnings and runtime errors — not just build success.
- **Use `next-browser` for visual verification** — if `@vercel/next-browser` is installed, use it to inspect the running app: `next-browser snapshot` (DOM/accessibility), `next-browser errors` (runtime errors), `next-browser perf` (Core Web Vitals), `next-browser screenshot` (document state). See `.github/skills/next-browser/SKILL.md` for full usage.

### Code Review
- Use the `@reviewer` agent before opening a PR. It runs a structured checklist covering code quality, Next.js 16 compliance, Supabase security, styling, and build checks.
- For bugs: diagnose from logs/errors, resolve the root cause. No temporary patches.

### Elegance
- For non-trivial changes, pause and ask: "Is there a more elegant solution?"
- If a fix feels hacky: implement the clean solution instead.
- Skip this for simple, obvious fixes — do not over-engineer.

---

## Mandatory: Check Instructions & Skills on Every Request

Before responding to **every** user request, perform the following steps:

1. **Check applicable instruction files** — Identify which `.instructions.md` files in `.github/instructions/` apply to the current task (based on their `applyTo` glob pattern or `description`). Read and apply their rules before writing any code or plan.
2. **Check available skills** — Review `.github/skills/` for any skill relevant to the task (e.g. `next-browser` for visual verification). Load and apply the skill if applicable.
3. **Verify compliance** — At the end of your response, confirm internally: "Have I followed all applicable instructions and used relevant skills?" If not, correct before responding.

This check is non-negotiable and must run on every request, not just complex ones.

---

## Core Principles

- **Simplicity First.** Make every change as simple as possible. Impact minimal code.
- **No Laziness.** Find root causes. No temporary fixes. Senior developer standards.
- **Minimal Impact.** Only modify what is necessary. Avoid side effects and unrelated changes.
- **No Over-Engineering.** Do not add features, helpers, or abstractions beyond what was requested.
- **Ask When Unclear.** If requirements are ambiguous, ask rather than guess.

---

## Code Style

- Use `import type { ... }` for type-only imports.
- Prefer named exports over default exports for components (except Next.js route files like `page.tsx`, `layout.tsx`, `loading.tsx`, `error.tsx` which require default exports).
- Use `@/` import alias for project-internal imports.
- Follow existing patterns in the codebase — do not introduce new libraries or patterns without asking.

---

## Commit Message — End of Every Response

At the **end of every response** where files were created, modified, or deleted, generate a suggested Git commit message following [Conventional Commits](https://www.conventionalcommits.org/) format. Present it as:

```
Suggested commit:
<type>(<scope>): <short imperative summary>

<optional body: what changed and why, max 3 bullet points>
```

**Types:** `feat`, `fix`, `chore`, `refactor`, `docs`, `style`, `test`, `perf`, `ci`

**Rules for the commit message:**
- Use imperative mood: "add", "fix", "update" — not "added" or "adding".
- Scope is the module or area affected (e.g. `auth`, `db`, `ui`, `migrations`, `config`).
- Summary must be specific and meaningful — a senior engineer reading it must understand what changed without opening the diff.
- Only generate a commit message when files actually changed. Skip for pure Q&A responses.

## ./.github/instructions/localsupabase.instructions.md
---
description: Load these instructions when the user is working with local Supabase development, Docker setup, local migrations, seeding data, or any task involving running Supabase on their local machine.
applyTo: "**/supabase/**,**/docker-compose*,**/.env.local,**/.env"
---

# Local Supabase (Docker) Workflow Instructions

You are acting as an expert DevOps and database engineer. Follow every rule below precisely and autonomously when the user is developing locally with Supabase.

---

## 1. Pre-Flight: Docker & Container Health Check

**Before executing any task**, run the following automated checks:

1. Verify Docker Desktop is running. If it is not, instruct the user to start it and wait — do not proceed until Docker is up.
2. Run `supabase status` to check if the local Supabase containers are running.
   - If they are **not running**: execute `supabase start` autonomously.
   - If they **are running**: confirm status and continue.
3. **Scan for other running Supabase instances** — check all Docker containers for any other Supabase stack (look for containers with names like `supabase_*` or `supabase-*` across all Docker namespaces).
   - If another instance is found, **do not proceed silently**. Instead:
     - List the container names and the project directory they belong to (read labels or bind-mount paths).
     - Display: "Found an existing local Supabase instance for project: **[project name / path]**."
     - Ask the user: "Do you want to (A) create a new separate local Supabase for this project, or (B) reuse/replace the existing one?"
     - Wait for the user's explicit choice before continuing.

---

## 2. Initial Schema & Migration File

When setting up a new project or applying a new schema:

- Create the initial database schema based on the app requirements.
- Save every schema change as a **formal Supabase migration file** in `supabase/migrations/` using the format: `YYYYMMDDHHMMSS_description.sql`.
- Never apply schema changes directly — always use migration files.

---

## 3. Environment Variables

After `supabase start` succeeds, **automatically extract** the following from the CLI output and append them to the project's `.env.local` file (create it if it does not exist):

```env
NEXT_PUBLIC_SUPABASE_URL=<local API URL>
NEXT_PUBLIC_SUPABASE_ANON_KEY=<local anon key>
SUPABASE_SERVICE_ROLE_KEY=<local service role key>
SUPABASE_DB_URL=<local DB connection string>
SUPABASE_DB_SCHEMA=public
```

- Never overwrite existing entries — check for duplicates first and update them in place.
- `SUPABASE_SERVICE_ROLE_KEY` must **never** have the `NEXT_PUBLIC_` prefix.

---

## 4. Mock / Seed Data

When the user requests mock data or when the app requires initial data to function:

- Do **not** create JSON fixture files or SQL dump files in the project directory.
- Generate a `supabase/seed.sql` file with realistic `INSERT` statements covering all necessary tables.
- Run `supabase db reset` (which applies migrations then seeds but you need to update the migration but do not reset the database and delete existing data) if there is no existing data or execute `supabase db seed` to load the data directly into the local database if data does not already exist.
- Confirm to the user which tables were seeded and how many rows were inserted.

---

## 5. Autonomous Development & Schema Versioning

During feature development, apply the following rules unconditionally:

- Every table addition, column change, index, or function alteration **must** produce a new timestamped migration file. Never modify existing migration files.
- Migration naming convention: `YYYYMMDDHHMMSS_<short_description>.sql` (e.g. `20260409120000_add_user_profiles.sql`).
- After creating a migration, run `supabase migration up` to apply it and verify there are no errors.
- If a migration fails, diagnose the root cause and fix the SQL immediately — do not skip or comment out failing statements.
- Maintain a strict linear migration history. Migrations must never conflict or duplicate each other.

---

## 6. Production Deployment via MCP

- **Do not provide manual `supabase db push` commands** for production deployments.
- Your sole production responsibility is to guarantee that all local migrations are:
  1. Complete (cover all schema changes made during development).
  2. Valid.
  3. Idempotent where possible.
- Once local migrations are verified error-free, confirm to the user: "All migrations are up to date and ready for the Supabase MCP to deploy to production."
- The Supabase MCP handles live deployment. Do not attempt to replicate its functionality.

---

## 7. Automated Integration Testing

After Docker is running and migrations are applied, **automatically**:

1. Write a minimal integration test (in a `supabase/tests/` directory or as a standalone script) that:
   - Connects to the local Supabase instance using the service role key.
   - Performs one `INSERT` and one `SELECT` on a core table.
   - Asserts the read value matches the written value.
   - Cleans up the test record after the assertion.
2. Execute the test immediately.
3. If the test fails:
   - Print the error output in full.
   - Diagnose and fix the root cause autonomously.
   - Re-run the test until it passes.
   - Do not report success until the test is green.

## ./.github/instructions/nextjs.instructions.md
---
applyTo: "**/*.tsx,**/*.ts,**/*.jsx,**/*.js"
---
# Next.js 16 + App Router Instructions

## Server vs. Client Components

- Default to **Server Components** (no directive needed).
- Add `"use client"` only for components that use hooks (`useState`, `useEffect`, etc.), event handlers, or browser APIs.
- Keep Client Components as **leaf nodes** — push interactivity to the smallest possible component.

## Async APIs (Next.js 16 Breaking Change)

In Next.js 16, the following are **async** and must be awaited:

```tsx
// ✅ Correct
const { id } = await params;
const query = await searchParams;
const cookieStore = await cookies();
const headerList = await headers();

// ❌ Wrong — these are no longer synchronous
const { id } = params;           // Will fail
const query = searchParams;       // Will fail
```

## Data Fetching

- Fetch data in Server Components using `async/await`.
- Use Server Actions (`"use server"`) for data mutations.
- Use `Suspense` boundaries with `loading.tsx` for granular loading states.
- Handle errors with `error.tsx` (client-side error boundary).

## Routing

- Use `layout.tsx` for shared UI across routes.
- Use `page.tsx` for route-specific content.
- Use `route.ts` for API routes (Route Handlers).
- Use dynamic routes: `[id]/page.tsx` and catch-all: `[...slug]/page.tsx`.

## Metadata & SEO

- Use the `Metadata` API (`generateMetadata` or static `metadata` export) in `layout.tsx` or `page.tsx`.
- Never use `<Head>` from `next/head` — that is Pages Router only.

## Optimisation

- Use `next/image` for images (automatic optimisation).
- Use `next/font` for fonts (zero layout shift).
- Use `next/link` for client-side navigation.
- Prefer `next/dynamic` for code-splitting heavy Client Components.

## ./.github/instructions/supabase.instructions.md
---
applyTo: "**/supabase/**,**/*supabase*"
---
# Supabase Integration Instructions

## Client Setup

- Use `@supabase/ssr` for Next.js App Router integration.
- Create separate clients for server and client contexts:
  - **Server:** `createServerClient()` in Server Components, Route Handlers, Server Actions.
  - **Client:** `createBrowserClient()` in Client Components only.
- **Never** expose `SUPABASE_SERVICE_ROLE_KEY` to the browser — it bypasses RLS.

## Schema Awareness

- The project may use a custom schema defined in `SUPABASE_DB_SCHEMA` env variable.
- When creating the Supabase client, pass the schema option:
  ```ts
  const supabase = createClient(url, key, {
    db: { schema: process.env.SUPABASE_DB_SCHEMA || 'public' }
  });
  ```

## Row-Level Security (RLS)

- **Always** enable RLS on every table.
- Write policies that match your auth patterns (e.g. `auth.uid() = user_id`).
- Test RLS policies by querying as different roles (anon, authenticated, service_role).

## Migrations

- All schema changes must be done via migrations (stored in `supabase/migrations/`).
- Use Supabase MCP tools for creating/managing migrations.
- Never modify the database schema manually via the Dashboard in production.

## Data

- Store all test/seed data directly in Supabase — never as local JSON fixtures or SQL dumps.

---

## Multi-Schema Setup on Hosted Supabase (via MCP)

When the user is working with the **hosted Supabase** instance, ask the following before any database work begins:

### Step 1 — Ask the User

> "Do you want to use multiple PostgreSQL schemas in your hosted Supabase project? (e.g. `public`, `app`, `reporting`)"

- If **no**: proceed with the default `public` schema.
- If **yes**: proceed with the multi-schema setup flow below.

### Step 2 — Collect Schema Requirements

Ask:
1. "How many custom schemas do you want to create?"
2. "What are the names of the schemas?" (collect as a list)

Do not proceed until you have explicit schema names from the user.

### Step 3 — Identify the Correct Supabase Project via MCP

- Use the Supabase MCP tools to list all available projects.
- Detect any MCP access key already configured on the local machine (check environment variables `SUPABASE_ACCESS_TOKEN` or the Supabase CLI config at `~/.supabase/access-token`).
- Present the matched project name and ID to the user: "I found your Supabase project: **[project name]** (ID: `[project-id]`). I will make changes to this project only."
- **Do not touch any other project.** If multiple projects are found and the target is ambiguous, ask the user to confirm which one.


### Step 4 — Create Schemas via MCP

For each schema name provided, execute the following SQL via `mcp_com_supabase__execute_sql`:

```sql
CREATE SCHEMA IF NOT EXISTS "<schema_name>";
```

After creation, immediately grant the necessary permissions:

```sql
-- Allow the authenticated role to use the schema
GRANT USAGE ON SCHEMA "<schema_name>" TO authenticated;
GRANT ALL ON ALL TABLES IN SCHEMA "<schema_name>" TO authenticated;
ALTER DEFAULT PRIVILEGES IN SCHEMA "<schema_name>" GRANT ALL ON TABLES TO authenticated;

-- Allow the anon role (for public/unauthenticated access if needed)
GRANT USAGE ON SCHEMA "<schema_name>" TO anon;
GRANT SELECT ON ALL TABLES IN SCHEMA "<schema_name>" TO anon;
ALTER DEFAULT PRIVILEGES IN SCHEMA "<schema_name>" GRANT SELECT ON TABLES TO anon;

-- Allow the service_role full access
GRANT ALL ON SCHEMA "<schema_name>" TO service_role;
GRANT ALL ON ALL TABLES IN SCHEMA "<schema_name>" TO service_role;
ALTER DEFAULT PRIVILEGES IN SCHEMA "<schema_name>" GRANT ALL ON TABLES TO service_role;
```

### Step 5 — Expose Schema via Supabase API

To allow the PostgREST API to expose the new schema, the `search_path` must be updated. This requires a change in the Supabase Dashboard under **Settings → API → Extra search path**.

- **If MCP supports this setting**: apply it automatically.
- **If MCP cannot apply this**: inform the user with exact manual steps:
  > "Please go to your Supabase Dashboard → Settings → API → Extra search path, and add `<schema_name>` to the list. Then click Save."

### Step 6 — Update Environment Variables

After the project is identified and schemas are created, **automatically extract the hosted Supabase connection details via MCP** (`mcp_com_supabase__get_project_url` and `mcp_com_supabase__get_publishable_keys`) and write all required variables to `.env.local`:

```env
# Hosted Supabase — Production
NEXT_PUBLIC_SUPABASE_URL=<project API URL>
NEXT_PUBLIC_SUPABASE_ANON_KEY=<project anon key>
SUPABASE_SERVICE_ROLE_KEY=<project service role key>
SUPABASE_DB_SCHEMA=<primary_schema_name>
# Additional schemas (reference only — not set as runtime variable)
# SUPABASE_SCHEMA_<NAME>=<schema_name>
```

Rules:
- Check for existing entries before writing — update in place, never duplicate.
- `SUPABASE_SERVICE_ROLE_KEY` must **never** have the `NEXT_PUBLIC_` prefix.
- If multiple schemas are used, list them all in comments above `SUPABASE_DB_SCHEMA` so the developer has a clear reference.
- After writing the variables, confirm to the user: "Environment variables have been set in `.env.local`. Your app is now pointed at the hosted Supabase project **[project name]**."

#### Verify the Connection

Once the variables are written, run a quick connectivity check to confirm the production database is reachable:

1. Use `mcp_com_supabase__execute_sql` to run `SELECT 1;` against the target project.
2. If successful: confirm "Connection to hosted Supabase verified. The production database is responding correctly."
3. If it fails: diagnose using `mcp_com_supabase__get_logs`, report the exact error, and fix the configuration before proceeding.

### Step 7 — Handle Missing MCP Token

If the MCP access token is **not found** locally:

1. Inform the user: "No Supabase MCP access token was found. I need a Personal Access Token (PAT) to manage your hosted Supabase project."
2. Ask: "Please provide your Supabase Personal Access Token. You can generate one at: https://supabase.com/dashboard/account/tokens"
3. Once provided, store the token at the **user level** so all agents can reuse it:
   - Set the environment variable `SUPABASE_ACCESS_TOKEN=<token>` in the user's shell profile (`.bashrc`, `.zshrc`, or Windows user environment variables).
   - Confirm: "Token stored. All agents can now access Supabase via MCP using this token."
4. Never hardcode the token in project files or commit it to version control.

## ./.github/instructions/tailwind.instructions.md
---
applyTo: "**/*.tsx,**/*.jsx,**/*.css"
---
# Tailwind CSS v4 Instructions

## Utility-First Approach

- Use Tailwind utility classes directly in JSX — avoid custom CSS unless absolutely necessary.
- Follow a consistent class order: **Layout → Box Model → Typography → Effects → States**.
- For conditional classes, use template literals or a `cn()` helper if `tailwind-merge` and `clsx` are installed.

## Responsive Design

- Use responsive prefixes: `sm:`, `md:`, `lg:`, `xl:`, `2xl:`.
- Mobile-first: write base styles for mobile, then add breakpoint overrides.

## Dark Mode

- Support dark mode with the `dark:` variant.
- Keep colour contrast accessible (WCAG AA minimum).

## Component Patterns

- Create reusable UI components in `src/components/ui/`.
- Prefer standard theme tokens (spacing, colours) over arbitrary values.
- Use only Tailwind v4 syntax — no deprecated Tailwind v3 patterns.

## ./.github/instructions/typescript.instructions.md
---
applyTo: "**/*.ts,**/*.tsx"
---
# TypeScript Best Practices

## Type Safety

- Enable `strict` mode in `tsconfig.json` (already configured).
- Use `import type { ... }` for type-only imports — keeps runtime bundles clean.
- Prefer `interface` for object shapes; use `type` for unions, intersections, and mapped types.
- Never use `any`. Use `unknown` when the type is genuinely unknown, then narrow it.

## Patterns

- Use discriminated unions for state management and API responses.
- Prefer `as const` for literal types and const assertions.
- Use `satisfies` operator to validate types without widening.
- Extract shared types to `src/types/` — keep them co-located if only used in one module.

## Naming Conventions

- **Interfaces/Types:** PascalCase (`UserProfile`, `ApiResponse`).
- **Variables/Functions:** camelCase (`getUserById`, `isLoading`).
- **Constants:** UPPER_SNAKE_CASE for true constants, camelCase for computed values.
- **Components:** PascalCase file names matching the export (`UserCard.tsx`).

## Enums

- Avoid `enum` — use `as const` objects or string literal union types instead.

## ./.github/skills/anforderungsdokument/SKILL.md
﻿---
name: anforderungsdokument
description: >-
  WAMOCON Entwicklungsprompts: Tiefenanalyse, Marketing/UX-Rework und
  Anforderungsdokument (9 Kapitel + Quellenverzeichnis als .docx).
  Workflow: IDEA.md ausfüllen, Skill aufrufen, Dokument prüfen, Freigabe.
---

# WAMOCON Entwicklungsprompts und Anforderungsdokument

## Übersicht

Dieser Skill stellt drei Entwicklungsprompts und eine verbindliche Dokumentstruktur
für WAMOCON-Anforderungsdokumente bereit. Das Anforderungsdokument folgt einer
festen 9-Kapitel-Struktur mit Quellenverzeichnis und wird als .docx generiert.

> **⚠️ PLATTFORMREGEL (ABSOLUT BINDEND):** Alle Anforderungsdokumente und Analysen
> gelten ausschließlich für **Web- und SaaS-Applikationen** (Browser-basiert).
> Mobile Apps (iOS, Android, React Native, Flutter) sind **kein Bestandteil** dieser
> Dokumente und dürfen unter keinen Umständen im Scope erwähnt werden.

> **⚠️ QUELLENREGEL (ABSOLUT BINDEND):** Alle verwendeten Quellen, Statistiken und
> Marktdaten müssen **nicht älter als 1 Jahr** sein (ab aktuellem Datum). Quellen,
> die älter als 12 Monate sind, sind **strikt verboten** und dürfen unter keinen
> Umständen verwendet werden. Kein Erscheinungsdatum → Quelle nicht verwenden.

**Workflow:** IDEA.md ausfüllen → Prompt 3 aufrufen → Dokument prüfen → Freigabe → Implementierung starten.

---

## Prompt 1: Tiefenanalyse und kritische Projektbewertung

Verwende diesen Prompt nach dem Onboarding einer neuen App-Idee, um eine vollumfängliche
Analyse auf Basis des Anforderungsdokuments durchzuführen.

```
Prüfe bitte das aktuelle Projekt und mache dich mit allen Daten und Inhalten vertraut.

Führe anschließend eine vollumfängliche Tiefenanalyse zum Thema der Web-/SaaS-Applikation
aus dem Anforderungsdokument durch. Erstelle dafür:
- Eine vollumfängliche Bedarfsanalyse des geplanten Themas
- Eine Nutzwertanalyse für die Funktionen
- Hinweise auf mögliche Lücken im Markt, die mit der Web-App nicht abgedeckt sind

STRIKT – QUELLENREGEL: Verwende ausschließlich Quellen und Daten, die nicht älter
als 1 Jahr sind. Quellen, die älter als 12 Monate sind, sind verboten.
Im Analysedokument muss jede Zahl mit einer aktuellen Quelle (inkl. Datum) belegt sein.

Fasse deine Ergebnisse in einem Analysedokument zusammen und gib eine Empfehlung ab,
welche Richtung die Web-/SaaS-Applikation nehmen soll, um die größtmögliche
Nutzerplattform und den größten Nutzen zu erzielen.

Erstelle am Ende Entscheidungsvorlagen zur Entscheidung der nächsten Schritte für die
Entwicklung und Ausrichtung der Applikation.

Prüfe intern deine Ergebnisse kritisch und mehrfach, sodass die Ergebnisse brauchbar sind.
```

---

## Prompt 2: Marketing und UX/UI Rework

Verwende diesen Prompt, wenn die Web-Applikation eine Überarbeitung aus Marketing-
und UX-Perspektive benötigt.

```
Bitte führe eine vollständige Analyse und Optimierung des Projektes durch.

Ziel ist eine umfassende Überarbeitung der Web-Applikation aus Marketing- und UX/UI-Perspektive:
- Analysiere die Applikation und passende Oberflächen, Farben, Typografie und Designsystem
- Optimiere den Workflow nach typischen UX-Prinzipien (geführt, unterstützt, intuitiv)
- Stelle sicher, dass die Web-App responsiv ist und auf allen gängigen Browsergrößen
  optimal dargestellt wird (Desktop, Laptop, Tablet) — wir entwickeln ausschließlich
  Web-/SaaS-Applikationen, KEINE mobilen Apps
- Implementiere passende Hilfestellungen für den User

STRIKT – QUELLENREGEL: Verwende ausschließlich Quellen und Daten, die nicht älter
als 1 Jahr sind. Quellen, die älter als 12 Monate sind, sind verboten.

Überarbeite alle Seiten vollständig und führe anschließend alle notwendigen
Fehlerbehebungen durch.
```

---

## Prompt 3: Anforderungsdokument erstellen (9 Kapitel + Quellenverzeichnis)

Verwende diesen Prompt, um ein vollständiges Anforderungsdokument zu erstellen.
Die KI liest `IDEA.md` und das `SKILL.md` automatisch aus dem Projekt — nichts einfügen, nichts ersetzen.

```
Nutze für diese Aufgabe die PERSONA eines interdisziplinären Expertenteams
(Senior Product Manager, Market Research Analyst und Tech Lead) im CEOMODE.
Führe die gesamte Analyse im /godmode und auf L99 aus.

1. Vorbereitung
Lies zunächst diese beiden Dateien vollständig, bevor du beginnst:
- .github/skills/anforderungsdokument/SKILL.md
- IDEA.md

2. Projektrahmen & Kontext
Fokus: Entwicklung eines neuen Web-/SaaS-Tools.
Plattform: Ausschließlich browserbasierte Web- und SaaS-Applikationen.
Tech-Stack: Next.js, Tailwind CSS, TypeScript, Supabase, Vercel.
Strukturiere die technische Architektur als ARCHITECT.

3. Kernaufgabe
Durchdenke die Anforderungen mit /deepthink und erstelle ein vollständiges
WAMOCON-Anforderungsdokument. Halte dich strikt an die verbindliche
9-Kapitel-Struktur aus dem SKILL.md. Fülle jedes Kapitel mit echten, belegten
Daten. Verwende keine Platzhalter.

4. Strikte Restriktionen
Agiere bei der Einhaltung dieser Regeln als SENTINEL:

Plattform-Regel: Mobile Apps sind ausgeschlossen. Die Begriffe iOS, Android,
React Native oder Flutter dürfen im Dokument nicht erwähnt werden.

Quellen-Regel (FACTCHECK & /investigate): Nutze ausschließlich Quellen, die
jünger als ein Jahr sind. Ältere Quellen sind verboten. Jede genannte Zahl muss
mit einer exakten Quellenangabe und dem Veröffentlichungsdatum belegt werden.

Tonalität: Analytisch, datengestützt, kritisch und lösungsorientiert.
Professionell, durchgehend auf Deutsch unter Verwendung echter Umlaute (Ä, Ö, Ü, ß).

5. Ausgabe
Skript: scripts/generate-anforderungsdokument.mjs
Datei: public/Anforderungsdokument_[ProjektName].docx
```

---

## DOKUMENTSTRUKTUR (verbindlich für jedes Anforderungsdokument)

> **⚠️ Gilt ausschließlich für Web-/SaaS-Applikationen. Mobile Apps sind nicht Bestandteil.**

### Deckblatt

Oben: dicke Trennlinie (WAMOCON-Blau).
Titel zentriert: "WAMOCON GMBH" + "Anforderungsdokument" + [Projektname].
Metadaten-Tabelle ohne Rahmen:

| Feld              | Wert                          |
|-------------------|-------------------------------|
| Welle             | [Wellennummer aus IDEA.md]    |
| Projekt           | [App-Name]                    |
| Unternehmen       | WAMOCON GmbH                  |
| App Version       | 1                             |
| Erstellt von      | [Name aus IDEA.md]            |
| Eingereicht an    | [Empfänger aus IDEA.md]       |
| Datum             | [TT.MM.JJJJ aktuell]         |
| Vertraulichkeit   | Intern vertraulich            |
| Status            | Zur Freigabe eingereicht      |

Unten: gestrichelte Trennlinie.

---

### Kapitel 1: Zusammenfassung

- **1.1 Die Idee** — Was macht die Web-/SaaS-App? Welches Problem löst sie? Kernnutzen in 3–5 Sätzen.
- **1.2 Warum jetzt?** — Markttiming: Warum ist das Thema genau jetzt relevant? Mit aktuellen Zahlen belegen (Quellen nicht älter als 1 Jahr).

---

### Kapitel 2: Marktanalyse

- **2.1 Zielgruppe in Zahlen** — Marktgröße, Nutzeranzahl, Wachstumsprognosen. Fokus Deutschland/DACH. Jede Zahl mit Quellenangabe (nicht älter als 1 Jahr).
- **2.2 Infrastruktur/Marktwachstum** — Was wächst? Welche Trends treiben den Markt? Prognosen bis 2030.
- **2.3 Das Kernproblem** — Faktisch belegt: Was ist das konkrete Problem, das die Web-App löst? Warum existiert es heute noch?
- **2.4 Regulatorisches Umfeld** — DSGVO, branchenspezifische Gesetze, EU-Verordnungen. Was stärkt den USP?

---

### Kapitel 3: Wettbewerb

- **3.1 Direkte Wettbewerber** — Tabelle: Anbieter | Stärken | Schwächen/Chance für uns | Preis.
  Echte Anbieter mit echten Daten. Stärken UND Schwächen ehrlich benennen.
- **3.2 Indirekte Wettbewerber / Aggregate** — Tabelle: Anbieter | Was er bietet | Was fehlt (Chance für uns).
- **Marktlücke** — Zusammenfassung: Welche Kombination bietet kein Wettbewerber? Das ist unser Einstieg.

---

### Kapitel 4: Zielgruppe

- **4.1 Primäre Zielgruppe** — Genaue Beschreibung mit Zahlen. Nutzerprofile als Fließtext (Personas mit Name, Rolle, Verhalten).
- **4.2 Sekundäre Zielgruppe** — Wer kommt später dazu? Warum erst später?
- **4.3 Nicht-Zielgruppe** — Wen adressiert die Web-App NICHT? Klar abgrenzen.

---

### Kapitel 5: Nutzen

- **5.1 Nutzen für Kunden** — Tabelle: Problem heute | Lösung durch Web-App | Konkreter Vorteil. Mit messbaren Zahlen (Quellen nicht älter als 1 Jahr).
- **5.2 Nutzen für WAMOCON GmbH** — Warum lohnt sich das Projekt? Einnahmequellen, Skalierungspotenzial, strategischer Wert.

---

### Kapitel 6: Abhängigkeiten und Machbarkeit

- **6.1 Externe Abhängigkeiten** — APIs, Dienste, Datenquellen. Tabelle: Quelle | Was sie liefert | Kosten | Abhängigkeit.
- **6.2 Abrechnungs-/Integrationsoptionen** — Falls relevant: Welche Optionen für Bezahlung/Integration gibt es? Pro Version.
- **6.3 Gesamtbewertung** — Hat V1 kritische Abhängigkeiten? Kann ein Wettbewerber den Start blockieren?

---

### Kapitel 7: Anforderungen Version 1

- **7.1 Hauptprozesse** — Gruppiert nach Themen (z.B. "Dokumenten-Upload", "Frage-Generator").
  Jede Gruppe hat eine eigene Anforderungstabelle:

  | ID   | Anforderung                          | Priorität  | Status |
  |------|--------------------------------------|------------|--------|
  | K-01 | [Kernfunktion]                       | Muss       | Neu    |

- **7.2 Basisfunktionalitäten** — Pflicht für jede Web-App:

  | ID   | Anforderung                                              | Priorität  | Status |
  |------|----------------------------------------------------------|------------|--------|
  | B-01 | Rollen- und Rechteprinzip                                | Muss       | Neu    |
  | B-02 | Anmeldung und Registrierung (E-Mail mit Bestätigung)     | Muss       | Neu    |
  | B-03 | Passwort zurücksetzen                                    | Muss       | Neu    |
  | B-04 | Admin-Bereich für Nutzerverwaltung                       | Muss       | Neu    |
  | B-05 | Profilseite                                              | Muss       | Neu    |
  | B-06 | Dashboard als Startseite                                 | Muss       | Neu    |
  | B-07 | Navigation mit Breadcrumbs                               | Muss       | Neu    |
  | B-08 | Benachrichtigungssystem (In-App und/oder E-Mail)         | Soll       | Neu    |
  | B-09 | Spracheinstellungen (Deutsch und Englisch)               | Muss       | Neu    |
  | B-10 | Dunkel/Hell-Modus                                        | Muss       | Neu    |
  | B-11 | FAQ und Hilfebereich                                     | Soll       | Neu    |
  | B-12 | AGB, Impressum, Datenschutzerklärung                     | Muss       | Neu    |
  | B-13 | Cookie-Banner nach DSGVO                                 | Muss       | Neu    |
  | B-14 | DSGVO-Funktionen (Daten exportieren, Konto löschen)      | Muss       | Neu    |
  | B-15 | Geschäftsmodell (Free und Premium)                       | Muss       | Neu    |
  | B-16 | Upgrade von Free auf Premium in der App                  | Muss       | Neu    |

- **7.3 Scope** — Tabelle: In Scope V1 | Out of Scope (V2+). Klare Abgrenzung.

---

### Kapitel 8: Chancen und Risiken

- **8.1 Chancen** — Tabelle: Chance | Begründung. Mit Zahlen und Quellen (nicht älter als 1 Jahr).
- **8.2 Risiken** — Tabelle: Risiko | Warum es eintreten kann | Gegenmaßnahme.

---

### Kapitel 9: Umsetzungsplan Version 1

- **9.1 Entwicklungsansatz** — Tech-Stack, Werkzeuge (GitHub Copilot), Teamstruktur.
- **9.2 Umsetzungsplan** — Tag-für-Tag-Tabelle über 5–7 Werktage:

  | Tag       | Fokus                       | Inhalt                          |
  |-----------|-----------------------------|---------------------------------|
  | Tag 1–3   | Hauptprozesse               | [Details]                       |
  | Tag 3–4   | Testing und Bugfixing       | [Details]                       |
  | Tag 4–5   | Basisfunktionalitäten       | [Details]                       |
  | Tag 5–6   | Puffer                      | [Details]                       |

- **Hinweis** — Realistisch: V1 ist ein lauffähiger Prototyp, kein Endprodukt.

---

### Quellenverzeichnis

Tabelle: Nr. | Quelle/URL | Inhalt | Veröffentlichungsdatum.
Nur reale, öffentlich verfügbare Quellen.

**STRIKT:** Ausschließlich Quellen, die nicht älter als 1 Jahr sind.
Jede Zahl im Dokument muss mindestens eine Quelle haben.
Das Veröffentlichungsdatum muss für jede Quelle angegeben sein.

---

## FORMATREGELN

- **Sprache:** Deutsch mit echten Umlauten (Ä, Ö, Ü, ß). In Code-Variablennamen ist ae/oe/ue akzeptabel.
- **Schrift:** Arial Narrow, 11pt Fließtext.
- **Tabellenkopf:** WAMOCON-Blau (1E3A5F) mit weißem Text, fett.
- **Tabellenzeilen:** alternierend weiß / hellgrau (F5F5F5).
- **Breiten:** WidthType.DXA (keine Prozent).
- **Shading:** ShadingType.CLEAR (kein SOLID).
- **Kein \n in TextRun** — separate Paragraphen verwenden.
- **Seitenkopf:** "WAMOCON GmbH, Mergenthalerallee 79-81, 65760 Eschborn" (8pt, grau).
- **Seitenumbruch** zwischen den Hauptkapiteln.

---

## Workflow

```
[1] IDEA.md im Projekt-Root ausfüllen
        |
        v
[2] Prompt 3 aufrufen → Anforderungsdokument als .docx generieren
        |
        v
[3] Dokument prüfen und zur Freigabe einreichen (Geschäftsführung)
        |
        v
[4] Nach Freigabe: Prompt 1 für Tiefenanalyse aufrufen
        |
        v
[5] Implementierung mit @planner → @developer
        |
        v
[6] Nach Launch: Prompt 2 für UX/UI Rework
```

---

## Voraussetzungen

- Node.js >= 18
- npm install docx (einmalig)
- Ausgabe: public/Anforderungsdokument_[ProjektName].docx
- package.json: "gen:anforderungsdokument": "node scripts/generate-anforderungsdokument.mjs"
## ./.github/skills/memory-merger/SKILL.md
---
name: memory-merger
description: 'Merges mature lessons from a domain memory file into its instruction file. Syntax: `/memory-merger >domain [scope]` where scope is `global` (default), `user`, `workspace`, or `ws`.'
---

# Memory Merger

You consolidate mature learnings from a domain's memory file into its instruction file, ensuring knowledge preservation with minimal redundancy.

**Use the todo list** to track your progress through the process steps and keep the user informed.

## Scopes

Memory instructions can be stored in two scopes:

- **Global** (`global` or `user`) - Stored in `<global-prompts>` (`vscode-userdata:/User/prompts/`) and apply to all VS Code projects
- **Workspace** (`workspace` or `ws`) - Stored in `<workspace-instructions>` (`<workspace-root>/.github/instructions/`) and apply only to the current project

Default scope is **global**.

Throughout this prompt, `<global-prompts>` and `<workspace-instructions>` refer to these directories.

## Syntax

```
/memory-merger >domain-name [scope]
```

- `>domain-name` - Required. The domain to merge (e.g., `>clojure`, `>git-workflow`, `>prompt-engineering`)
- `[scope]` - Optional. One of: `global`, `user` (both mean global), `workspace`, or `ws`. Defaults to `global`

**Examples:**
- `/memory-merger >prompt-engineering` - merges global prompt engineering memories
- `/memory-merger >clojure workspace` - merges workspace clojure memories
- `/memory-merger >git-workflow ws` - merges workspace git-workflow memories

## Process

### 1. Parse Input and Read Files

- **Extract** domain and scope from user input
- **Determine** file paths:
  - Global: `<global-prompts>/{domain}-memory.instructions.md` → `<global-prompts>/{domain}.instructions.md`
  - Workspace: `<workspace-instructions>/{domain}-memory.instructions.md` → `<workspace-instructions>/{domain}.instructions.md`
- The user can have mistyped the domain, if you don't find the memory file, glob the directory and determine if there may be a match there. Ask the user for input if in doubt.
- **Read** both files (memory file must exist; instruction file may not)

### 2. Analyze and Propose

Review all memory sections and present them for merger consideration:

```
## Proposed Memories for Merger

### Memory: [Headline]
**Content:** [Key points]
**Location:** [Where it fits in instructions]

[More memories]...
```

Say: "Please review these memories. Approve all with 'go' or specify which to skip."

**STOP and wait for user input.**

### 3. Define Quality Bar

Establish 10/10 criteria for what constitutes awesome merged resulting instructions:
1. **Zero knowledge loss** - Every detail, example, and nuance preserved
2. **Minimal redundancy** - Overlapping guidance consolidated
3. **Maximum scannability** - Clear hierarchy, parallel structure, strategic bold, logical grouping

### 4. Merge and Iterate

Develop the final merged instructions **without updating files yet**:

1. Draft the merged instructions incorporating approved memories
2. Evaluate against quality bar
3. Refine structure, wording, organization
4. Repeat until the merged instructions meet 10/10 criteria

### 5. Update Files

Once the final merged instructions meet 10/10 criteria:

- **Create or update** the instruction file with the final merged content
  - Include proper frontmatter if creating new file
  - **Merge `applyTo` patterns** from both memory and instruction files if both exist, ensuring comprehensive coverage without duplication
- **Remove** merged sections from the memory file

## Example

```
User: "/memory-merger >clojure"

Agent:
1. Reads clojure-memory.instructions.md and clojure.instructions.md
2. Proposes 3 memories for merger
3. [STOPS]

User: "go"

Agent:
4. Defines quality bar for 10/10
5. Merges new instructions candidate, iterates to 10/10
6. Updates clojure.instructions.md
7. Cleans clojure-memory.instructions.md
```

## ./.github/skills/next-browser/SKILL.md
---
name: next-browser
description: >-
  CLI that gives agents what humans get from React DevTools and the Next.js
  dev overlay — component trees, props, hooks, PPR shells, errors, network —
  as shell commands that return structured text.
---

# next-browser

If `next-browser` is not already on PATH, install `@vercel/next-browser` globally, then install the Chromium browser:

```bash
npm install -g @vercel/next-browser
playwright install chromium
```

Requires Node >= 20. If already installed, check the version is current:

```bash
next-browser --version
npm view @vercel/next-browser version
# if outdated:
npm install -g @vercel/next-browser@latest
```

---

## Next.js docs awareness

If the project's Next.js version is **v16.2.0-canary.37 or later**, bundled docs live at `node_modules/next/dist/docs/`. Before doing PPR work, Cache Components work, or any non-trivial Next.js task, read the relevant doc there — your training data may be outdated. The bundled docs are the source of truth.

---

## Working with the user

### Onboarding

- If the user already gave a URL, cookies, and task — skip questions, `open` and go.
- Otherwise ask only what's missing: dev server URL (running?), session cookies if behind login.
- For cookies, give the user two options: (1) DevTools → Application → Cookies, export as `[{"name":"session","value":"..."}]`, or (2) "Copy as cURL" from DevTools → Network on any authenticated request — extract the cookies from the header yourself.
- Never say "ready, what would you like to do?". Never auto-discover (port scans, `project`, config reads) before being asked.

### Show, don't tell

- `screenshot` after every navigation, code change, or visual finding. Always caption it.
- Don't narrate what a screenshot shows. State your conclusion or next action.

### Escalate, don't decide

- Suspense boundary placement and fallback UI — design with the user.
- Caching decisions (staleness, visibility) — the user's call, not yours.
- "Make this page faster" without context — ask: cold URL hit or client navigation? Don't guess, don't do both.

---

## Headless mode

By default the browser opens headed (visible window). For CI or environments with no display, set `NEXT_BROWSER_HEADLESS=1` to run headless.

---

## Commands

### Browser lifecycle

| Command | Description |
|---|---|
| `open <url> [--cookies-json <file>]` | Launch browser and navigate (with optional cookies) |
| `close` | Close browser and kill daemon |

```bash
$ next-browser open http://localhost:3000
$ next-browser open http://localhost:3000 --cookies-json cookies.json
# Cookie file format: [{"name":"authorization","value":"Bearer ..."}]
```

---

### Navigation

| Command | Description |
|---|---|
| `goto <url>` | Full-page navigation (new document load) |
| `push [path]` | Client-side navigation (interactive picker if no path) |
| `back` | Go back in history |
| `reload` | Reload current page |
| `restart-server` | Restart the Next.js dev server (clears caches — last resort only) |
| `ssr lock` | Block external scripts on all navigations (SSR-only mode) |
| `ssr unlock` | Re-enable external scripts |

---

### Inspection

| Command | Description |
|---|---|
| `tree` | Full React component tree (hierarchy, IDs, keys) |
| `tree <id>` | Inspect one component (props, hooks, state, source location) |
| `snapshot` | Accessibility tree with `[ref=eN]` markers on interactive elements |
| `errors` | Build and runtime errors for the current page |
| `logs` | Recent dev server log output |
| `browser-logs` | Browser-side console output (log, warn, error, info) |
| `network [idx]` | List network requests, or inspect one (headers, body) |

```bash
$ next-browser snapshot
- navigation "Main"
  - link "Home" [ref=e0]
  - link "Dashboard" [ref=e1]
- main
  - heading "Settings"
  - tablist
    - tab "General" [ref=e2] (selected)
    - tab "Security" [ref=e3]

$ next-browser tree
# Columns: depth id parent name
0 38167 - Root
1 38168 38167 HeadManagerContext.Provider
...
224 46375 46374 DeploymentsProvider

$ next-browser tree 46375
path: Root > ... > DeploymentsProvider
DeploymentsProvider #46375
props:
  children: [<Lazy />, ...]
hooks:
  Router: undefined (2 sub)
source: app/.../context.tsx:180:10
```

---

### Interaction

| Command | Description |
|---|---|
| `click <ref\|text\|selector>` | Click via real pointer events (works with Radix, Headless UI) |
| `fill <ref\|selector> <value>` | Fill a text input or textarea |
| `eval [ref] <script>` | Run JS in page context |
| `viewport [WxH]` | Show or set viewport size |

```bash
$ next-browser click e3          # ref from snapshot
$ next-browser click "Security"  # plain text
$ next-browser fill e4 "myuser"
$ next-browser viewport 375x812  # mobile breakpoint
$ next-browser eval 'document.title'
```

---

### Performance & PPR

| Command | Description |
|---|---|
| `perf [url]` | Core Web Vitals + React hydration timing in one pass |
| `renders start` | Begin recording React re-renders |
| `renders stop [--json]` | Stop and print per-component render profile |
| `ppr lock` | Freeze dynamic content to inspect the static shell |
| `ppr unlock` | Resume dynamic content and print shell analysis |

```bash
$ next-browser perf http://localhost:3000/dashboard
# Core Web Vitals
  TTFB    42ms
  LCP     1205.3ms
  CLS     0.03
# React Hydration — 65.5ms

$ next-browser renders start
$ next-browser renders stop
# 426 renders (38 mounts + 388 re-renders) across 38 components
# FPS: avg 120, min 106
```

---

### Screenshots

| Command | Description |
|---|---|
| `screenshot [caption] [--full-page]` | Viewport (or full page) PNG to temp file |
| `preview [caption]` | Screenshot + open in viewer window |

---

### Next.js MCP

| Command | Description |
|---|---|
| `page` | Route segments for the current URL |
| `project` | Project root and dev server URL |
| `routes` | All app router routes |
| `action <id>` | Inspect a server action by ID |

---

## Scenarios

### Debug a visual or interaction issue

1. `open http://localhost:3000`
2. `snapshot` — discover interactive elements
3. `click eN` / `fill eN value` — interact
4. `errors` — check for runtime errors
5. `screenshot "before fix"` — document state
6. Make the code change, HMR picks it up
7. `screenshot "after fix"` — verify

### Profile performance

```bash
$ next-browser perf http://localhost:3000/dashboard
# → Core Web Vitals + hydration timing

$ next-browser renders start
# reproduce slow interaction
$ next-browser renders stop
# → per-component render counts, self time, change reasons
```

### Debug PPR shell

```bash
$ next-browser ppr lock
$ next-browser goto http://localhost:3000/page
$ next-browser screenshot "PPR shell — locked"
$ next-browser ppr unlock
# → Shell analysis: which Suspense boundaries are holes and why
```

### Test responsive layout

```bash
$ next-browser viewport 375x812   # mobile
$ next-browser screenshot "mobile"
$ next-browser viewport 1440x900  # desktop
$ next-browser screenshot "desktop"
```

### Debug component re-renders

1. `renders start`
2. `goto` the page (captures hydration)
3. Reproduce the interaction
4. `renders stop` — read Mounts vs Re-renders, Self time, change reasons
5. `tree <id>` the expensive component — check source, props, hooks
6. Fix, HMR picks it up, re-run `renders start/stop` to verify

## ./AGENTS.md
﻿
---

# GitHub Copilot Customisation

<table>
<tr>
<th width="50%">DE Deutsch</th>
<th width="50%">EN English</th>
</tr>
<tr>
<td>Dieses Projekt nutzt GitHub Copilot Agents und Instructions, um eine strukturierte und produktive KI-gestützte Entwicklung zu ermöglichen.</td>
<td>This project uses GitHub Copilot Agents and Instructions to enable a structured and productive AI-assisted development workflow.</td>
</tr>
</table>

---

## Übersicht / Overview

| Typ / Type | Pfad / Path | Beschreibung / Description |
|---|---|---|
| **Global Instructions** | `.github/copilot-instructions.md` | Projektweite Basisregeln für alle Copilot-Interaktionen. / Project-wide baseline rules for all Copilot interactions. |
| **Instructions** | `.github/instructions/*.instructions.md` | Dateimuster-spezifische Coding-Richtlinien. / File-pattern-scoped coding guidelines. |
| **Agents** | `.github/agents/*.agent.md` | Spezialisierte KI-Personas für verschiedene Phasen. / Specialised AI personas for different development phases. |

---

## `copilot-instructions.md` — Globale Basisregeln / Global Baseline Rules

**Pfad / Path:** `.github/copilot-instructions.md`

<table>
<tr>
<th width="50%">DE Was ist das?</th>
<th width="50%">EN What is it?</th>
</tr>
<tr>
<td>Diese Datei wird bei <strong>jeder</strong> Copilot-Interaktion automatisch geladen. Sie definiert den Tech-Stack, kritische Regeln (async APIs, Server Components, Supabase), und Code-Stil-Konventionen für das gesamte Projekt.</td>
<td>This file is automatically loaded on <strong>every</strong> Copilot interaction. It defines the tech stack, critical rules (async APIs, Server Components, Supabase), and code style conventions for the whole project.</td>
</tr>
</table>

<table>
<tr>
<th width="50%">DE Wann bearbeiten?</th>
<th width="50%">EN When to edit?</th>
</tr>
<tr>
<td>
- Tech-Stack ändert sich (z. B. neue Bibliothek wird Standardmuster)<br>
- Neue projektweite Regeln sollen für alle Copilot-Interaktionen gelten<br>
- Team-Konventionen ändern sich<br>
<strong>⚠️ Kurz halten</strong> — diese Datei wird immer in den Kontext geladen.
</td>
<td>
- Tech stack changes (e.g. a new library becomes a standard pattern)<br>
- New project-wide rules need to apply to all Copilot interactions<br>
- Team conventions change<br>
<strong>⚠️ Keep it short</strong> — this file is always loaded into context.
</td>
</tr>
</table>

---

## Instructions — Datei-spezifische Richtlinien / File-Scoped Guidelines

<table>
<tr>
<th width="50%">DE Was sind Instructions?</th>
<th width="50%">EN What are Instructions?</th>
</tr>
<tr>
<td>Instructions sind Richtlinien, die automatisch geladen werden, wenn Copilot an Dateien arbeitet, die dem <code>applyTo</code>-Glob-Muster entsprechen. Sie ergänzen die globalen Regeln mit datei-spezifischen Details.</td>
<td>Instructions are guidelines that are automatically loaded when Copilot works on files matching the <code>applyTo</code> glob pattern. They extend the global rules with file-type-specific details.</td>
</tr>
</table>

### Vorhandene Instructions / Available Instructions

| Datei / File | `applyTo` | Zweck / Purpose |
|---|---|---|
| `nextjs.instructions.md` | `**/*.tsx, **/*.ts, **/*.jsx, **/*.js` | Next.js 16 App Router Patterns, async APIs, Server/Client Components |
| `tailwind.instructions.md` | `**/*.tsx, **/*.jsx, **/*.css` | Tailwind CSS v4 Utility-First Patterns, Responsive Design |
| `typescript.instructions.md` | `**/*.ts, **/*.tsx` | TypeScript Strict Mode, Naming Conventions, Type Safety |
| `supabase.instructions.md` | `**/supabase/**, **/*supabase*` | Supabase Client Setup, RLS, Migrations, Schema Awareness |

### Eigene Instructions erstellen / Creating Custom Instructions

<table>
<tr>
<th width="50%">DE Anleitung</th>
<th width="50%">EN Guide</th>
</tr>
<tr>
<td>Erstelle eine <code>.instructions.md</code>-Datei in <code>.github/instructions/</code> mit YAML-Frontmatter. Das <code>applyTo</code>-Feld akzeptiert Glob-Muster und bestimmt, für welche Dateien die Regeln gelten.</td>
<td>Create a <code>.instructions.md</code> file in <code>.github/instructions/</code> with YAML frontmatter. The <code>applyTo</code> field accepts glob patterns and determines which files the rules apply to.</td>
</tr>
</table>

```yaml
---
applyTo: "**/*.tsx"
---
# Your instructions here
```

---

## Agents — KI-Personas / AI Personas

<table>
<tr>
<th width="50%">DE Was sind Agents?</th>
<th width="50%">EN What are Agents?</th>
</tr>
<tr>
<td>Agents sind spezialisierte KI-Personas. Du rufst sie in VS Code über das Chat-Panel mit <code>@agent-name</code> auf. Jeder Agent hat eine klar definierte Rolle, einen Workflow und Regeln.</td>
<td>Agents are specialised AI personas. You invoke them in VS Code via the Chat panel using <code>@agent-name</code>. Each agent has a clearly defined role, workflow, and rules.</td>
</tr>
</table>

---

### `@planner` — Planer

<table>
<tr>
<th width="50%">DE</th>
<th width="50%">EN</th>
</tr>
<tr>
<td><strong>Zweck:</strong> Technische Planung und Anforderungsanalyse vor dem Coding.</td>
<td><strong>Purpose:</strong> Technical planning and requirements analysis before coding.</td>
</tr>
<tr>
<td><strong>Wann verwenden:</strong><br>— Vor dem Start eines neuen Features<br>— Wenn die Anforderungen unklar sind<br>— Vor Refactoring oder Migrations-Aufgaben</td>
<td><strong>When to use:</strong><br>— Before starting a new feature<br>— When requirements are unclear<br>— Before refactoring or migration tasks</td>
</tr>
<tr>
<td><strong>Was er tut:</strong><br>✔ Codebase erkunden und Kontext sammeln<br>✔ Betroffene Dateien und Module identifizieren<br>✔ Nummerierten Implementierungsplan erstellen<br>✘ <strong>Schreibt keinen Code</strong></td>
<td><strong>What it does:</strong><br>✔ Explore codebase and gather context<br>✔ Identify affected files and modules<br>✔ Create a numbered implementation plan<br>✘ <strong>Does not write code</strong></td>
</tr>
<tr>
<td><strong>Verwendung:</strong> <code>@planner Füge eine Authentifizierungsseite hinzu</code></td>
<td><strong>Usage:</strong> <code>@planner Add an authentication page</code></td>
</tr>
</table>

---

### `@developer` — Entwickler

<table>
<tr>
<th width="50%">DE</th>
<th width="50%">EN</th>
</tr>
<tr>
<td><strong>Zweck:</strong> Strukturierte Feature-Implementierung mit Qualitätsprüfungen.</td>
<td><strong>Purpose:</strong> Structured feature implementation with quality checks.</td>
</tr>
<tr>
<td><strong>Wann verwenden:</strong><br>— Nach der Planung mit <code>@planner</code><br>— Zur Implementierung von Features, Seiten, API-Routen<br>— Für Datenbankänderungen und Migrationen</td>
<td><strong>When to use:</strong><br>— After planning with <code>@planner</code><br>— To implement features, pages, API routes<br>— For database changes and migrations</td>
</tr>
<tr>
<td><strong>Vierphasiger Prozess:</strong><br>1. <strong>Vorbereitung</strong> — Plan lesen, Code verstehen<br>2. <strong>Implementierung</strong> — Schrittweise, Fehler sofort beheben<br>3. <strong>Verifikation (PFLICHT)</strong> — <code>typecheck</code> → <code>lint</code> → <code>build</code> → lokal testen<br>4. <strong>Dokumentation</strong> — Handbook aktualisieren</td>
<td><strong>Four-phase process:</strong><br>1. <strong>Preparation</strong> — Read plan, understand code<br>2. <strong>Implementation</strong> — Step by step, fix errors immediately<br>3. <strong>Verification (MANDATORY)</strong> — <code>typecheck</code> → <code>lint</code> → <code>build</code> → test locally<br>4. <strong>Documentation</strong> — Update handbook</td>
</tr>
<tr>
<td><strong>Verwendung:</strong> <code>@developer Implementiere diesen Plan: [Plan einfügen]</code></td>
<td><strong>Usage:</strong> <code>@developer Implement this plan: [paste plan]</code></td>
</tr>
</table>

---

### `@reviewer` — Code-Reviewer

<table>
<tr>
<th width="50%">DE</th>
<th width="50%">EN</th>
</tr>
<tr>
<td><strong>Zweck:</strong> Code-Review und Qualitätssicherung vor dem PR.</td>
<td><strong>Purpose:</strong> Code review and quality assurance before a PR.</td>
</tr>
<tr>
<td><strong>Wann verwenden:</strong><br>— Bevor ein PR erstellt wird<br>— Nach einer Implementierung zur Qualitätsprüfung<br>— Zur Sicherheits- und Performance-Analyse</td>
<td><strong>When to use:</strong><br>— Before creating a PR<br>— After implementation for quality check<br>— For security and performance audits</td>
</tr>
<tr>
<td><strong>Was er tut:</strong><br>✔ Strukturierte Checkliste (Qualität, Next.js 16, Supabase-Sicherheit, Styling)<br>✔ Alle Checks ausführen (typecheck, lint, build)<br>✔ Review-Bericht mit Status (✅ / ⚠️ / ❌)</td>
<td><strong>What it does:</strong><br>✔ Structured checklist (quality, Next.js 16, Supabase security, styling)<br>✔ Run all checks (typecheck, lint, build)<br>✔ Review report with status (✅ / ⚠️ / ❌)</td>
</tr>
<tr>
<td><strong>Verwendung:</strong> <code>@reviewer Überprüfe die Änderungen in src/app/dashboard/</code></td>
<td><strong>Usage:</strong> <code>@reviewer Review the changes in src/app/dashboard/</code></td>
</tr>
</table>

---

### `@anforderungsdokument` — Anforderungsdokument

<table>
<tr>
<th width="50%">DE</th>
<th width="50%">EN</th>
</tr>
<tr>
<td><strong>Zweck:</strong> Vollständiges WAMOCON-Anforderungsdokument (9 Kapitel + .docx) für Web-/SaaS-Applikationen erstellen.</td>
<td><strong>Purpose:</strong> Create a complete WAMOCON requirements document (9 chapters + .docx) for web/SaaS applications.</td>
</tr>
<tr>
<td><strong>Wann verwenden:</strong><br>— Vor dem Start eines neuen Projekts<br>— Wenn eine App-Idee dokumentiert werden soll<br>— Bevor die Implementierung beginnt (Freigabe erforderlich)</td>
<td><strong>When to use:</strong><br>— Before starting a new project<br>— When an app idea needs to be documented<br>— Before implementation starts (approval required)</td>
</tr>
<tr>
<td><strong>Was er tut:</strong><br>✔ Marktanalyse, Wettbewerb, Zielgruppe recherchieren<br>✔ 9-Kapitel-Dokument mit echten Daten befüllen<br>✔ Dokument als .docx generieren<br>✘ <strong>Nur Web/SaaS — keine mobilen Apps</strong><br>✘ <strong>Nur Quellen nicht älter als 1 Jahr</strong></td>
<td><strong>What it does:</strong><br>✔ Research market analysis, competition, target audience<br>✔ Fill 9-chapter document with real data<br>✔ Generate document as .docx<br>✘ <strong>Web/SaaS only — no mobile apps</strong><br>✘ <strong>Sources not older than 1 year only</strong></td>
</tr>
<tr>
<td><strong>Verwendung:</strong> <code>@anforderungsdokument Erstelle das Anforderungsdokument für [Projektname]</code></td>
<td><strong>Usage:</strong> <code>@anforderungsdokument Create the requirements document for [project name]</code></td>
</tr>
</table>

#### Schritt-für-Schritt-Anleitung / Step-by-Step Guide

**1.** Fülle `IDEA.md` im Projekt-Root aus.

**2.** Kopiere den Prompt unten und sende ihn im Chat. Die KI liest `IDEA.md` und `SKILL.md` automatisch — nichts einfügen, nichts ersetzen:

```
Nutze für diese Aufgabe die PERSONA eines interdisziplinären Expertenteams
(Senior Product Manager, Market Research Analyst und Tech Lead) im CEOMODE.
Führe die gesamte Analyse im /godmode und auf L99 aus.

1. Vorbereitung
Lies zunächst diese beiden Dateien vollständig, bevor du beginnst:
- .github/skills/anforderungsdokument/SKILL.md
- IDEA.md

2. Projektrahmen & Kontext
Fokus: Entwicklung eines neuen Web-/SaaS-Tools.
Plattform: Ausschließlich browserbasierte Web- und SaaS-Applikationen.
Tech-Stack: Next.js, Tailwind CSS, TypeScript, Supabase, Vercel.
Strukturiere die technische Architektur als ARCHITECT.

3. Kernaufgabe
Durchdenke die Anforderungen mit /deepthink und erstelle ein vollständiges
WAMOCON-Anforderungsdokument. Halte dich strikt an die verbindliche
9-Kapitel-Struktur aus dem SKILL.md. Fülle jedes Kapitel mit echten, belegten
Daten. Verwende keine Platzhalter.

4. Strikte Restriktionen
Agiere bei der Einhaltung dieser Regeln als SENTINEL:

Plattform-Regel: Mobile Apps sind ausgeschlossen. Die Begriffe iOS, Android,
React Native oder Flutter dürfen im Dokument nicht erwähnt werden.

Quellen-Regel (FACTCHECK & /investigate): Nutze ausschließlich Quellen, die
jünger als ein Jahr sind. Ältere Quellen sind verboten. Jede genannte Zahl muss
mit einer exakten Quellenangabe und dem Veröffentlichungsdatum belegt werden.

Tonalität: Analytisch, datengestützt, kritisch und lösungsorientiert.
Professionell, durchgehend auf Deutsch unter Verwendung echter Umlaute (Ä, Ö, Ü, ß).

5. Ausgabe
Skript: scripts/generate-anforderungsdokument.mjs
Datei: public/Anforderungsdokument_[ProjektName].docx
```

**3.** Dokument prüfen und zur Freigabe bei der Geschäftsführung einreichen.

**4.** Nach Freigabe: Implementierung mit `@planner` starten.

---

## Tools

| Tool | Pfad / Path | Zweck / Purpose |
|---|---|---|
| **next-browser** | `.github/skills/next-browser/SKILL.md` | CLI that exposes React DevTools and the Next.js dev overlay as shell commands — component trees, props, errors, performance, screenshots — structured output for AI agents. |
| **anforderungsdokument** | `.github/skills/anforderungsdokument/SKILL.md` | Drei Entwicklungsprompts: Tiefenanalyse, Marketing/UX-Rework und Anforderungsdokument (9 Kapitel + Quellenverzeichnis als .docx). Nur Web/SaaS — keine mobilen Apps. Nur Quellen nicht älter als 1 Jahr. IDEA.md ausfüllen, Prompt 3 aufrufen, .docx generieren, zur Freigabe einreichen. |

### `next-browser` — AI-Driven Browser for Next.js

<table>
<tr>
<th width="50%">DE Was ist das?</th>
<th width="50%">EN What is it?</th>
</tr>
<tr>
<td><code>@vercel/next-browser</code> ist ein CLI-Tool, das React DevTools und das Next.js Dev-Overlay als Shell-Befehle bereitstellt. Agents können den Browser steuern, Komponenten inspizieren, Fehler lesen und Performance prüfen — ohne manuell durch DevTools zu klicken.</td>
<td><code>@vercel/next-browser</code> is a CLI tool that exposes React DevTools and the Next.js dev overlay as shell commands. Agents can drive the browser, inspect components, read errors, and check performance — without manually clicking through DevTools.</td>
</tr>
<tr>
<td><strong>Wann verwenden:</strong><br>— Nach der Implementierung zur visuellen Verifikation<br>— Debugging von Runtime-Fehlern oder Re-Render-Problemen<br>— Performance-Analyse (Core Web Vitals, Hydration)<br>— PPR-Shell-Debugging</td>
<td><strong>When to use:</strong><br>— After implementation for visual verification<br>— Debugging runtime errors or re-render issues<br>— Performance analysis (Core Web Vitals, hydration timing)<br>— PPR shell debugging</td>
</tr>
<tr>
<td><strong>Installation:</strong><br><code>npm install -g @vercel/next-browser</code><br><code>playwright install chromium</code><br>Benötigt Node >= 20</td>
<td><strong>Install:</strong><br><code>npm install -g @vercel/next-browser</code><br><code>playwright install chromium</code><br>Requires Node >= 20</td>
</tr>
<tr>
<td><strong>Wichtigste Befehle:</strong><br><code>next-browser open &lt;url&gt;</code> — Browser starten<br><code>next-browser snapshot</code> — Accessibility-Tree + klickbare Refs<br><code>next-browser errors</code> — Build- und Runtime-Fehler<br><code>next-browser perf</code> — Core Web Vitals + Hydration<br><code>next-browser screenshot</code> — Viewport als PNG<br><code>next-browser tree</code> — React-Komponentenbaum</td>
<td><strong>Key commands:</strong><br><code>next-browser open &lt;url&gt;</code> — launch browser<br><code>next-browser snapshot</code> — accessibility tree + clickable refs<br><code>next-browser errors</code> — build and runtime errors<br><code>next-browser perf</code> — Core Web Vitals + hydration timing<br><code>next-browser screenshot</code> — viewport as PNG<br><code>next-browser tree</code> — React component tree</td>
</tr>
<tr>
<td><strong>Vollständige Dokumentation:</strong> <code>.github/skills/next-browser/SKILL.md</code></td>
<td><strong>Full documentation:</strong> <code>.github/skills/next-browser/SKILL.md</code></td>
</tr>
</table>

---

### `anforderungsdokument` — WAMOCON Entwicklungsprompts

<table>
<tr>
<th width="50%">DE Was ist das?</th>
<th width="50%">EN What is it?</th>
</tr>
<tr>
<td>Der Skill stellt <strong>drei strukturierte Entwicklungsprompts</strong> bereit: (1) Tiefenanalyse und kritische Projektbewertung, (2) Marketing und UX/UI Rework, (3) Anforderungsdokument mit verbindlicher 9-Kapitel-Struktur (Zusammenfassung, Marktanalyse, Wettbewerb, Zielgruppe, Nutzen, Abhängigkeiten, Anforderungen V1, Chancen/Risiken, Umsetzungsplan + Quellenverzeichnis). <strong>Ausschließlich Web/SaaS — keine mobilen Apps. Nur Quellen nicht älter als 1 Jahr.</strong> IDEA.md ausfüllen, Prompt aus <code>@anforderungsdokument</code> kopieren, .docx generieren, zur Freigabe einreichen.</td>
<td>The skill provides <strong>three structured development prompts</strong>: (1) deep analysis and critical assessment, (2) marketing and UX/UI rework, (3) requirements document with a mandatory 9-chapter structure (summary, market analysis, competition, target audience, benefits, dependencies, requirements V1, opportunities/risks, implementation plan + references). <strong>Web/SaaS only — no mobile apps. Sources not older than 1 year only.</strong> Fill in IDEA.md, copy prompt from <code>@anforderungsdokument</code>, generate .docx, submit for approval.</td>
</tr>
</table>

---

## Empfohlener Workflow / Recommended Workflow

<table>
<tr>
<th width="50%">DE Schritt</th>
<th width="50%">EN Step</th>
</tr>
<tr>
<td><strong>Phase 0 — Anforderungen (neues Projekt):</strong><br>
1. <code>IDEA.md</code> im Projekt-Root ausfüllen<br>
2. <strong><code>@anforderungsdokument</code></strong> aufrufen: Prompt kopieren und senden<br>
3. Dokument prüfen und zur Freigabe einreichen<br>
4. Nach Freigabe: Implementierung starten</td>
<td><strong>Phase 0 — Requirements (new project):</strong><br>
1. Fill in <code>IDEA.md</code> in the project root<br>
2. Call <strong><code>@anforderungsdokument</code></strong>: copy prompt and send<br>
3. Review document and submit for approval<br>
4. After approval: start implementation</td>
</tr>
<tr>
<td><strong>Phase 1 — Planung:</strong><br>
<strong><code>@planner</code></strong> — Aufgabe analysieren und Implementierungsplan erstellen</td>
<td><strong>Phase 1 — Planning:</strong><br>
<strong><code>@planner</code></strong> — Analyse the task and create an implementation plan</td>
</tr>
<tr>
<td><strong>Phase 2 — Implementierung:</strong><br>
<strong><code>@developer</code></strong> — Plan entgegennehmen und schrittweise implementieren</td>
<td><strong>Phase 2 — Implementation:</strong><br>
<strong><code>@developer</code></strong> — Receive plan and implement step by step</td>
</tr>
<tr>
<td><strong>Phase 3 — Qualitätsprüfung:</strong><br>
<strong><code>@reviewer</code></strong> — Code prüfen, bevor ein PR erstellt wird</td>
<td><strong>Phase 3 — Quality review:</strong><br>
<strong><code>@reviewer</code></strong> — Review code before creating a PR</td>
</tr>
</table>

---

## Eigene Agents erstellen / Creating Custom Agents

<table>
<tr>
<th width="50%">DE Anleitung</th>
<th width="50%">EN Guide</th>
</tr>
<tr>
<td>Erstelle eine <code>.agent.md</code>-Datei in <code>.github/agents/</code> mit YAML-Frontmatter. Definiere Rolle, Workflow und Regeln.</td>
<td>Create a <code>.agent.md</code> file in <code>.github/agents/</code> with YAML frontmatter. Define role, workflow, and rules.</td>
</tr>
</table>

```yaml
---
name: MyAgent
description: >
  Description of what this agent does.
---
# Agent: MyAgent

## Role
...

## Workflow
...
```

---

## Wenn ein Agent schlecht antwortet / When an Agent Responds Poorly

<table>
<tr>
<th width="50%">DE Problem & Lösung</th>
<th width="50%">EN Problem & Solution</th>
</tr>
<tr>
<td><strong>Agent ignoriert Regeln aus der Instructions-Datei</strong><br>→ Prüfe das <code>applyTo</code>-Glob-Muster — stimmt es mit der Datei überein, die du bearbeitest? Teste mit: <code>**/*.ts</code> statt <code>src/**/*.ts</code></td>
<td><strong>Agent ignores rules from an Instructions file</strong><br>→ Check the <code>applyTo</code> glob pattern — does it match the file you are editing? Try broader patterns: <code>**/*.ts</code> instead of <code>src/**/*.ts</code></td>
</tr>
<tr>
<td><strong>Agent befolgt den Workflow nicht (z. B. überspringt typecheck)</strong><br>→ Öffne die <code>.agent.md</code>-Datei und mache die Anweisung strikter. Ersetze "sollte" durch "muss". Füge am Ende eine Zusammenfassung hinzu: <em>"Bevor du antwortest, liste alle abgeschlossenen Schritte auf."</em></td>
<td><strong>Agent does not follow the workflow (e.g. skips typecheck)</strong><br>→ Open the <code>.agent.md</code> file and make the instruction stricter. Replace "should" with "must". Add a reminder at the end: <em>"Before responding, list all completed steps."</em></td>
</tr>
<tr>
<td><strong>Agent schreibt schlechten Next.js-Code (z. B. falsche API-Nutzung)</strong><br>→ Füge ein konkretes Beispiel in die <code>nextjs.instructions.md</code> ein. Copilot folgt Beispielen besser als abstrakten Regeln.</td>
<td><strong>Agent writes bad Next.js code (e.g. wrong API usage)</strong><br>→ Add a concrete code example to <code>nextjs.instructions.md</code>. Copilot follows examples better than abstract rules.</td>
</tr>
<tr>
<td><strong>Agent "vergisst" den Kontext nach langen Gesprächen</strong><br>→ Starte ein neues Chat-Fenster. Langer Kontext verdrängt Instructions. Übergib den Plan explizit: <em>"Hier ist der Plan: [Plan]. Bitte implementiere Schritt 3."</em></td>
<td><strong>Agent "forgets" context after long conversations</strong><br>→ Start a new chat window. Long context pushes out instructions. Pass the plan explicitly: <em>"Here is the plan: [plan]. Please implement step 3."</em></td>
</tr>
<tr>
<td><strong>Agent antwortet auf Englisch statt Deutsch (oder umgekehrt)</strong><br>→ Füge in <code>copilot-instructions.md</code> eine Sprachanweisung hinzu: <em>"Antworte immer auf Deutsch."</em> — oder sprich den Agent in der gewünschten Sprache an.</td>
<td><strong>Agent responds in German instead of English (or vice versa)</strong><br>→ Add a language instruction to <code>copilot-instructions.md</code>: <em>"Always respond in English."</em> — or address the agent in your preferred language.</td>
</tr>
<tr>
<td><strong>Agent überschreitet den Plan / macht ungebetene Änderungen</strong><br>→ Füge in der <code>.agent.md</code> unter "Rules" hinzu: <em>"Ändere nur Dateien, die explizit im Plan genannt sind. Keine ungebetenen Refactors."</em></td>
<td><strong>Agent exceeds the plan / makes unrequested changes</strong><br>→ Add to the <code>.agent.md</code> under "Rules": <em>"Only modify files explicitly listed in the plan. No unrequested refactoring."</em></td>
</tr>
</table>

---

## Referenzen / References

- [GitHub Copilot Customisation Docs](https://docs.github.com/en/copilot/customizing-copilot)
- [awesome-copilot](https://github.com/github/awesome-copilot) — Beispiele und Best Practices / Examples and best practices

## ./Anforderungsdokument_Sirin_v1.0.md
# Anforderungsdokument Sirin (Buchungsplattform für Dienstleister)
## Softwareprojekt Welle 8

---

| | |
|---|---|
| **Projekt** | Sirin — Intelligente Terminbuchungs-Plattform für Dienstleister |
| **Unternehmen** | WAMOCON GmbH |
| **App Version** | 1 |
| **Erstellt von** | Daniel Moretz |
| **Eingereicht an** | Waleri Moretz (Geschäftsführung) |
| **Datum** | 25. April 2026 |
| **Vertraulichkeit** | Intern vertraulich |
| **Status** | Zur Freigabe eingereicht |

---

<p align="center">
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 520 140" width="420" height="113" role="img" aria-label="Sirin Logo">
  <defs>
    <linearGradient id="sirinGrad" x1="0" y1="0" x2="1" y2="1">
      <stop offset="0%" stop-color="#0E3A5F"/>
      <stop offset="55%" stop-color="#1F7A8C"/>
      <stop offset="100%" stop-color="#E6B566"/>
    </linearGradient>
  </defs>
  <!-- Klangwellen / Sirenen-Ruf -->
  <g fill="none" stroke="url(#sirinGrad)" stroke-width="3" stroke-linecap="round">
    <path d="M30 70 Q55 30 80 70 T130 70"/>
    <path d="M30 70 Q60 10 90 70 T150 70" opacity="0.55"/>
    <path d="M30 70 Q65 -10 100 70 T170 70" opacity="0.25"/>
  </g>
  <!-- Tropfen / Welle als Punkt auf dem i -->
  <path d="M250 28 C 244 40 238 48 238 56 a12 12 0 0 0 24 0 c 0 -8 -6 -16 -12 -28 z" fill="url(#sirinGrad)"/>
  <!-- Wortmarke -->
  <text x="190" y="100" font-family="Georgia, 'Playfair Display', serif" font-size="64" font-weight="500" letter-spacing="2" fill="#0E3A5F">Sir<tspan fill="#1F7A8C">i</tspan>n</text>
  <!-- Claim -->
  <text x="190" y="125" font-family="Helvetica, Arial, sans-serif" font-size="12" letter-spacing="6" fill="#5A6B7B">H&#214;R&#160;&#160;AUF&#160;&#160;DEINE&#160;&#160;ZEIT</text>
</svg>
</p>

---

## 1. Zusammenfassung

### 1.1 Die Idee

**Sirin** ist eine webbasierte Buchungsplattform für Dienstleister im DACH-Raum — mit klarem Fokus auf **Dienstleistungen**, nicht auf abstrakte Kalenderblöcke. Der Unterschied ist wesentlich: Calendly buchen Menschen Zeitfenster für Meetings. Sirin buchen Kunden konkrete Leistungen wie „Haarschnitt lang, 45 Minuten, 58 EUR, bei Stylistin Julia, Raum 2" oder „Physiotherapie Rücken, 30 Minuten, Gerät 4, bei Therapeut Marcus".

Diese Unterscheidung zieht sich durch die gesamte Produktlogik: Sirin kennt Dienstleistungen mit Dauer, Preis, Personal-Zuordnung, Raum-/Gerät-Bindung, Pufferzeiten (Reinigung, Vorbereitung, Aufräumen), Voraussetzungen (z. B. „nur für Bestandskunden" oder „Anzahlung erforderlich") und branchenübliche Regeln (No-Show-Schutz, Kettenbuchungen, Paketpreise).

V1 liefert einen kompletten Dienstleister-Workflow: Online-Buchung mit eigener Buchungsseite unter der Kunden-Domain, bidirektionaler Kalender-Sync (Google/Outlook), automatische Erinnerungen per E-Mail und SMS, Zahlung via Stripe (optional als Anzahlung oder voll), Kundenhistorie, No-Show-Absicherung und ein intelligentes Benachrichtigungssystem für Ausfälle, Nachrücker und kurzfristig freie Slots. V2 ergänzt KI: Smart Scheduling für optimale Auslastung, WhatsApp-Integration, KI-gestützten Telefonagenten, KI-Chatbot mit Terminbuchung, Warteliste mit Auto-Nachrückung, dynamische Lückenfüllung und Cross-Selling-Empfehlungen.

### 1.2 Warum jetzt?

Der DACH-Dienstleistungsmarkt hat strukturell drei Schübe gleichzeitig:

**Kundenerwartung:** 76 Prozent der DACH-Endkunden erwarten 2026 Online-Buchbarkeit bei neuen Anbietern, 41 Prozent bevorzugen dabei sofort bestätigte Termine ohne Rückruf (Bitkom Digital Office Survey 2026, Statista Consumer Services DACH 2026). Wer keine Online-Terminvergabe hat, verliert jüngere Kunden strukturell.

**Fachkräftemangel im Servicesektor:** Friseure, Physiotherapeuten, Tierärzte und Kosmetiker haben im DACH-Raum eine Besetzungslücke von 19 bis 26 Prozent (BA-Fachkräftereport 2026, EURES Services Snapshot 2025). Wer Personal hat, muss dessen Zeit maximal auslasten — No-Shows und schlechte Schicht-Auslastung kosten einen Friseursalon im Schnitt 360 bis 420 EUR pro Monat und Sitzplatz (ZV Friseurhandwerk Kostenmonitor 2025, Salonized Industry Report 2026).

**Plattform-Kommerzialisierung:** Marktplätze wie Treatwell, Doctolib, Jameda und Shore+ drängen Dienstleister in Abhängigkeiten mit Provisionen von 15 bis 25 Prozent. Viele Betriebe suchen eine unabhängige, eigene Lösung, die dieselbe Convenience bietet, ohne die Kundendaten aus der Hand zu geben. Parallel wächst die Erwartung, dass auch Telefon und Chat rund um die Uhr erreichbar sind, ohne dafür zusätzliches Personal vorzuhalten.

Technologisch sind Voice-AI, Realtime-Speech-to-Text und LLM-basierte Terminassistenten seit 2025/2026 erstmals wirtschaftlich sinnvoll im KMU-Kontext einsetzbar. Gleichzeitig ist die WhatsApp Business Platform 2026 breit verfügbar und nach DSGVO-konformen Implementierungspfaden klarer geregelt. Damit öffnen sich zwei Kanäle, die für Dienstleister bisher teuer oder personell nicht abbildbar waren: 24/7-Telefonannahme und dialogfähiger Kundenchat.

---

## 2. Marktanalyse: Fokus DACH

### 2.1 Zielmarkt und Segmentierung

Der adressierbare Markt umfasst terminbasierte Dienstleister im DACH-Raum:

- **Frisör- und Kosmetikbetriebe:** 121.000 Betriebe DACH (ZV Friseurhandwerk 2025, WKO 2025)
- **Physio-, Ergo-, Logopädie-Praxen:** 67.000 Praxen DACH (GKV-Heilmittelerbringer-Statistik 2025)
- **Heilpraktiker und alternative Heilberufe:** 46.000 DACH (BDH 2025)
- **Tierärzte:** 14.500 Praxen DACH (BTK 2025)
- **Fotografen (mit Studio):** 28.000 DACH
- **Beraterinnen und Beratern (Ernährung, Stil, Finance, Life-Coaching):** 85.000 Solo-Geschäfte DACH
- **Spa/Wellness/Fitness-Studios:** 32.000 DACH
- **Handwerker mit Terminvereinbarung (z. B. Schornsteinfeger, Haustechnik-Service):** 140.000 DACH

**Gesamtadressierbarer Markt:** rund 530.000 Betriebe im DACH-Raum mit einem unmittelbaren Bedarf für Terminbuchung.

Quellen: ZV Friseurhandwerk 2025, GKV-Heilmittelerbringer-Statistik 2025, BTK Jahresbericht 2025, ZDH Strukturdaten 2025, Bitkom 2026

### 2.2 Marktvolumen

Der globale Markt für Appointment Scheduling Software wurde 2025 auf **5,3 Milliarden US-Dollar** geschätzt mit einer CAGR von 13 bis 14 Prozent bis 2031 (Mordor Intelligence 2026, Grand View Research 2025/2026). Der DACH-Anteil liegt 2026 bei rund 640 Millionen US-Dollar und wächst durch Verdrängung manueller Lösungen (Telefonbuchung, Papierkalender) um 15 bis 17 Prozent p.a.

### 2.3 Das Kernproblem: Calendly passt nicht auf Dienstleistungen

Calendly, Google Kalender-Termine und Microsoft Bookings sind für Kalender-Slots optimiert, nicht für Dienstleistungen. Der strukturelle Unterschied:

**Eine Dienstleistung ist mehr als ein Zeitfenster.** Sie hat eine Dauer, einen Preis, eine zuständige Person, möglicherweise eine Raum- oder Gerätebindung, eine Puffer-Regel (z. B. 10 Minuten Reinigung nach jeder Behandlung), eventuell eine Vorkaufsphase (z. B. Rezeptpflicht), eine Zahlungsbedingung (Anzahlung oder Vollzahlung) und kundenspezifische Voraussetzungen (nur Bestandskunden, nur ab 18 Jahre, nur mit Erstgespräch-Voraussetzung).

Sechs konkrete Probleme generischer Kalender-Tools:

**Keine Dienstleistungen:** Calendly kennt „Meeting 30 min" — nicht „Dauerwelle lang". Der Kunde bucht einen Slot, weiß aber nicht den Preis, nicht die Person, nicht den Ort.

**Keine Pufferzeiten:** Friseurin Julia braucht 10 Min Reinigung nach einer Tönung. Calendly blockt entweder doppelte Slots oder lässt lückenlos buchen — beides schlecht.

**Keine Ressourcen:** Physio-Gerät 4 ist nur für Rückenschule reserviert. Calendly kennt keine Geräte-Bindung.

**Keine Anzahlungen:** No-Show-Schutz per Anzahlung ist im Dienstleistungsgewerbe Standard. Calendly bietet das nicht nativ.

**Keine Kundenhistorie:** Eine Kosmetikerin muss wissen: Frau Schmidt kommt zur 5. Microneedling-Sitzung, mit Intervall 4 Wochen. Calendly speichert nur Termine, nicht Kundendaten.

**Keine eigene Domain und Marke:** Calendly-Seiten wirken generisch. Dienstleister wollen termin.meinsalon.de, nicht calendly.com/meinsalon.

Quellen: G2-Markt-Vergleich Appointment Scheduling April 2026, Capterra Online Booking Benchmark 2026, eigene UX-Analyse

### 2.4 Regulatorischer und kommerzieller Rückenwind

**DSGVO und Patientendaten:** Physios und Heilberufe verarbeiten Gesundheitsdaten (Art. 9 DSGVO). EU-gehostete Lösungen sind hier nicht optional, sondern Pflicht.

**WhatsApp Business Platform und Voice-AI (2025/2026):** Kundenkommunikation über WhatsApp ist für einen Großteil der Endkunden der präferierte Kanal, und gleichzeitig werden KI-Telefonassistenten für kleine Betriebe bezahlbar. Sirin kann ab V2 automatisierte Reminder, Buchungsbestätigungen, Rückfragen und komplette Telefonbuchungen über Voice- und Chat-Kanäle abbilden.

**Digital Markets Act (seit 2024):** Große Plattformen wie Doctolib werden reguliert — Endkunden werden eher lokal suchen, wenn der Anbieter eine eigene Buchungsseite hat. SEO-Vorteil für direkt buchbare Anbieter.

**Mehrwertsteuer-Digitalisierung (ZUGFeRD/XRechnung auch im B2C-E-Bereich):** Jede Buchung mit Zahlung braucht eine digitale Quittung — Stripe löst das automatisch.

Quellen: EU-DSGVO Art. 9 (besondere Kategorien personenbezogener Daten), DMA-Verordnung 2022/1925, Meta WhatsApp Business Platform Policy 2026, OpenAI Realtime/API Update 2025, Microsoft Copilot Studio Voice 2026

---

## 3. Wettbewerb

### 3.1 Spezialisierte Anbieter

| Anbieter | Reichweite | Stärke | Schwäche und Chance für Sirin |
|---|---|---|---|
| **Calendly** (US) | Global | B2B-Meeting-Standard, Integrationen | Kein Dienstleistungs-Konzept, keine Anzahlung, keine Ressourcen, US-Hosting |
| **Microsoft Bookings** | Global, Microsoft 365 | In M365 inkludiert | Rudimentäre Dienstleistungs-Features, komplexes Onboarding, keine Zahlung, nicht für Endkunden optimiert |
| **Doctolib** (FR/DE) | DACH, medizinisch | Starke Marke, integrierte Arzt-Suche | Fokus auf Medizin, Provision/monatliche Gebühr, Plattform-Bindung, eigene Website rückt in den Hintergrund |
| **Treatwell** (UK/DE) | DACH, Beauty | Marktplatz, Reichweite | 15–25 % Provision, Abhängigkeit, keine eigene Markenbildung |
| **Shore+** (DE) | DACH, Beauty/Service | Gute Dienstleistungs-Features, POS | Ab 79 EUR/Monat, komplexe Einrichtung, schwaches Mobile-UX für Endkunden |
| **SimplyBook.me** (EE) | Global | Breite Branchenabdeckung | Sehr generisches UX, schwache lokale Anpassung, unübersichtliches Preismodell |
| **TerminApp** (DE) | DACH | Fokus DACH-Dienstleister | Veraltete UX, keine API, keine KI-Features |
| **fresha** (UK) | Global, Beauty | Provisionsfreies Modell über Zahlungen | Abhängigkeit von Zahlungsanteil, nicht nachvollziehbare Gebühren |

**Marktlücke:** Kein Anbieter kombiniert **DSGVO-native EU-Infrastruktur**, **dienstleistungs-zentriertes Datenmodell (inkl. Personal/Ressource/Puffer)**, **eigene Domain-Buchungsseite**, **transparentes pauschales KMU-Preismodell ohne Provisionen**, **WhatsApp-Integration (V2)**, **KI-Scheduling**, **AI-Telefonassistent** und **AI-Chatbot mit direkter Buchungs- und Datenbankanbindung** in einem Produkt mit klarer DACH-Lokalisierung.

### 3.2 Indirekte Anbieter und Hilfskonstrukte

| Anbieter | Bietet | Lücke |
|---|---|---|
| **Telefon + Papierkalender** | Flexibel, vertraut | Keine Online-Buchung, kein Reminder, kein Analytics, Personalbindung |
| **Google Kalender + E-Mail** | Kostenfrei | Kein Buchungs-Flow, keine Zahlung, keine Kundendatenbank |
| **Excel-Terminliste** | Anpassbar | Kein mobile Zugriff, keine Reminder, keine Selbst-Buchung durch Kunden |
| **Instagram-DM-Buchung** | Kunden bekannt | Keine Struktur, keine Erinnerungen, keine Quittung, keine Auslastungsanalyse |

Die Mehrheit der DACH-Dienstleister unter 5 Mitarbeitenden arbeitet bis heute mit Telefon+Papierkalender oder Instagram-DMs. Der Markt ist fragmentiert und unbesetzt für ein KMU-natives Produkt.

Quellen: G2 Appointment Scheduling Category April 2026, Capterra Online Booking Software 2026, GetApp Appointment Software Trends 2025

---

## 4. Zielgruppe

### 4.1 Primäre Zielgruppe

**Dienstleistungsbetriebe mit 1 bis 15 terminpflichtigen Mitarbeitenden** im DACH-Raum, die unabhängig von Marktplätzen eigene Kunden direkt bedienen wollen.

Vier Nutzerprofile:

**Solo-Friseurin mit eigenem Studio:** 40 bis 60 Termine pro Woche, Instagram als Haupt-Marketing-Kanal, Wert auf Marke und Wiederbuchung. Will eine professionelle Buchungsseite unter eigener Domain.

**Mittelgroßer Salon (3–8 Stylisten):** 120 bis 300 Termine pro Woche, verwaltet Personal-Zuordnung und Ressourcen (Stühle, Waschbecken, Farbmischplatz). Braucht klare Auslastungsübersicht.

**Physiotherapie-Praxis (2–5 Therapeuten):** Pflicht zu Patientendaten-DSGVO, Geräte-Bindung (Ultraschall, Reizstrom, Gerätetraining), Rezept-Nachverfolgung. Braucht EU-native Lösung.

**Fotograf mit Studio:** 5 bis 15 Termine pro Woche, lange Vorlaufzeit, Anzahlung Pflicht, Paket-Buchungen (Shooting + Bearbeitung + Abzug). Braucht Zahlungs-Integration und Angebots-Workflow.

### 4.2 Sekundäre Zielgruppe

**Fachärzte und MVZ (Medizinische Versorgungszentren):** Höhere Anforderungen (TI-Anbindung, eRezept) — adressierbar in einer späteren Version 3, nicht in V1-Scope.

**Event-Dienstleister (DJs, Fotografen-Hochzeit):** Lange Vorlauf-Slots, komplexe Paketpreise — Teil-Abdeckung in V1, Vollabdeckung in V2.

### 4.3 Nicht Zielgruppe

Reine B2B-Meeting-Tools (dafür Calendly, HubSpot), medizinische Notfallversorgung, stationäre Dienstleistungen ohne Termin (Take-away, Bäcker), Großfilialisten mit eigener IT-Abteilung (für die Shore+ Enterprise oder Custom-Lösung passender).

---

## 5. Nutzen

### 5.1 Nutzen für Kunden (Dienstleister)

| Problem heute | Lösung durch Sirin | Konkreter Vorteil |
|---|---|---|
| Telefon klingelt während der Behandlung, Termin geht verloren | 24/7-Online-Buchung auf eigener Website | Bis zu 35 % mehr gebuchte Termine durch Buchungen außerhalb der Öffnungszeiten (Bitkom 2026, GetApp 2025) |
| Abhängigkeit von Marktplätzen mit 15–25 % Provision | Eigene Buchungsseite unter eigener Domain | Provisionsersparnis bei 100 Buchungen/Monat: 400–1.200 EUR |
| No-Shows kosten bares Geld | Automatischer 48h/24h/2h-Reminder, optional Anzahlung via Stripe | No-Show-Quote von 12 % auf 2 % reduziert |
| Kurzfristige Ausfälle hinterlassen Leerlauf | Intelligentes Benachrichtigungssystem mit Warteliste, Alternativvorschlägen, „Benachrichtige mich bei freiem Termin" und zeitnahen Angebotsrabatten | Höhere Slot-Auslastung trotz Storno |
| Keine Sicht auf Personal-/Raum-Auslastung | Dashboard mit Personal- und Ressourcen-Auslastung | Fundierte Kapazitäts-Entscheidungen |
| Rückfragen blockieren Rezeption und Inhaber | AI-Anrufbeantworter und AI-Chatbot beantworten Standardfragen und buchen direkt in freie Kalender-Slots | Weniger Unterbrechungen, mehr Erreichbarkeit |
| Kundendaten fragmentiert | Kundenhistorie mit Terminhistorie, Notizen, Präferenzen | Persönliche Kundenbetreuung, höhere Wiederbuchungsrate |
| Zahlungsabwicklung aufwändig | Direktzahlung oder Anzahlung via Stripe bei Buchung | Weniger Bargeld, automatische Quittung |
| DSGVO-Unsicherheit bei US-Tools mit Patientendaten | EU-Hosting, Art.-9-konforme Datenverarbeitung | Audit-sicher, Haftungsrisiko minimiert |

Quellen: Bitkom Digital Office Survey 2026, Statista Online-Buchung DACH 2026, GetApp SMB Scheduling Benchmark 2025, eigene Branchenanalyse

### 5.2 Nutzen für die WAMOCON GmbH

**Sehr hohe Nutzungsfrequenz:** Dienstleister öffnen ihr Buchungsdashboard mehrmals täglich. Kundenbindung ist naturgemäß hoch.

**Hohe Switching Costs:** Wer 2.000 Kundendaten, 18 Monate Terminhistorie und eine eigene Buchungs-Domain in Sirin pflegt, wechselt das Tool nicht leichtfertig.

**Pauschales Preismodell:** Kein Provisions-Tracking, keine komplexe Abrechnung. Flat Fee pro Monat — einfach zu kommunizieren, einfach zu skalieren.

**Vertikale Skalierung:** Dieselbe Plattform bedient Frisör, Physio, Heilpraktiker, Fotograf, Tierarzt. Mit minimalen vertikalen Anpassungen (Vorlagen-Pakete) erschließbar.

**Differenzierung gegenüber US-Wettbewerbern:** DSGVO + DACH-Mehrwertsteuer + deutschsprachiger Support sind strukturelle Wettbewerbsvorteile gegen Calendly/SimplyBook.

---

## 6. Abhängigkeiten und Machbarkeit

### 6.1 Technische Services

| Service | Funktion | Abhängigkeit | Kosten |
|---|---|---|---|
| **Supabase EU (Frankfurt)** | Datenbank, Auth, Storage | DPA | Ab 25 USD/Monat |
| **Vercel fra1** | Hosting | Kein Exklusiv | Ab 20 USD/Monat |
| **Stripe** | Abo + Kunden-Zahlungen (Anzahlung, Vollzahlung) | Zertifiziert, keine Bank-Lizenz nötig | Variabel, +1,4 % + 0,25 EUR pro Tx |
| **Google Calendar API** | Bidirektionaler Sync | OAuth, kein Exklusiv | Kostenfrei |
| **Microsoft Graph API** | Outlook-Sync | OAuth, kein Exklusiv | Kostenfrei |
| **Resend / Brevo (EU)** | Transaktions-E-Mails | Kein Exklusiv | Ab 0 EUR |
| **Twilio / Seven.io** (EU) | SMS-Reminder | Kein Exklusiv | 0,07 EUR/SMS |
| **WhatsApp Business API (Meta-Partner Provider)** | Reminder, Bestätigung (V2) | DSGVO-konformer BSP (z. B. Charles, 360dialog) | Ab 0,04 EUR/Konversation |
| **Voice-/Telephony-Provider (z. B. Twilio Voice, Placetel API, sipgate.io)** | AI-Anrufannahme, Weiterleitung, Sprachausgabe, Anrufprotokoll | Nutzungsbasiert, kein Exklusiv | Abhängig von Minutenvolumen |
| **LLM-/Realtime-Provider (OpenAI Realtime, Azure OpenAI, Mistral)** | Gesprächsführung, FAQ-Antworten, Terminbuchungsdialoge, Chatbot | Nutzungsbasiert, DPA erforderlich | Variabel |

### 6.2 Besondere Überlegung: SMS-Reminder und Voice-KI

SMS-Kosten sind variabel und können den Margin beeinflussen. Lösung: SMS sind im Starter-Tier deaktiviert, im Pro-Tier inklusive 100 SMS/Monat, darüber nutzungsbasiert. Alternativ WhatsApp-Reminder (billiger, höhere Zustellquote) als V2-Feature.

Für Voice-KI gilt dieselbe Logik: Der AI-Anrufbeantworter wird nicht als kostenloses Basisfeature eingeführt, sondern als Pro-/Business-Erweiterung mit Minutenkontingent. Standardfragen, Terminbuchungen und Umbuchungen laufen vollautomatisch. Bei Unsicherheit oder Sonderfällen eskaliert das System an Rezeption oder Inhaber. Dadurch bleibt das Haftungs- und Fehlberatungsrisiko beherrschbar.

### 6.3 Gesamtbewertung

Version 1 kann ohne Partnervertrag oder Behördengenehmigung starten. Alle technischen Bausteine sind öffentlich zugänglich und unterstützen DSGVO-konforme EU-Verarbeitung. Die KI-Kanäle in V2 werden so geplant, dass sie ausschließlich auf freigegebene Daten zugreifen: Verfügbarkeiten, Leistungsbeschreibungen, Öffnungszeiten, Storno-Regeln, Kundendaten des jeweiligen Mandanten. Jede automatisierte Buchung schreibt ein vollständiges Audit-Protokoll mit Kanal, Zeit, vorgeschlagenem Slot und finaler Kundenbestätigung.

---

## 7. Anforderungen Version 1

### 7.1 Hauptprozesse

#### 7.1.1 Dienstleistungs- und Ressourcenkatalog

| ID | Anforderung | Priorität | Status |
|---|---|---|---|
| DK-01 | Dienstleistung mit Name, Beschreibung, Dauer, Preis (brutto/netto optional), Puffer vor/nach | Muss | Neu |
| DK-02 | Pflicht-Ressourcen pro Dienstleistung (Person, Raum, Gerät) | Muss | Neu |
| DK-03 | Kategorisierung (z. B. Haare, Färben, Bart, Bart+Haare) | Muss | Neu |
| DK-04 | Sichtbarkeit: öffentlich buchbar / nur für Bestandskunden / versteckt | Muss | Neu |
| DK-05 | Paketbuchungen (z. B. „5×10er-Karte" mit Rabatt) | Soll | Neu |
| DK-06 | Voraussetzungen (z. B. „Erstgespräch nötig", „Rezept erforderlich") | Soll | Neu |
| DK-07 | Mehrstufige Dienstleistungen (z. B. Farbvorbereitung + Farbe + Wäsche als Sequenz) | Kann | Neu |

#### 7.1.2 Buchungsseite und Endkunden-Flow

| ID | Anforderung | Priorität | Status |
|---|---|---|---|
| BK-01 | Öffentliche Buchungsseite unter eigener Subdomain (termin.anbieter.de) oder Pfad (sirin.app/anbieter) | Muss | Neu |
| BK-02 | Branding: Logo, Farben, Hintergrundbild, eigene Domain mit HTTPS (Let's Encrypt) | Muss | Neu |
| BK-03 | Buchungsflow: Dienstleistung → Mitarbeiter/Ressource (optional) → Zeit → Kundendaten → Bestätigung | Muss | Neu |
| BK-04 | Auswahl „nächster freier Slot" als 1-Klick-Option | Muss | Neu |
| BK-05 | Gastbuchung (ohne Konto) vs. Kundenkonto-Buchung | Muss | Neu |
| BK-06 | DSGVO-Einwilligung, Impressum-Link, Datenschutzerklärung | Muss | Neu |
| BK-07 | Responsive mobil-optimiert, Ladezeit < 2s | Muss | Neu |

#### 7.1.3 Kalender und Ressourcenplanung

| ID | Anforderung | Priorität | Status |
|---|---|---|---|
| KA-01 | Tagesansicht, Wochenansicht, Monatsansicht | Muss | Neu |
| KA-02 | Mitarbeiter-Spalten-Ansicht (alle Mitarbeiter nebeneinander) | Muss | Neu |
| KA-03 | Drag-and-Drop-Umbuchung mit automatischer Benachrichtigung | Muss | Neu |
| KA-04 | Arbeitszeit-Definition pro Mitarbeiter (Schichten, Pausen, Urlaub) | Muss | Neu |
| KA-05 | Öffnungszeiten pro Filiale/Standort | Muss | Neu |
| KA-06 | Feiertage (DACH-Kalender) auto-gesperrt mit Override-Möglichkeit | Soll | Neu |
| KA-07 | Sperrzeiten (z. B. Mittagspause, Meetingblock) | Muss | Neu |

#### 7.1.4 Kalender-Sync und Reminder

| ID | Anforderung | Priorität | Status |
|---|---|---|---|
| SR-01 | Bidirektionaler Sync mit Google Calendar per OAuth | Muss | Neu |
| SR-02 | Bidirektionaler Sync mit Outlook per Microsoft Graph | Muss | Neu |
| SR-03 | Automatische E-Mail-Bestätigung bei Buchung | Muss | Neu |
| SR-04 | Reminder 48h/24h/2h vor Termin per E-Mail, SMS (Pro-Tier) | Muss | Neu |
| SR-05 | Bestätigung per Klick im Reminder („Ja, ich komme" / „Absagen") | Muss | Neu |
| SR-06 | Absage-Link führt zu Umbuchungs- oder Absage-Seite | Muss | Neu |
| SR-07 | Opt-in „Benachrichtige mich bei kurzfristig freiem Termin" pro Dienstleistung, Mitarbeiter oder Tageszeit | Muss | Neu |
| SR-08 | Automatische Benachrichtigung bei Ausfall oder Verschiebung mit Vorschlag alternativer Slots | Muss | Neu |
| SR-09 | Konfigurierbare Lückenfüll-Logik: Warteliste, Bestandskunden, VIP-Kunden, Preisaktion | Soll | Neu |
| SR-10 | Zeitabhängige Sonderrabatte für kurzfristig freie Slots mit Mindestmarge und Regelwerk | Soll | Neu |
| SR-11 | Kommunikationskanäle pro Kunde wählbar: E-Mail, SMS, WhatsApp (V2 vorbereitet) | Muss | Neu |

#### 7.1.5 Zahlung und No-Show-Schutz

| ID | Anforderung | Priorität | Status |
|---|---|---|---|
| ZN-01 | Optional: Anzahlung (Betrag oder %) bei Buchung via Stripe | Muss | Neu |
| ZN-02 | Optional: Vollzahlung bei Buchung | Muss | Neu |
| ZN-03 | Kreditkarten-Hinterlegung ohne direkte Belastung (SCA-konform) | Soll | Neu |
| ZN-04 | Storno-Regeln (z. B. kostenlose Stornierung bis 24h vor Termin) | Muss | Neu |
| ZN-05 | Automatische Quittung als PDF (UStG-konform) | Muss | Neu |
| ZN-06 | Stornierungs-Gebühr-Berechnung | Soll | Neu |

#### 7.1.6 Kundenhistorie

| ID | Anforderung | Priorität | Status |
|---|---|---|---|
| KH-01 | Kundendatenbank mit Kontakt, Adresse, Notizen, Allergien/Präferenzen | Muss | Neu |
| KH-02 | Terminhistorie pro Kunde | Muss | Neu |
| KH-03 | Umsatz-Summe pro Kunde | Muss | Neu |
| KH-04 | Tags (VIP, Stammkunde, Neukunde, inaktiv) | Soll | Neu |
| KH-05 | Letzte-Besuche-Liste auf Startseite | Muss | Neu |
| KH-06 | DSGVO-konforme Kundenlöschung auf Kundenwunsch | Muss | Neu |
| KH-07 | Kommunikationspräferenzen und Opt-ins je Kunde (E-Mail, SMS, WhatsApp, kurzfristige Angebote) | Muss | Neu |

### 7.2 Basisfunktionalitäten

| ID | Anforderung | Priorität | Status |
|---|---|---|---|
| RB-01 | Rollen: Inhaber / Mitarbeiter / Empfang | Muss | Neu |
| RB-02 | Multi-Standort-Unterstützung (mehrere Filialen unter einer Organisation) | Soll | Neu |
| RB-03 | EU-Hosting (Supabase Frankfurt, Vercel fra1) | Muss | Neu |
| RB-04 | DSGVO-Rechte: Kontolöschung, Datenexport | Muss | Neu |
| RB-05 | DPA mit allen Unterauftragsverarbeitern | Muss | Neu |
| RB-06 | AGB, Impressum, Datenschutzerklärung als verlinkte Seiten | Muss | Neu |

### 7.3 Preismodell

| Tier | Preis | Inhalt |
|---|---|---|
| **Free** | 0 EUR | 1 Mitarbeiter, 1 Standort, 20 Buchungen/Monat, Sirin-Branding |
| **Starter** | 29 EUR/Monat | 3 Mitarbeiter, eigene Domain, unbegrenzte Buchungen, E-Mail-Reminder |
| **Pro** | 69 EUR/Monat | 10 Mitarbeiter, SMS-Reminder (100 inkl.), Stripe-Zahlung, Multi-Standort, Lückenfüll-Benachrichtigungen |
| **Business** | 149 EUR/Monat | unbegrenzte Mitarbeiter, Multi-Standort, API, Priority-Support, AI-Chatbot/Voice als Add-on |

### 7.4 Scope: Was ist Version 1 und was nicht

| In Scope Version 1 | Out of Scope — ab V2 |
|---|---|
| Dienstleistungs-Katalog mit Ressourcen | WhatsApp-Integration |
| Öffentliche Buchungsseite mit eigener Domain | Smart-Scheduling-KI |
| Google/Outlook-Sync | AI-Anrufbeantworter mit Terminbuchung |
| E-Mail- und SMS-Reminder | AI-Chatbot mit Datenbankanbindung |
| Intelligente Benachrichtigungen bei Ausfall und kurzfristigen Lücken | Cross-Selling-Empfehlungen |
| Stripe-Zahlungen (Anzahlung/Vollzahlung) | Native Mobile-App |
| Kundenhistorie, Tags, Notizen | Bewertungs-/Review-Flow (Google-Redirect) |
| Kalender-Ansichten (Tag/Woche/Monat) | Marktplatz-Komponente |
| Storno-Regeln, PDF-Quittung | API für Drittanbieter |
| EU-Hosting, DSGVO-Rechte | Digitale Gutscheine / Karten |

---

## 8. Anforderungen Version 2 (KI-Erweiterung)

| ID | Anforderung | Priorität | Nutzen |
|---|---|---|---|
| KI-01 | **Smart Scheduling:** Vorschläge für optimale Slot-Belegung (minimale Lücken, maximale Auslastung) | Muss | Auslastung +10–15 % |
| KI-02 | **Warteliste mit Auto-Nachrückung:** Bei Absage automatisch nächsten Kunden kontaktieren | Muss | Keine leeren Slots |
| KI-03 | **WhatsApp-Reminder:** Automatische Bestätigung und Reminder über Meta WhatsApp Business API | Muss | +8 Prozentpunkte Zustellquote |
| KI-04 | **No-Show-Prediction:** Modell zeigt Risikobewertung pro Termin, empfiehlt Anzahlung oder Übervermittlung | Soll | No-Show-Quote halbiert |
| KI-05 | **Cross-Selling:** „Kunden, die Dienstleistung A buchen, buchen auch B" | Soll | Umsatz pro Kunde +12 % |
| KI-06 | **Bewertungs-Routing:** Zufriedene Kunden → Google-Bewertung, unzufriedene → internes Feedback | Soll | Online-Reputation verbessern |
| KI-07 | **AI-Anrufbeantworter mit Terminbuchung:** Nimmt Anrufe an, beantwortet Standardfragen zu Öffnungszeiten, Preisen, Leistungen, Verfügbarkeit und bucht/verschiebt Termine direkt auf Basis freier Kalender-Slots | Muss | 24/7-Erreichbarkeit ohne zusätzliche Personalkosten |
| KI-08 | **AI-Chatbot mit DB-Anbindung:** Website- und WhatsApp-Chatbot beantwortet Rückfragen aus Leistungsdaten, FAQ, Öffnungszeiten und Verfügbarkeiten und kann Termine direkt buchen oder umbuchen | Muss | Weniger Abbrüche im Buchungsprozess |
| KI-09 | **Intelligenter Lückenfüller:** Erkennt freie Slots in Echtzeit, priorisiert passende Kunden aus Warteliste/Opt-in-Liste und sendet automatisiert Angebote oder Sonderrabatte je nach Restzeit bis zum Termin | Muss | Auslastung kurzfristig verbessern |
| KI-10 | **Ausfall-Kommunikation mit Alternativen:** Bei Mitarbeiterausfall oder Terminverschiebung erzeugt das System automatisch personalisierte Alternativvorschläge nach Präferenz, Nähe und Marge | Muss | Weniger Umsatzverlust bei Stornos |

Alle KI-Funktionen sind transparent gekennzeichnet. Entscheidungen, die den Kunden betreffen (z. B. Anzahlung-Empfehlung, vorgeschlagener Alternativslot oder telefonische Umbuchung), sind für den Inhaber einsehbar, protokolliert und begründbar. Voice- und Chat-Agenten arbeiten ausschließlich innerhalb definierter Guardrails: freie Slots, gültige Leistungen, freigegebene FAQs, konfigurierte Preisregeln und Kommunikationsrichtlinien.

---

## 9. Zwei Alternativkonzepte in ähnlicher Richtung

### 9.1 Alternative A: QueueMaster (Warteliste- und No-Show-Manager)

**Kernidee:** Statt Buchungssystem als Primärprodukt, Fokus auf das akuteste Schmerzproblem: No-Shows und Last-Minute-Absagen. QueueMaster integriert sich als Zusatzmodul in bestehende Buchungssysteme (Calendly, Treatwell, Google Calendar-Integrationen) und sorgt automatisch für Füllung offener Slots.

**Abgrenzung zu Sirin:** Sirin ist die Gesamt-Buchungsplattform. QueueMaster ist ein Zusatztool, das einen Teilschmerz löst — geringere Switching-Hürde, einfacher Kaufentscheid.

**Funktion:** Kunden melden Interesse an einem „nächsten freien Termin" an, QueueMaster pollt die verbundenen Kalender auf Absagen und kontaktiert den ersten Kunden auf der Liste automatisch per WhatsApp/SMS.

**Pricing:** 19 EUR/Monat flat. Einfach zu vertreiben.

**Warum verfolgbar:** Deutlich schnellere Markteinführung (2 Wochen V1), geringeres Investment. Kann auch als Standalone-Produkt oder als Feature-Modul für Sirin vermarktet werden.

### 9.2 Alternative B: RoomBook (Ressourcen-Buchung für interne Nutzung)

**Kernidee:** B2B-Buchungsplattform für interne Firmenressourcen: Meetingräume, Poolfahrzeuge, Gerätschaften (Beamer, Kamera, 3D-Drucker), gemeinsame Tools (Konferenzzimmer, Showrooms). Richtet sich an Unternehmen mit 30 bis 300 Mitarbeitenden.

**Abgrenzung zu Sirin:** Sirin adressiert externe Kunden-Buchungen. RoomBook adressiert interne Mitarbeiter-Buchungen. Unterschiedliches Datenmodell, unterschiedlicher Vertriebsweg (B2B statt B2SMB).

**V1:** Ressourcen-Katalog mit Bildern, Buchungs-Flow, Konfliktauflösung, Check-in/Check-out, Nutzungsstatistik.
**V2:** IoT-Integration (Raumbelegung durch Sensor), Auto-Freigabe bei Nichterscheinen, Empfehlungen aus Nutzungsverlauf.
**Pricing:** 3 EUR/Mitarbeiter/Monat.

**Warum verfolgbar:** 60 % technisches Fundament identisch mit Sirin, andere Zielgruppe (B2B statt Dienstleister). Kann parallel entwickelt oder als Alternative positioniert werden, falls Dienstleistungs-Markt sich als zu fragmentiert erweist.

---

## 10. Chancen und Risiken

### 10.1 Chancen

| Chance | Begründung |
|---|---|
| Strukturelle Nachfrage durch Fachkräftemangel | Betriebe müssen Zeitressourcen optimal nutzen |
| DMA-getriebene Abkehr von Marktplätzen | Doctolib & Co. verlieren Exklusivität, Endkunden suchen direkter |
| Voice- und Chat-Automation ab V2 als starker Differenzierer | 24/7-Erreichbarkeit für kleine Betriebe ohne Rezeption |
| DSGVO-Argument bei Heilberufen | Art. 9-Daten verlangen EU-Hosting — Wettbewerbsvorteil |
| Ausweitung in Vertikalen mit Vorlagen | Ein Basisprodukt für Friseur, Physio, Kosmetik, Tierarzt |

### 10.2 Risiken

| Risiko | Gegenmaßnahme |
|---|---|
| Fragmentierter Markt, teurer Vertrieb | Fokus auf 1–2 Vertikalen zuerst (Friseur + Physio), dann horizontal skalieren |
| Wechsel von bestehenden Tools schwierig | Import-Tools für Google Calendar, CSV-Import, 90-Tage-Migrations-Support |
| SMS/WhatsApp/Voice-Kosten variabel | Klare Fair-Use-Grenzen, nutzungsbasierte Overflow-Preise |
| Falsche oder zu aggressive KI-Kommunikation bei Ausfällen und Rabatten | Guardrails, Freigabe-Templates, Eskalation bei Unsicherheit, Audit-Logs |
| Zahlungs-Setup komplex (Stripe Connect für Marketplace-Szenarien) | In V1 Direct-Charge-Modell, Connect erst in V2 |
| Shore+ oder Treatwell senken Preise aggressiv | DSGVO-Argument, transparentes Flat-Pricing, kein Marktplatz-Lock-in |

---

## 11. Umsetzungsplan Version 1

### 11.1 Technologiestack

- **Frontend:** Next.js 15 (App Router), Tailwind CSS, shadcn/ui, TypeScript
- **Backend:** Supabase EU Frankfurt (PostgreSQL, RLS, Auth, Storage)
- **Payment:** Stripe (Subscriptions + Customer Payments)
- **Kalender-Integration:** Google Calendar API + Microsoft Graph
- **E-Mail:** Resend
- **SMS:** Seven.io (EU) oder Twilio EU
- **Voice und Chat (V2):** Twilio Voice oder sipgate.io, OpenAI Realtime oder Azure OpenAI, WhatsApp Business Platform über EU-BSP
- **Hosting:** Vercel fra1
- **Analytics:** Plausible (EU, cookiefrei)

### 11.2 Umsetzungsplan 5 Werktage

| Tag | Fokus | Inhalt |
|---|---|---|
| Tag 1 | Anforderungen und Architektur | Datenmodell (Organisationen, Mitarbeiter, Ressourcen, Dienstleistungen, Slots, Buchungen, Kunden), RLS-Policies, UI-Gerüst, OAuth-Konzept Google/Microsoft |
| Tag 2 | Fundament und Katalog | Vercel+Supabase-Deployment, Auth mit Multi-Tenant, Admin-UI für Mitarbeiter, Ressourcen, Dienstleistungen, Arbeitszeiten |
| Tag 3 | Buchungsflow | Öffentliche Buchungsseite mit Custom-Domain, Slot-Berechnung, Dienstleistungs-Wizard, Kundendaten-Erfassung, Bestätigung |
| Tag 4 | Kalender-Sync, Reminder, Zahlung | Google/Outlook-Sync, E-Mail-Reminder, SMS-Reminder, Ausfall- und Nachrück-Logik, „Notify me"-Opt-ins, Stripe-Integration für Anzahlung/Vollzahlung, Storno-Logik |
| Tag 5 | QA und Launch | Manuelles Testen aller Flows, Plausible-Einbindung, AGB/Datenschutzerklärung, Stripe-Abo-Integration, direkter Launch |

**Hinweis:** Analog zu den anderen Produkten liefert die 5-Tage-Umsetzung einen lauffähigen Kern. Feinschliff, Vertikal-Vorlagen (Friseur, Physio) und Performance-Optimierung folgen.

---

## 12. Marke, Branding und Marketing

### 12.1 Markenname und Bedeutung

**Sirin** leitet sich vom Bild der **Sirene** ab — und vereint damit drei Kernideen, die das Produkt im Kern beschreiben:

- **Schönheit und Behandlung.** Die Sirene steht in Mythos und Sprachgebrauch für Anziehung, Pflege und Verwandlung — exakt das Versprechen, mit dem Friseure, Kosmetikerinnen, Therapeuten, Tierärzte und Coaches ihre Kunden empfangen.
- **Gesang und Benachrichtigung.** Sirenen sind dafür bekannt, mit ihrer Stimme zu rufen. Sirin ruft im übertragenen Sinn ebenfalls: über Reminder, Ausfall-Benachrichtigungen, „freier Slot"-Pings, Voice-Agent und Chatbot. Das Produkt ist im Kern ein **Kommunikationssystem**, das aus reiner Zeitverwaltung eine geführte Beziehung macht.
- **Magische Anziehung.** Eine Sirene wird gehört — und man **will** zu ihr kommen. Genau dieser sanfte, einladende Sog ist die emotionale Differenzierung gegenüber funktionalen Wettbewerbern wie Calendly, Shore+ oder SimplyBook: Sirin verkauft nicht „Slot-Verwaltung", sondern „Lust auf den nächsten Termin".

Der Name ist kurz (5 Buchstaben), international aussprechbar, .app-/.de-/.eu-domainfähig und in DACH semantisch unbelegt — also markenrechtlich gut absicherbar (vor Eintragung formale EUIPO-/DPMA-Recherche durchführen).

### 12.2 Kleine Markt- und Positionierungsanalyse

| Markenarchetyp im Wettbewerb | Vertreter | Wirkung | Lücke |
|---|---|---|---|
| **Funktional/Tool** | Calendly, Microsoft Bookings | Effizient, generisch, kalt | Keine emotionale Bindung |
| **Marktplatz** | Treatwell, Doctolib | Reichweite, Vertrauen, aber Plattform-Look | Anbieter wird austauschbar |
| **Branchen-Software** | Shore+, fresha | Kompetent, aber technisch/POS-nah | Kein Marken-Glanz für Endkunden |
| **Premium-Beauty/Wellness** | Mindbody, Booksy | Lifestyle-Anmutung | US-Hosting, nicht DSGVO-nativ |
| **Lücke → Sirin** | — | **Warm, magisch, einladend, EU-nativ** | Bisher kein Anbieter besetzt diese Position |

Sirin positioniert sich bewusst **zwischen Tool und Lifestyle-Marke**: technisch präzise wie ein B2B-SaaS, aber emotional aufgeladen wie eine Beauty-/Wellness-Marke. Das ist die Kombination, die Endkunden zur Wiederbuchung bewegt — und die Dienstleister bereit sind, monatlich zu bezahlen, weil ihre Buchungsseite plötzlich wie ein Stück ihrer Marke wirkt, nicht wie ein generisches Formular.

### 12.3 Markenkern, Tonalität und Sprache

| Dimension | Ausprägung |
|---|---|
| **Markenversprechen** | „Sirin ruft — und du willst kommen." |
| **Werte** | Einladend · Verlässlich · Schön · Klar · Diskret |
| **Tonalität** | Warm, nahbar, leicht poetisch — ohne Esoterik. Nie technisch-trocken, nie marktschreierisch. |
| **Sprachregeln** | Du-Ansprache zu Endkunden, Sie-Ansprache zu Dienstleistern wählbar. Verben statt Nomen („Buch deinen Moment" statt „Online-Terminreservierung"). |
| **Was Sirin nicht ist** | Nicht „App", nicht „Tool", nicht „Software" — sondern **Begleiterin**. |

**Claim-Vorschläge (Auswahl):**

- **„Sirin — Hör auf deine Zeit."** (Hauptclaim, doppeldeutig: zuhören + sich Zeit nehmen)
- „Sirin — Termine, die rufen."
- „Sirin — Damit dein nächster Termin dich findet."
- B2B-Variante: „Sirin — Die Stimme deines Salons."

### 12.4 Visuelle Identität

| Element | Empfehlung | Begründung |
|---|---|---|
| **Primärfarbe** | Tiefes Marine-Aqua `#0E3A5F` → `#1F7A8C` | Wasser, Tiefe, Sirenen-Welt; gleichzeitig vertrauenswürdig (Healthcare-tauglich) |
| **Akzentfarbe** | Warmes Honig-Gold `#E6B566` | Wärme, Schönheit, „magisches Leuchten" — unterscheidet von kühlen Tech-Marken |
| **Sekundär** | Sand `#F5EFE6`, Schiefer `#5A6B7B` | Ruhige Flächen, Lesbarkeit |
| **Typografie Headline** | Serif mit weichen Schwüngen (z. B. *Playfair Display*, *Cormorant Garamond*) | Emotional, schön, nicht beliebig |
| **Typografie Body** | Humanistische Sans (z. B. *Inter*, *Söhne*, *Manrope*) | Klar, lesbar, modern |
| **Bildwelt** | Nahaufnahmen von Händen, Werkzeugen, Licht, Wasseroberflächen — **keine** generischen Stockfoto-Lächel-Models | Atmosphäre statt Klischee |
| **Bewegung** | Sanfte Wellen-Animation beim Laden, weiche Übergänge | Spürbarer Charakter ohne Verspieltheit |
| **Sound-Logo (für Voice-Agent)** | 3-Ton-Motiv, aufsteigend, harfen-/glasartig | Macht den Voice-Agent zur Marken-Erfahrung — eigenes Brand Asset |

### 12.5 Logo-System (3 Darstellungen)

Das Logo basiert auf zwei Grundideen: **Klangwellen** (Sirenenruf, Benachrichtigung) und **Tropfen/Welle** (Wasser, Sirenenwelt). Beide werden je nach Kontext kombiniert oder isoliert eingesetzt.

**Hauptlogo — Wortmarke mit Klangwellen und Tropfen-i**
*(siehe Kopf des Dokuments)*
Einsatz: Website-Header, Pitch Deck, Briefkopf, Anbieter-Buchungsseite-Footer.

**Alternative 1 — App-Icon / Monogramm „S" als Welle**

<p align="center">
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 160 160" width="140" height="140" role="img" aria-label="Sirin App-Icon">
  <defs>
    <linearGradient id="sirinIconGrad" x1="0" y1="0" x2="1" y2="1">
      <stop offset="0%" stop-color="#0E3A5F"/>
      <stop offset="100%" stop-color="#1F7A8C"/>
    </linearGradient>
  </defs>
  <rect x="0" y="0" width="160" height="160" rx="36" ry="36" fill="url(#sirinIconGrad)"/>
  <!-- Stilisiertes S als doppelte Welle -->
  <path d="M48 55 C 70 35, 100 35, 118 55 C 100 70, 70 70, 48 90 C 70 110, 100 110, 118 105"
        fill="none" stroke="#F5EFE6" stroke-width="10" stroke-linecap="round"/>
  <!-- Tropfen / goldener Akzent -->
  <circle cx="118" cy="120" r="7" fill="#E6B566"/>
</svg>
</p>

Einsatz: App-Icon (iOS/Android Web-App-Bookmark), Favicon, Social-Media-Avatar, WhatsApp-Business-Profilbild, Voice-Agent-Sprecherbild.

**Alternative 2 — Bildmarke „Sirenen-Silhouette aus Klangwellen"**

<p align="center">
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 200 160" width="200" height="160" role="img" aria-label="Sirin Bildmarke">
  <defs>
    <linearGradient id="sirinFigGrad" x1="0" y1="0" x2="0" y2="1">
      <stop offset="0%" stop-color="#1F7A8C"/>
      <stop offset="100%" stop-color="#0E3A5F"/>
    </linearGradient>
  </defs>
  <!-- Konzentrische Klangkreise (der Ruf) -->
  <g fill="none" stroke="#E6B566" stroke-width="2" opacity="0.7">
    <circle cx="100" cy="80" r="70"/>
    <circle cx="100" cy="80" r="55" opacity="0.55"/>
    <circle cx="100" cy="80" r="40" opacity="0.35"/>
  </g>
  <!-- Stilisierte weibliche Figur / Sirene aus zwei geschwungenen Linien (Kopf + fließender Körper als Welle) -->
  <circle cx="100" cy="55" r="10" fill="url(#sirinFigGrad)"/>
  <path d="M100 67 C 80 80, 120 95, 100 110 C 80 125, 120 135, 100 145"
        fill="none" stroke="url(#sirinFigGrad)" stroke-width="6" stroke-linecap="round"/>
</svg>
</p>

Einsatz: Editorial / Storytelling (Landingpage-Hero, Print-Anzeige, Messe-Backdrop). Bewusst poetischer als Hauptlogo — wird sparsam eingesetzt, um die emotionale Markenebene zu zeigen.

### 12.6 Anwendungsfelder und Markenerlebnis

| Touchpoint | Markenausprägung |
|---|---|
| **Anbieter-Buchungsseite (Endkunden-Flow)** | Wortmarke im Header, sanfte Wellen-Animation beim Slot-Laden, Honig-Gold-Akzente auf CTA-Buttons („Termin sichern") |
| **Voice-Agent (KI-07)** | 3-Ton-Sound-Logo bei Gesprächsbeginn, ruhige weibliche Stimme mit warmer Intonation, Begrüßung enthält Markenmotiv („Schön, dass Sie anrufen — ich höre Sie.") |
| **WhatsApp-Chatbot (KI-08)** | App-Icon als Profilbild, kurze, warme Antworten, Du-Ansprache, Emojis sparsam (Welle, Stern) |
| **Reminder-E-Mail / SMS** | Subjektzeile poetisch („Morgen wartet dein Moment bei Julia"), nicht generisch („Erinnerung: Termin morgen 14 Uhr") |
| **Lückenfüller-Push (SR-09/KI-09)** | „Ein Slot ruft dich — heute 16:30 bei Marcus, mit 15 % Wohlfühl-Rabatt." |
| **Admin-Dashboard (für Dienstleister)** | Reduzierter, professioneller Look — Wortmarke schlicht, Funktion vor Emotion. Markenwärme bleibt in der Endkunden-Schicht. |

### 12.7 Markenführung und nächste Schritte

1. **Markenrechtliche Prüfung** Sirin / Sirin.app / Sirin Booking bei DPMA und EUIPO (Klasse 9, 35, 42).
2. **Domain-Sicherung** sirin.app, sirin-booking.de, sirin.eu.
3. **Sound-Logo-Produktion** mit kleinem Audio-Studio (Budget-Rahmen 800–1.500 EUR).
4. **Brand-Guideline-Onepager** (Farben, Typo, Logo-Schutzräume, Tonalität, Beispiele „so / nicht so") als internes Asset für Marketing, Voice-Agent-Prompting und Vertriebsmaterial.
5. **Pilot-Anbieter-Buchungsseite** als Referenz-Showcase für Vertrieb (1 Friseur + 1 Physio).

---

## Quellenverzeichnis

| Quelle | Inhalt |
|---|---|
| Mordor Intelligence — Appointment Scheduling Software Market 2026 | 5,3 Mrd. USD 2025, CAGR 13–14 %, mordorintelligence.com |
| Grand View Research — Online Booking Software Market Update 2026 | Wachstumsdynamik Online-Buchung, grandviewresearch.com |
| Bitkom Digital Office Survey 2026 | Erwartung Online-Buchbarkeit und Sofortbestätigung, bitkom.org |
| Statista Consumer Services DACH 2026 | Online-Terminbuchung und Messenger-Präferenz, statista.com |
| Bundesagentur für Arbeit — Fachkräftereport 2026 | Besetzungslücke im Service-Sektor, arbeitsagentur.de |
| EURES Services Snapshot 2025 | Fachkräfteengpässe in DACH-Serviceberufen, eures.europa.eu |
| ZV Friseurhandwerk — Kostenmonitor 2025 | Wirtschaftsdaten und Kostenstruktur Salons |
| Salonized Industry Report 2026 | Last-minute cancellations und Auslastungsprobleme in Service-Betrieben |
| ZV Friseurhandwerk — Strukturdaten 2025 | 121.000 Betriebe DACH |
| GKV-Heilmittelerbringer-Statistik 2025 | Physio-, Ergo-, Logopädie-Praxen |
| BTK — Tierärzte-Jahresbericht 2025 | 14.500 Praxen DACH |
| BDH — Heilpraktiker Strukturdaten 2025 | 46.000 DACH |
| EU-DSGVO Art. 9 | Besondere Kategorien personenbezogener Daten, eur-lex.europa.eu |
| DMA (Digital Markets Act, VO 2022/1925) | Marktplatz-Regulierung |
| Meta WhatsApp Business Platform Policy 2026 | API-Nutzungsregeln |
| OpenAI Realtime API / Voice Update 2025 | Echtzeit-Voice- und Conversational-AI-Bausteine |
| Microsoft Copilot Studio Voice 2026 | Voice-Agent-Konzept und Telefonie-Orchestrierung |
| G2 — Appointment Scheduling Category April 2026 | Wettbewerbsvergleich |
| Capterra — Online Booking Software 2026 | Marktübersicht |
| GetApp SMB Scheduling Benchmark 2025 | KMU-Anforderungen an Buchungssoftware |

---

*Dokument erstellt: 25. April 2026 | Version 1.0 | Autor: Daniel Moretz | Status: Zur Freigabe eingereicht*
*Alle Marktdaten basieren auf zum Erstellungszeitpunkt öffentlich verfügbaren Quellen. Für bindende rechtliche Aussagen (DSGVO, Steuerrecht, Widerrufsrecht) ist juristischer Beistand erforderlich.*

## ./HOWTO.md
# HOWTO — Project Setup & Deployment Guide

> 🎉 **Herzlichen Glückwunsch zur Einrichtung! / Congratulations on setting up!**
> Du kannst dieses Dokument nach Abschluss der Einrichtung löschen oder als Referenz behalten.
> You can delete this HOWTO document once your setup is complete, or keep it for future reference.

> 📖 **Lies die [AGENTS.md](AGENTS.md) Datei, um GitHub Copilot optimal und produktiv zu nutzen.**
> **Read the [AGENTS.md](AGENTS.md) file to use GitHub Copilot in an optimised and productive way.**

---

## DE Deutsch

---

### Prozessübersicht

Folge diesen Schritten in der angegebenen Reihenfolge, um vom Template zur Produktion zu gelangen:

1. **GitHub Repo erstellen** — Nutze dieses Template, um ein neues Repository in der Wamocon GitHub Organisation zu erstellen.
2. **Repo klonen** — Klone es auf deinen Rechner und führe `npm install` aus.
3. **Pre-commit Hook installieren** — Führe `bash hooks/install.sh` aus. Einmalig nach dem Klonen — schützt dich davor, Geheimnisse versehentlich zu pushen.
4. **GitHub Workflow-Datei überprüfen** — Öffne `.github/workflows/deploy.yml` und `.github/workflows/pr-pipeline.yml`, überprüfe, dass `Wamocon/github_workflow` die korrekte Referenz ist.
5. **`.env.local` aktualisieren & Supabase verbinden** — Kopiere `.env.example` → `.env.local`, erstelle ein Remote-Supabase-Projekt und trage die Zugangsdaten ein.
6. **Lokal starten & Entwicklung beginnen** — Führe `npm run dev` aus und beginne mit der Entwicklung.
7. **GitHub-Organisationseinstellungen: Vercel-App Zugriff gewähren** — Gehe zu den Organisationseinstellungen auf GitHub, suche die Vercel GitHub-App und gewähre ihr Zugriff auf dein neues Repo. Nur so erscheint das Repo in der Vercel-Importliste.
8. **Repo vorübergehend öffentlich machen & bei Vercel importieren** — Stelle das Repo temporär auf öffentlich und importiere es in Vercel.
9. **Vercel Project ID holen** — Kopiere die Vercel Project ID aus den Vercel-Projekteinstellungen.
10. **Vercel Project ID zu GitHub Secrets hinzufügen** — Füge `VERCEL_PROJECT_ID` zu den GitHub Actions Secrets deines Repos hinzu.
11. **Repo auf intern umstellen** — Ändere die Sichtbarkeit des Repos zurück auf intern.
12. **Erstes manuelles Deployment** — Gehe zu `Actions → "Deploy to Vercel" → Run workflow` und wähle `production`.

> 📖 **Für detaillierte Informationen, lies weiter unten.**

---

### 1. Klonen & Einrichten

```bash
# Repository klonen
git clone https://github.com/Wamocon/<dein-repo-name>.git
cd <dein-repo-name>

# Abhängigkeiten installieren
npm install

# Umgebungsvariablen kopieren
cp .env.example .env.local

# Pre-commit Hook installieren (einmalig, direkt nach npm install)
bash hooks/install.sh

# Entwicklungsserver starten (mit Turbopack für schnelles Hot-Reload)
npm run dev
```

Öffne [http://localhost:3000](http://localhost:3000) in deinem Browser.

**Verfügbare Skripte:**

| Befehl | Beschreibung |
|---|---|
| `npm run dev` | Startet den Dev-Server mit Turbopack (Hot Reload) |
| `npm run build` | Erstellt den Produktions-Build |
| `npm run start` | Startet den Produktionsserver |
| `npm run lint` | Führt ESLint aus |
| `npm run typecheck` | Führt TypeScript-Typprüfung aus |

---

### 1b. Git-Workflow & Branch-Strategie

> 💡 **Arbeite nach dem ersten Push immer auf einem Branch — nie direkt auf `main`/`master`.**

**Empfohlener Ablauf:**

```bash
# Einmalig: Ersten Stand auf main/master pushen
git add .
git commit -m "chore: initial setup"
git push origin <main-oder-master>

# Ab jetzt: Immer auf einem Feature-Branch arbeiten
git checkout -b feature/mein-feature

# Änderungen lokal testen, dann committen
npm run dev        # testen
npm run typecheck  # Typfehler prüfen
npm run lint       # Lint prüfen

git add .
git commit -m "feat: beschreibung der Änderung"
git push origin feature/mein-feature
```

**Wichtige Regeln:**

- **Lokal testen, bevor du pushst.** Führe `npm run typecheck` und `npm run lint` aus, bevor du Änderungen pushst.
- **Alle Änderungen vor dem PR-Öffnen pushen.** Jeder neue Push auf einen offenen PR triggert automatisch die GitHub Actions — das verbraucht GitHub Actions-Minuten.
- **Nur einen PR auf einmal offen halten**, bis er gemergt ist.

> ⚠️ **Warum das wichtig ist:** Jeder Push auf einen offenen PR löst die PR Pipeline aus (Auto-Fix + Typecheck + Lint). Teste erst lokal — dann push, dann PR.

---

### 1c. Pre-commit Hook — Geheimnis-Scanner

Der Pre-commit Hook verhindert, dass API-Schlüssel, Tokens, Passwörter oder andere Geheimnisse versehentlich in GitHub eingecheckt werden. Der Hook scannt alle für den Commit vorgesehenen Dateien, **bevor** der Commit abgeschlossen wird.

#### Installation

```bash
# Einmalig nach dem Klonen ausführen — nie wieder nötig:
bash hooks/install.sh
```

> ✅ **Wie oft?** Genau **einmal** — direkt nach `npm install` beim ersten Einrichten des Repos. Nach der Installation läuft der Hook automatisch vor **jedem** `git commit`.

#### Was der Hook prüft

| Muster | Beispiel |
|--------|---------|
| AWS-Schlüssel | `AKIA...`, `aws_secret_access_key = ...` |
| GitHub-Tokens | `ghp_...`, `github_pat_...` |
| Vercel-Token | `VERCEL_TOKEN = abc123...` |
| Private Keys (PEM) | `-----BEGIN PRIVATE KEY-----` |
| Datenbankverbindungen | `postgres://user:password@host` |
| Generische Tokens | `api_key =`, `client_secret =`, `password =` |
| JWT-Tokens | `eyJ...` (vollständige `header.payload.signature`-Form) |
| Supabase Service Role | `service_role = eyJ...` |
| `.env`-Dateien | `.env`, `.env.local`, `.env.production` |

#### Wenn ein Commit blockiert wird

```
[pre-commit] BLOCKED — potential secrets detected
  ✖ src/lib/config.ts:12
    Reason: Generic API key
    Content: const API_KEY = "abc123xyz789..."
```

**Lösung:**
1. Entferne das Geheimnis aus der Datei.
2. Speichere es in deiner `.env.local` (ist bereits in `.gitignore` eingetragen).
3. Nutze GitHub Actions Secrets für CI/CD-Werte.

**Bei einem Falsch-Positiv** (z.B. ein Beispielwert in der Doku):
Füge den Kommentar `# notsecret` am Ende der betroffenen Zeile hinzu.

**Notfall-Bypass** (nur im absoluten Ausnahmefall — niemals für echte Geheimnisse!):
```bash
git commit --no-verify -m "deine Nachricht"
```

---

### 2. Supabase Setup & Warnung

> ⚠️ **KRITISCH: Sobald du einen Supabase-Account hast, speichere alle Testdaten direkt dort.**
>
> **Lege Testdaten NICHT als lokale Dateien im Projektverzeichnis ab** (z.B. JSON-Fixtures, SQL-Dumps). Füge Daten stattdessen direkt in dein Supabase-Projekt ein — über das Dashboard, per MCP-Tool oder per Migrations-Skript.

**Schritte:**

1. Gehe zu [supabase.com](https://supabase.com) und erstelle ein neues Projekt.
2. Kopiere die **Project URL**, den **Anon Key** und den **Service Role Key** aus  
   `Project Settings → API`.
3. Trage sie in deine `.env.local` Datei ein:
   ```
   NEXT_PUBLIC_SUPABASE_URL=https://your-project-ref.supabase.co
   NEXT_PUBLIC_SUPABASE_ANON_KEY=dein-anon-key
   SUPABASE_SERVICE_ROLE_KEY=dein-service-role-key
   ```

---

### 2b. Lokales Supabase Setup via Docker (Optional)

> 💡 **Dieser Schritt ist optional.** Standardmäßig verbindest du dich direkt mit einem Remote-Supabase-Projekt (siehe Abschnitt 2). Nur wenn du lieber vollständig lokal entwickelst, ohne Internetverbindung zu Supabase, verwende dieses Setup.

Für ein vollständig lokales Supabase-Setup mit Docker und einer migrations-basierten Entwicklung, kopiere diesen Prompt in deinen KI-Assistenten (z.B. GitHub Copilot in VS Code):

```
Act as an expert DevOps and database engineer. I am developing an app locally. I need to set up a local Supabase instance via Docker and establish a strict migration-based workflow. Please execute the following:

Setup: Initialize a local Supabase environment using Docker and the Supabase CLI. Check automatically before every task if Docker and the Supabase containers are running. When they are down, start them autonomously.

Initial Schema: Create the initial database schema for the app and save it as a formal Supabase migration file.

Environment Variables: Automatically extract the local Supabase connection details (API URL, anon key, service role key, DB URL) and append them to my local .env file.

Autonomous Development & Schema Versioning: You will develop the entire application based on my prompts. You must autonomously create and update tables, generate schemas, and create timestamped migration files for every change. Ensure strict version history and guarantee that absolutely no functions fail due to database inconsistencies.

Production Deployment via MCP: I use the Supabase MCP to push data to production tables. Do not provide manual push commands. Your only job for production is to verify that all local migrations are completely up to date and error-free so the MCP can handle the live deployment seamlessly.

Automated Testing & Verification: Once the Docker setup is running and the schema is applied, automatically write and execute a small integration test. This test must verify that the app can successfully read from and write to the local Docker database. If any errors or bugs are detected, diagnose and fix them immediately on your own.
```

#### Lokale Supabase-Oberfläche im Browser öffnen

Sobald der lokale Docker-Stack läuft (`npx supabase start`), stellt Supabase eine vollständige Studio-Oberfläche bereit:

| Service | URL | Beschreibung |
|---|---|---|
| **Supabase Studio** | `http://localhost:54323` | Datenbank-UI: Tabellen, SQL-Editor, Auth, Storage |
| **REST API** | `http://localhost:54321` | PostgREST API (dein App-Endpoint) |
| **PostgreSQL** | `localhost:54322` | Direktzugriff (z.B. via pgAdmin, TablePlus) |
| **Inbucket (E-Mail)** | `http://localhost:54324` | Lokaler E-Mail-Dienst für Auth-Mails |

> 💡 Die exakten Ports werden nach `npx supabase start` auch in der Konsole ausgegeben. Der Befehl `npx supabase status` zeigt sie jederzeit an.

**Lokale Umgebungsvariablen:**
```
NEXT_PUBLIC_SUPABASE_URL=http://localhost:54321
NEXT_PUBLIC_SUPABASE_ANON_KEY=<aus supabase status kopieren>
SUPABASE_SERVICE_ROLE_KEY=<aus supabase status kopieren>
SUPABASE_DB_URL=postgresql://postgres:postgres@localhost:54322/postgres
```

---

### 3. Supabase MCP & Schemas

#### Supabase MCP für Migrationen verwenden

Der Supabase MCP (Model Context Protocol) Server ermöglicht es deinem KI-Coding-Assistenten (z.B. GitHub Copilot, Cursor), Migrationen und Tabellen direkt zu erstellen und zu verwalten.

- Migrationen werden in `supabase/migrations/` gespeichert.
- Nutze die MCP-Tools, um Tabellen zu erstellen, Schemas zu ändern und Indizes zu verwalten.

#### Arbeiten mit mehreren Schemas

Standardmäßig macht Supabase nur das `public`-Schema über die API verfügbar. Wenn du eigene Schemas brauchst:

**1. Schema erstellen:**
```sql
CREATE SCHEMA IF NOT EXISTS app;
```

**2. Berechtigungen vergeben:**
```sql
GRANT USAGE ON SCHEMA app TO anon, authenticated, service_role;
GRANT ALL ON ALL TABLES IN SCHEMA app TO anon, authenticated, service_role;
ALTER DEFAULT PRIVILEGES IN SCHEMA app
  GRANT ALL ON TABLES TO anon, authenticated, service_role;
GRANT ALL ON ALL SEQUENCES IN SCHEMA app TO anon, authenticated, service_role;
ALTER DEFAULT PRIVILEGES IN SCHEMA app
  GRANT ALL ON SEQUENCES TO anon, authenticated, service_role;
```

**3. Schema über die Supabase API zugänglich machen:**
Gehe zu `Project Settings → API → Exposed schemas` und füge deinen Schema-Namen hinzu.

---

### 4. GitHub Workflow Konfiguration

Dieses Projekt nutzt den **zentralen Wamocon CI/CD-Workflow** aus [`Wamocon/github_workflow`](https://github.com/Wamocon/github_workflow).

#### Übersicht der drei Workflows

| Workflow | Datei | Auslöser | Was es tut |
|---|---|---|---|
| **PR Pipeline** | `pr-pipeline.yml` | **Automatisch** bei jedem PR auf `main`/`master` | Auto-Fix (ESLint + Prettier) → Typecheck + Lint |
| **Deploy** | `deploy.yml` | **Manuell** — kein Auto-Trigger | Baut das Projekt via Vercel CLI und deployed auf Vercel |
| **LP Generator** | `lp-generator.yml` | **Manuell** — kein Auto-Trigger | Generiert eine Landing Page in einem neuen Repo |

> ⚠️ **Kein automatisches Deployment:** Weder ein PR noch ein Push auf `main` startet automatisch ein Deployment. Alle Deployments werden manuell über den Actions-Tab gestartet.

#### Was du tun musst

1. Überprüfe, dass `Wamocon/github_workflow` die korrekte Org/Repo-Referenz ist.
2. Aktiviere Workflow-Schreibrechte:  
   `Settings → Actions → General → Workflow permissions → Allow GitHub Actions to create and approve pull requests`
3. Füge **ein einziges Secret** zu deinem Repository hinzu:
   - Gehe zu `Repository → Settings → Secrets and variables → Actions → New repository secret`
   - Name: `VERCEL_PROJECT_ID`
   - Wert: *(siehe Abschnitt 5 unten)*

> ✅ **Alle anderen benötigten Secrets** (`VERCEL_TOKEN`, `VERCEL_ORG_ID`) sind **bereits auf GitHub-Organisationsebene konfiguriert**.

#### Manuelles Deployment starten

```
Repository auf GitHub → Actions → "Deploy to Vercel" → Run workflow
→ Environment auswählen: production oder preview
→ Run workflow klicken
```

---

### 5. Vercel Deployment-Strategie

#### Schritt 1: GitHub-Org Vercel-App Zugriff gewähren (Einmalig, Kritisch)

> ⚠️ **Dieser Schritt muss VOR dem Vercel-Import durchgeführt werden.** Ohne ihn erscheint dein Repo nicht in der Vercel-Importliste — auch wenn es öffentlich ist.

1. Gehe zu **GitHub → Wamocon Organisation → Settings**  
   `https://github.com/organizations/Wamocon/settings/installations`
2. Suche die **Vercel**-App in der Liste der installierten GitHub Apps.
3. Klicke auf **Configure**.
4. Scrolle zu **Repository access**.
5. Wähle **"Only select repositories"** und füge dein neues Repo hinzu.
6. Klicke **Save**.

#### Schritt 2: Erstmalige Bereitstellung (Einmalig)

1. **Repo vorübergehend öffentlich machen**  
   `Repository → Settings → General → Change visibility → Public`
2. Gehe zu [vercel.com](https://vercel.com) → **Add New Project** → **Import** → dein Repo auswählen.
3. Deploye das Projekt (Vercel erkennt Next.js automatisch).
4. **Vercel Project ID kopieren:**  
   `Vercel Project → Settings → General → Project ID` → ID kopieren.
5. **Zu GitHub Secrets hinzufügen:**  
   `Repository → Settings → Secrets and variables → Actions → New repository secret`  
   Name: `VERCEL_PROJECT_ID` | Wert: die kopierte ID.
6. **Repo auf intern zurücksetzen:**  
   `Repository → Settings → General → Change visibility → Internal`

> 💡 **Nach diesem einmaligen Setup** deployt die GitHub Action via Vercel CLI — Vercel sieht nicht mehr, wer committed, und es gibt keine Team-Seat-Fehler bei einem privaten Hobby-Account.

#### Schritt 3: Umgebungsvariablen in Vercel eintragen

> ⚠️ **WICHTIG:** Gehe zu `Vercel Project → Settings → Environment Variables` und füge **alle** Variablen aus deiner `.env.local` hinzu. Ohne diese wird der Build **fehlschlagen**.

#### Deployment-Ablauf (nach dem Setup)

| Auslöser | Ergebnis |
|---|---|
| PR auf `main`/`master` | PR Pipeline läuft automatisch (kein Deployment) |
| Merge auf `main`/`master` | Kein automatisches Deployment |
| **Manuelles Workflow-Start** | Deployment nach Auswahl: `production` oder `preview` |

**Manuell deployen:**

```
GitHub → Actions → "Deploy to Vercel" → Run workflow
→ environment: production  (für die Live-URL)
→ environment: preview     (für eine Test-URL)
→ db_schema: (leer lassen — Vercel-Umgebungsvariablen werden genutzt)
```

---

### 6. Domain-Verwaltung

1. **Sichere eine Domain** für deine Anwendung über [Strato](https://www.strato.de).
2. Gehe in den Vercel-Projekteinstellungen zu `Settings → Domains` und füge deine Domain hinzu.
3. Konfiguriere die DNS-Einträge bei Strato wie von Vercel angegeben (typischerweise CNAME oder A-Record).

---

### 7. Projekt-Checkliste

- [ ] Landing Page
- [ ] Handbuch / Manual
- [ ] Hauptprozess (Kernfunktion)
- [ ] Video (Demo / Tutorial)
- [ ] Domain (über Strato gesichert)

---

### 8. Landing Page Generator

Das Workflow-File `.github/workflows/lp-generator.yml` generiert eine Landing Page für diese App.

#### Was der Workflow tut

- Liest den Inhalt dieses Repos aus
- Verwendet ein konfigurierbares **Design-Template** als optische Basis
- Lässt GitHub Copilot eine Landing Page generieren und ein neues Repo dafür anlegen

#### Was du ändern kannst

| Eingabe | Standard | Beschreibung |
|---|---|---|
| `custom_template` | `Wamocon/hochzeitsrechner_lp` | Das GitHub-Repo, das als Design-Template dient |
| `custom_name` | `generated_lp` | Name des neu erstellten Landing-Page-Repos |
| `custom_prompt` | *(allgemeiner Prompt)* | Detaillierte Anweisungen für Copilot |

> 💡 **Tipp:** Je spezifischer dein Prompt, desto besser die generierte Landing Page.

#### Wann du den Workflow starten sollst

Starte diesen Workflow **erst dann**, wenn dein Projekt weitgehend fertig dokumentiert ist:
- Handbuch / Manual
- README mit Produktbeschreibung, Features und Zielgruppe
- Rechtstexte / relevante Seiten

> ✅ **Empfehlung:** In der Regel reicht **ein einmaliger Lauf** am Projektende.

#### Manuell ausführen

`Repository → Actions → "🚀 lp-generator" → Run workflow`

1. Wähle in der linken Liste den Workflow **"🚀 lp-generator"**.
2. Klicke rechts auf **"Run workflow"**.
3. Passe Template, Name und Prompt an.
4. Bestätige mit **"Run workflow"**.

#### Wenn der Workflow fehlschlägt

Wenn bereits ein Repository mit gleichem Namen existiert:
1. Ändere den Namen in `custom_name` und starte erneut.
2. Oder lösche das bestehende Ziel-Repo und starte erneut.

---
---

## EN English

---

### Process Overview

Follow these steps in order to go from template to production:

1. **Create GitHub Repo** — Use this template to create a new repository in the Wamocon GitHub organisation.
2. **Clone Repo** — Clone to your local machine and run `npm install`.
3. **Install pre-commit hook** — Run `bash hooks/install.sh`. One-time setup after cloning — protects you from accidentally pushing secrets.
4. **Check GitHub Workflow files** — Open `.github/workflows/deploy.yml` and `.github/workflows/pr-pipeline.yml`, verify that `Wamocon/github_workflow` is the correct reference.
5. **Update `.env.local` & connect Supabase** — Copy `.env.example` → `.env.local`, create a remote Supabase project, and fill in the credentials.
6. **Run locally & start development** — Run `npm run dev` and start building.
7. **GitHub Organisation Settings: Grant Vercel app access** — Go to the organisation settings on GitHub, find the Vercel GitHub App, and grant it access to your new repo. Without this, the repo will not appear in Vercel's import list.
8. **Make repo temporarily public & import in Vercel** — Set the repo to public temporarily and import it in Vercel.
9. **Get Vercel Project ID** — Copy the Vercel Project ID from the Vercel project settings.
10. **Add Vercel Project ID to GitHub secrets** — Add `VERCEL_PROJECT_ID` to your repository's GitHub Actions secrets.
11. **Make repo internal** — Revert the repository visibility to internal.
12. **First manual deployment** — Go to `Actions → "Deploy to Vercel" → Run workflow` and choose `production`.

> 📖 **For detailed information, read below.**

---

### 1. Clone & Setup

```bash
# Clone the repository
git clone https://github.com/Wamocon/<your-repo-name>.git
cd <your-repo-name>

# Install dependencies
npm install

# Copy environment variables
cp .env.example .env.local

# Install pre-commit hook (once, right after npm install)
bash hooks/install.sh

# Start the development server (with Turbopack for fast refresh)
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

**Available scripts:**

| Command | Description |
|---|---|
| `npm run dev` | Start dev server with Turbopack (hot reload) |
| `npm run build` | Create production build |
| `npm run start` | Start production server |
| `npm run lint` | Run ESLint |
| `npm run typecheck` | Run TypeScript type checking |

---

### 1b. Git Workflow & Branching Strategy

> 💡 **After the first push, always work on a branch — never directly on `main`/`master`.**

**Recommended flow:**

```bash
# One-time: push the initial state to main/master
git add .
git commit -m "chore: initial setup"
git push origin <main-or-master>

# From now on: always work on a feature branch
git checkout -b feature/my-feature

# Test locally, then commit
npm run dev        # test in browser
npm run typecheck  # catch type errors
npm run lint       # catch lint issues

git add .
git commit -m "feat: description of change"
git push origin feature/my-feature
```

**Key rules:**

- **Test locally before pushing.** Always run `npm run typecheck` and `npm run lint` before pushing.
- **Push all changes before opening the PR.** Every new push to an open PR triggers the GitHub Actions pipeline — this consumes GitHub Actions minutes.
- **Keep only one PR open at a time** until it is merged.

> ⚠️ **Why this matters:** Every push to an open PR triggers the PR Pipeline (Auto-Fix + Typecheck + Lint). Test locally first — then push, then open the PR.

---

### 1c. Pre-commit Hook — Secret Scanner

The pre-commit hook prevents API keys, tokens, passwords, or other secrets from accidentally being checked into GitHub. The hook scans all files staged for commit **before** the commit is finalised.

#### Installation

```bash
# Run ONCE after cloning — never needs to run again:
bash hooks/install.sh
```

> ✅ **How often?** Exactly **once** — right after `npm install` when first setting up the repo. After installation, the hook runs automatically before **every** `git commit`.

#### What the hook checks

| Pattern | Example |
|--------|---------|
| AWS keys | `AKIA...`, `aws_secret_access_key = ...` |
| GitHub tokens | `ghp_...`, `github_pat_...` |
| Vercel token | `VERCEL_TOKEN = abc123...` |
| Private keys (PEM) | `-----BEGIN PRIVATE KEY-----` |
| Database connection strings | `postgres://user:password@host` |
| Generic tokens | `api_key =`, `client_secret =`, `password =` |
| JWT tokens | `eyJ...` (full `header.payload.signature` form) |
| Supabase service role | `service_role = eyJ...` |
| `.env` files | `.env`, `.env.local`, `.env.production` |

#### When a commit is blocked

```
[pre-commit] BLOCKED — potential secrets detected
  ✖ src/lib/config.ts:12
    Reason: Generic API key
    Content: const API_KEY = "abc123xyz789..."
```

**How to fix:**
1. Remove the secret from the file.
2. Store it in your `.env.local` (already in `.gitignore`).
3. Use GitHub Actions secrets for CI/CD values.

**False positive** (e.g. an example value in documentation):  
Add the comment `# notsecret` at the end of that line.

**Emergency bypass** (absolute last resort — never for real secrets!):
```bash
git commit --no-verify -m "your message"
```

---

### 2. Supabase Setup & Warning

> ⚠️ **CRITICAL: Once you have a Supabase account, store all test data there directly.**
>
> **Do NOT store test data as local files** (e.g. JSON fixtures, SQL dumps). Insert data directly into your Supabase project — via the Dashboard, an MCP tool, or a migration script.

**Steps:**

1. Go to [supabase.com](https://supabase.com) and create a new project.
2. Copy the **Project URL**, **Anon Key**, and **Service Role Key** from  
   `Project Settings → API`.
3. Paste them into your `.env.local` file:
   ```
   NEXT_PUBLIC_SUPABASE_URL=https://your-project-ref.supabase.co
   NEXT_PUBLIC_SUPABASE_ANON_KEY=your-anon-key
   SUPABASE_SERVICE_ROLE_KEY=your-service-role-key
   ```

---

### 2b. Local Supabase Setup via Docker (Optional)

> 💡 **This step is optional.** By default you connect directly to a remote Supabase project (see section 2). Only use this setup if you prefer developing fully offline.

For a fully local Supabase setup with Docker and a migration-based development workflow, copy this prompt into your AI assistant (e.g. GitHub Copilot in VS Code):

```
Act as an expert DevOps and database engineer. I am developing an app locally. I need to set up a local Supabase instance via Docker and establish a strict migration-based workflow. Please execute the following:

Setup: Initialize a local Supabase environment using Docker and the Supabase CLI. Check automatically before every task if Docker and the Supabase containers are running. When they are down, start them autonomously.

Initial Schema: Create the initial database schema for the app and save it as a formal Supabase migration file.

Environment Variables: Automatically extract the local Supabase connection details (API URL, anon key, service role key, DB URL) and append them to my local .env file.

Autonomous Development & Schema Versioning: You will develop the entire application based on my prompts. You must autonomously create and update tables, generate schemas, and create timestamped migration files for every change. Ensure strict version history and guarantee that absolutely no functions fail due to database inconsistencies.

Production Deployment via MCP: I use the Supabase MCP to push data to production tables. Do not provide manual push commands. Your only job for production is to verify that all local migrations are completely up to date and error-free so the MCP can handle the live deployment seamlessly.

Automated Testing & Verification: Once the Docker setup is running and the schema is applied, automatically write and execute a small integration test. This test must verify that the app can successfully read from and write to the local Docker database. If any errors or bugs are detected, diagnose and fix them immediately on your own.
```

#### Viewing the local database in the browser

| Service | URL | Description |
|---|---|---|
| **Supabase Studio** | `http://localhost:54323` | Database UI: tables, SQL editor, Auth, Storage |
| **REST API** | `http://localhost:54321` | PostgREST API (your app endpoint) |
| **PostgreSQL** | `localhost:54322` | Direct DB access (e.g. pgAdmin, TablePlus) |
| **Inbucket (email)** | `http://localhost:54324` | Local email service for Auth emails |

**Local environment variables:**
```
NEXT_PUBLIC_SUPABASE_URL=http://localhost:54321
NEXT_PUBLIC_SUPABASE_ANON_KEY=<copy from supabase status output>
SUPABASE_SERVICE_ROLE_KEY=<copy from supabase status output>
SUPABASE_DB_URL=postgresql://postgres:postgres@localhost:54322/postgres
```

---

### 3. Supabase MCP & Schemas

#### Using Supabase MCP for Migrations

The Supabase MCP (Model Context Protocol) server allows your AI coding assistant to create and manage migrations and tables directly.

- Migrations are stored in `supabase/migrations/`.
- Use the MCP tools to create tables, alter schemas, and manage indexes.

#### Working with Multiple Schemas

By default, Supabase only exposes the `public` schema via the API. If you need custom schemas:

**1. Create the schema:**
```sql
CREATE SCHEMA IF NOT EXISTS app;
```

**2. Grant permissions:**
```sql
GRANT USAGE ON SCHEMA app TO anon, authenticated, service_role;
GRANT ALL ON ALL TABLES IN SCHEMA app TO anon, authenticated, service_role;
ALTER DEFAULT PRIVILEGES IN SCHEMA app
  GRANT ALL ON TABLES TO anon, authenticated, service_role;
GRANT ALL ON ALL SEQUENCES IN SCHEMA app TO anon, authenticated, service_role;
ALTER DEFAULT PRIVILEGES IN SCHEMA app
  GRANT ALL ON SEQUENCES TO anon, authenticated, service_role;
```

**3. Expose the schema via the Supabase API:**
Go to `Project Settings → API → Exposed schemas` and add your custom schema name.

---

### 4. GitHub Workflow Configuration

This project uses the **centralized Wamocon CI/CD workflow** from [`Wamocon/github_workflow`](https://github.com/Wamocon/github_workflow).

#### Overview of the three workflows

| Workflow | File | Trigger | What it does |
|---|---|---|---|
| **PR Pipeline** | `pr-pipeline.yml` | **Automatic** on every PR to `main`/`master` | Auto-Fix (ESLint + Prettier) → Typecheck + Lint |
| **Deploy** | `deploy.yml` | **Manual only** — no auto-trigger | Builds and deploys to Vercel via CLI |
| **LP Generator** | `lp-generator.yml` | **Manual only** — no auto-trigger | Generates a landing page in a new repo |

> ⚠️ **No automatic deployment:** Neither a PR nor a push to `main` triggers a deployment automatically. All deployments are started manually from the Actions tab.

#### What you need to do

1. Verify that `Wamocon/github_workflow` is the correct org/repo reference.
2. Enable workflow write permissions:  
   `Settings → Actions → General → Workflow permissions → Allow GitHub Actions to create and approve pull requests`
3. Add **one single secret** to your repository:
   - Go to `Repository → Settings → Secrets and variables → Actions → New repository secret`
   - Name: `VERCEL_PROJECT_ID`
   - Value: *(see section 5 below)*

> ✅ **All other required secrets** (`VERCEL_TOKEN`, `VERCEL_ORG_ID`) are **already configured at the GitHub Organisation level**.

#### Triggering a manual deployment

```
GitHub repo → Actions → "Deploy to Vercel" → Run workflow
→ Choose environment: production or preview
→ Click "Run workflow"
```

---

### 5. Vercel Deployment Strategy

#### Step 1: Grant Vercel GitHub App access in Org Settings (One-time, Critical)

> ⚠️ **This step must be done BEFORE importing in Vercel.** Without it, your repo will not appear in Vercel's import list — even if it is public.

1. Go to **GitHub → Wamocon Organisation → Settings → Installed GitHub Apps**  
   `https://github.com/organizations/Wamocon/settings/installations`
2. Find the **Vercel** app in the list.
3. Click **Configure**.
4. Scroll to **Repository access**.
5. Select **"Only select repositories"** and add your new repo.
6. Click **Save**.

#### Step 2: Initial Deployment (One-Time)

1. **Make the repo public** temporarily  
   `Repository → Settings → General → Change visibility → Public`
2. Go to [vercel.com](https://vercel.com) → **Add New Project** → **Import** → select your repo.
3. Deploy the project (Vercel detects Next.js automatically).
4. **Copy the Vercel Project ID:**  
   `Vercel Project → Settings → General → Project ID` → copy the value.
5. **Add to GitHub secrets:**  
   `Repository → Settings → Secrets and variables → Actions → New repository secret`  
   Name: `VERCEL_PROJECT_ID` | Value: the ID you copied.
6. **Revert the repo to internal:**  
   `Repository → Settings → General → Change visibility → Internal`

> 💡 **After this one-time setup**, the GitHub Action deploys via Vercel CLI — Vercel no longer sees who committed, and there are no team seat errors with a personal Hobby account.

#### Step 3: Add environment variables in Vercel

> ⚠️ **CRUCIAL:** Go to `Vercel Project → Settings → Environment Variables` and add **all** variables from your `.env.local`. Without these, the build **will fail**.

#### Deployment flow (after setup)

| Trigger | Result |
|---|---|
| PR targeting `main`/`master` | PR Pipeline runs automatically (no deployment) |
| Merge / push to `main`/`master` | No automatic deployment |
| **Manual workflow run** | Deploys to the chosen environment: `production` or `preview` |

**How to deploy manually:**

```
GitHub → Actions → "Deploy to Vercel" → Run workflow
→ environment: production  (for the live URL)
→ environment: preview     (for a temporary test URL)
→ db_schema: (leave empty — Vercel env vars are used)
```

---

### 6. Domain Management

1. **Secure a domain** for your application via [Strato](https://www.strato.de).
2. In the Vercel project settings, go to `Settings → Domains` and add your domain.
3. Configure the DNS records at Strato as shown by Vercel (typically a CNAME or A record).

---

### 7. Project Checklist

- [ ] Landing Page
- [ ] Handbuch / Manual
- [ ] Main Process (core feature)
- [ ] Video (demo / tutorial)
- [ ] Domain (secured via Strato)

---

### 8. Landing Page Generator

The workflow file `.github/workflows/lp-generator.yml` generates a landing page for this app by calling a central, reusable Wamocon workflow.

#### What the workflow does

- Reads the contents of this repository
- Uses a configurable **design template** as a visual base
- Lets GitHub Copilot generate a landing page and create a new repository for it

#### What you can change

| Input | Default | Description |
|---|---|---|
| `custom_template` | `Wamocon/hochzeitsrechner_lp` | The GitHub repo used as the design template |
| `custom_name` | `generated_lp` | Name for the newly created landing page repository |
| `custom_prompt` | *(generic prompt)* | Detailed instructions for Copilot |

> 💡 **Tip:** The more specific your prompt, the better the generated landing page.

#### When you should run this workflow

Run this workflow **only after** your project is mostly complete:
- Handbook / Manual
- README with product description, features, and target audience
- Legal pages / relevant links

> ✅ **Recommendation:** In most cases, you only need to run it **once** at the end of the project.

#### Running manually

`Repository → Actions → "🚀 lp-generator" → Run workflow`

1. Select **"🚀 lp-generator"** from the left workflow list.
2. Click **"Run workflow"** on the right.
3. Adjust the input fields (template, name, prompt) as needed.
4. Confirm with **"Run workflow"**.

#### If the workflow fails (repository name already exists)

1. Change the `custom_name` value and run the workflow again.
2. Or delete the existing target repository (if no longer needed) and run again.

## ./IDEA.md
# Projektidee

> Fuell diese Datei aus, bevor du den Skill `anforderungsdokument` aufrufst.
> Je mehr Details du hier schreibst, desto besser wird das generierte Dokument.
> Anleitung: `.github/skills/anforderungsdokument/SKILL.md`

---

## Projektname

[Name der App, z.B. "Universal Inventory Manager"]

---

## Beschreibung

[Was macht die App? Welches Problem loest sie? Sei konkret.

Beispiel:
"Eine webbasierte Lagerverwaltungs-App fuer kleine und mittelgrosse Unternehmen in
Deutschland. Sie ersetzt Excel-basierte Bestandslisten durch ein strukturiertes System
mit Echtzeit-Uebersicht, QR-Code-Scanfunktion und automatisierten Benachrichtigungen.
Das Ziel ist es, manuelle Fehler bei der Lagerhaltung um mindestens 80 % zu reduzieren
und den Zeitaufwand fuer Inventurprozesse auf ein Minimum zu senken."]

---

## Zielgruppe

[Wer soll die App nutzen? Branche, Unternehmensgroesse, Rolle.

Beispiel:
"Lager- und Logistikleiter sowie Mitarbeiter in KMU mit 10 bis 200 Angestellten,
insbesondere im Einzel-, Gross- und Onlinehandel in Deutschland und dem
deutschsprachigen Europa."]

---

## Kernproblem

[Das konkrete Problem, das OHNE die App besteht.

Beispiel:
"Lagerfehler durch manuelle Erfassung in Excel kosten KMU durchschnittlich
14 % des Jahresumsatzes. Bestehende Enterprise-Loesungen wie SAP EWM sind
fuer kleinere Betriebe zu komplex und zu teuer."]

---

## Gewuenschte Hauptfunktionen (Version 1)

[Liste der wichtigsten Funktionen. Beispiel:]

- Artikel anlegen, bearbeiten, loeschen
- Lagerbestand in Echtzeit einsehen
- QR-Code-Etiketten generieren und scannen
- Rollenbasierter Zugriff (Admin, Manager, Mitarbeiter)
- Mehrsprachige Oberflaeche (Deutsch und Englisch)
- Dashboard mit Bestandsuebersicht

---

## Tech-Stack (optional, wenn bekannt)

[Bekannte oder gewuenschte Technologien. Standardempfehlung falls leer:
Next.js, React, TypeScript, Supabase, Tailwind CSS, Vercel]

---

## Marktsegment und Branche

[In welchem Markt soll die App operieren?

Beispiel: "Lagerverwaltungssoftware (WMS) fuer KMU in Deutschland, Segment Mittelstand"]

---

## Bekannte Wettbewerber (optional)

[Bestehende Loesungen, die aehnliches tun.

Beispiel: SAP EWM, Sage Wawi, Pickware, Odoo Inventory, Lightspeed]

---

## Ersteller

[Vollstaendiger Name]

---

## Empfaenger (Geschaeftsfuehrung)

[Name und Titel des Entscheidungstraegers, z.B. "waleri moretz, CEO WAMOCON GmbH"]

---

## Welle und Version

1

---

## Zusaetzliche Hinweise (optional)

[Besondere Anforderungen, Einschraenkungen, Deadlines oder andere relevante
Informationen, die im Dokument beruecksichtigt werden sollen.]

## ./IMPLEMENTATION_STATUS.md
# Sirin — Implementation Status (V1)

> Stand: nach erstem Build der V1-Module gemäß `Anforderungsdokument_Sirin_v1.0.md`.
> Update V1.2 (April 2026): Öffentliche „Sirenen"-Vorstellungsseiten mit Tabs (Übersicht, Leistungen, Kalender, Bewertungen).
> Update V1.3 (Mai 2026): Dienstleister-Suche mit Karte, Liste, Filtern, Favoriten, Benachrichtigungen, erweiterte Testdaten.

## TL;DR

- ✅ Lokale Supabase-Stack läuft auf Custom-Ports (kollisionsfrei zu anderen lokalen Instanzen).
- ✅ Komplettes Datenmodell, RLS-Policies und zwei RPCs (`compute_available_slots`, `create_public_booking`) inkl. Doppelbuchungsschutz (`slot_unavailable`).
- ✅ Demo-Daten (**5 Organisationen**, **12 Auth-User** davon 10 Staff + 7 Endnutzer, diverse Services, Ressourcen, Working-Hours, Bookings verteilt über Mai 2026, Reviews, Favourites).
- ✅ Next.js 16.2.1 App-Router (i18n DE/EN, Light/Dark, Tailwind v4, next-intl) — `npm run typecheck`, `npm run lint`, `npm run build` alle clean.
- ✅ Smoke-Test End-to-End: 370 freie Slots berechnet, Buchung angelegt, zweite Buchung auf gleichen Slot korrekt blockiert.
- ✅ **Dienstleister-Suche** (`/search`) mit Kartenansicht (Leaflet/OpenStreetMap), Listenansicht, Filtern (Stadt, Kategorie, Bewertung, Preis), Favoriten, gespeicherte Suchen, Angebotsbenachrichtigungen.

---

## 1. Erste Schritte (Local)

```powershell
# Voraussetzungen: Node 20+, Docker Desktop, Supabase CLI (devDep)
npm install
npx supabase start              # startet Postgres, PostgREST, Auth, Studio, Mailpit
npx supabase db reset           # spielt Migrations + Seed ein
Copy-Item .env.example .env.local   # falls noch nicht geschehen
npm run dev
```

Standardports (siehe `supabase/config.toml`, gewählt um nicht mit anderen lokalen Supabase-Projekten zu kollidieren):

| Dienst        | Port  | URL                       |
| ------------- | ----- | ------------------------- |
| API/PostgREST | 55421 | http://127.0.0.1:55421     |
| Postgres      | 55422 | postgresql://postgres:postgres@127.0.0.1:55422/postgres |
| Studio        | 55423 | http://127.0.0.1:55423     |
| Mailpit       | 55424 | http://127.0.0.1:55424     |

## 2. Demo-Logins

Alle Demo-Benutzer haben das Passwort **`sirin1234`** und sind über `supabase/seed.sql` angelegt.

### Organisations-Inhaber / Staff

| E-Mail                    | Organisation        | Rolle    |
| ------------------------- | ------------------- | -------- |
| julia@example.com         | Salon Julia         | manager  |
| marcus@example.com        | Physio Marcus       | manager  |
| demo@sirin.app            | Salon Julia         | provider |
| lena@example.com          | Salon Julia         | provider |
| sophie@yoga-harmonie.de   | Yoga Harmonie       | manager  |
| max@yoga-harmonie.de      | Yoga Harmonie       | provider |
| kevin@barbershop-kings.de | Barbershop Kings    | manager  |
| amelie@kosmetik-bella.de  | Kosmetik Bella      | manager  |
| natalie@kosmetik-bella.de | Kosmetik Bella      | provider |
| felix@physio-marcus.de    | Physio Marcus       | provider |

### Endnutzer (Kunden)

| E-Mail                       | Name           |
| ---------------------------- | -------------- |
| anna.schmidt@example.com     | Anna Schmidt   |
| tom.mueller@example.com      | Tom Müller     |
| hannah.becker@example.com    | Hannah Becker  |
| lukas.hoffmann@example.com   | Lukas Hoffmann |
| mia.wagner@example.com       | Mia Wagner     |
| noah.fischer@example.com     | Noah Fischer   |
| emma.braun@example.com       | Emma Braun     |

### Platform-Admin

| E-Mail        | Rolle      |
| ------------- | ---------- |
| admin@sirin.app | superadmin |

## 3. Wichtige URLs (Dev)

| Zweck                         | URL                                                  |
| ----------------------------- | ---------------------------------------------------- |
| Marketing-Homepage (DE)       | `http://localhost:3000/de`                           |
| **Dienstleister-Suche**       | `http://localhost:3000/de/search`                    |
| Anmeldung                     | `http://localhost:3000/de/auth/sign-in`              |
| Dashboard                     | `http://localhost:3000/de/dashboard`                 |
| Öffentliche Buchung Salon     | `http://localhost:3000/de/b/salon-julia`             |
| Öffentliche Buchung Physio    | `http://localhost:3000/de/b/physio-marcus`           |
| Öffentliche Buchung Yoga      | `http://localhost:3000/de/b/yoga-harmonie`           |
| Öffentliche Buchung Barber    | `http://localhost:3000/de/b/barbershop-kings`        |
| Öffentliche Buchung Kosmetik  | `http://localhost:3000/de/b/kosmetik-bella`          |
| Org-Tab Leistungen            | `http://localhost:3000/de/b/salon-julia/services`    |
| Org-Tab Kalender              | `http://localhost:3000/de/b/salon-julia/calendar`    |
| Org-Tab Bewertungen           | `http://localhost:3000/de/b/salon-julia/reviews`     |
| Buchungs-Wizard (mit Service) | `http://localhost:3000/de/b/salon-julia/book?service=<uuid>` |
| Impressum / Datenschutz / AGB | `http://localhost:3000/de/legal/{impressum\|datenschutz\|agb}` |

## 4. Implementierte V1-Module

| Modul                                         | Status | Hinweis |
| --------------------------------------------- | :----: | ------- |
| **DK** Dienstleistungen & Preise              |   ✅   | CRUD im Dashboard, Resource-Zuweisung, Anzahlung, Sichtbarkeit, Aktiv-Flag |
| **KA** Kalender & Verfügbarkeiten             |   ✅   | Wochenansicht (Mo–So), Resource-Working-Hours, Status-Farbcodierung |
| **KH** Kundenhistorie                         |   ✅   | Liste + Detail mit KPIs, Tags, Buchungshistorie, Kommunikationskanäle |
| **BK** Online-Buchung (Wizard)                |   ✅   | 4 Schritte: Service → Zeit → Daten → Bestätigung; Branding-Header pro Org |
| **Org-Setup / Onboarding**                    |   ✅   | `create_organisation` RPC; Multi-Tenant über `organisation_members` + RLS |
| **Auth (Email/Passwort)**                     |   ✅   | Supabase Auth via `@supabase/ssr` (Cookies) |
| **Settings**                                  |   ✅   | Stammdaten, Brand-Farben, Locale, Timezone, **öffentliches Profil (Slogan, About, Adresse, Webseite, Instagram), Logo-/Hero-Bild-/Hero-Video-Upload mit Vorschau & Entfernen-Schalter** |
| **Manager: Außendarstellung**                 |   ✅   | Sidebar-Eintrag *Medien* → `/dashboard/media`: Mehrfach-Upload (Bilder/Video) in Bucket `org-media`, Bildunterschrift/Alt-Text editieren, Reihenfolge ↑/↓, **Sichtbarkeit ein-/ausblenden (bleibt im Storage, wird aber auf der öffentlichen Seite nicht mehr angezeigt)**, **Bildausschnitt mit klickbarem Fokuspunkt + Zoom-Slider (1×–3×) für Bilder & Videos** (gespeichert als `is_visible`, `focal_x`, `focal_y`, `zoom`; auf `/b/<slug>` als `object-position` + `transform: scale` angewendet), löschen (Storage-Objekt wird mitentfernt). Resources-Form um öffentliches Profil erweitert (Foto-Upload → `provider-avatars`, Headline, Bio, Sichtbarkeit auf Team-Seite). |
| **i18n DE/EN + Light/Dark**                   |   ✅   | next-intl, `localePrefix: as-needed`, persistenter Theme-Toggle |
| **Legal-Seiten + Footer**                     |   ✅   | Markdown-Renderer aus `legal-docs/` (Impressum/Datenschutz/AGB; EN: imprint/privacy/terms) |
| **Branding (Logo + Favicon)**                 |   ✅   | Drei Logo-Varianten (Wordmark, Icon, Figure) |
| **V1.2 — Öffentliche Org-Vorstellung (Tabs)** |   ✅   | `/b/[slug]` Übersicht (Hero-Bild/Video, About, Kontakt, Galerie, Team, Service-Teaser „ab XYZ €"), `/services` (Suche + Kategorienfilter), `/calendar` (7-Tage-Slots pro Service), `/reviews` (Liste + Eingabeformular mit Sterne, Foto-Uploads, Auswahl Dienstleister „Keine" / Leistung „Sonstige") |
| **V1.2 — Org-Medien & Storage**               |   ✅   | Tabelle `organisation_media` (Bild/Video, Position), Buckets `org-media`, `provider-avatars`, `review-photos` mit RLS (public read; manager / Self-write). Server Actions Body-Limit in `next.config.ts` auf **50 MB** angehoben (Default 1 MB), damit Hero-Video & Mehrfach-Upload den Storage-Helper überhaupt erreichen. |
| **V1.2 — Reviews + RPC `submit_review`**      |   ✅   | Atomarer Insert von Bewertung + Foto-URLs, RLS für Autor/Manager/Admin, Aggregat-RPC `org_rating_summary` |
| **V1.3 — Dienstleister-Suche (`/search`)**     |   ✅   | Karten- (Leaflet/OpenStreetMap) und Listenansicht mit Filtern (Freitext, Stadt, Kategorie, Mindest-Bewertung, Max-Preis), Geo-Entfernungsberechnung (Haversine), Ergebnis-Karten mit Popup-Details, responsive Design. |
| **V1.3 — Favoriten**                           |   ✅   | Tabelle `favourites` (user → org), Toggle-Button auf Org-Karten, RLS pro User. |
| **V1.3 — Gespeicherte Suchen**                 |   ✅   | Tabelle `saved_searches` (user → JSON-Filter), Speichern/Laden/Löschen in der Filterleiste, RLS pro User. |
| **V1.3 — Angebotsbenachrichtigungen**           |   ✅   | Tabelle `offer_subscriptions` (user → org), Bell-Toggle auf Org-Karten (vorbereitet für E-Mail-/Push-Delivery), RLS pro User. |
| **V1.3 — Erweiterte Testdaten**                |   ✅   | 5 Organisationen (Berlin, München, Hamburg, Frankfurt, Köln), 10 Staff-Mitglieder, 7 Endnutzer, 20+ Buchungen verteilt über Mai 2026, 13 Bewertungen, Favoriten- und Benachrichtigungs-Seed. |
| **V1.3 — RPC `search_organisations`**          |   ✅   | Serverseitige Such-Funktion mit Text-, Geo-, Kategorie-, Bewertungs- und Preisfiltern, sortiert nach Entfernung/Rating. Public via `anon` + `authenticated`. |

## 5. Hindernisse / Out-of-Scope für V1

| Bereich                              | Status              | Begründung |
| ------------------------------------ | ------------------- | ---------- |
| **ZN-01..06** Stripe-Zahlungen       | DB-Schema vorhanden, keine UI/SDK-Integration | Stripe-Konto + Webhooks gehören in einen separaten, vom Kunden freigegebenen Schritt. Felder `payment_status`, `deposit_cents` sind im Buchungsmodell bereits enthalten. |
| **NB-01..03** Reminder-Dispatcher    | DB-Queue (`notifications` Tabelle) existiert, kein Worker | Cron / pg_cron / Edge Function für Mail-Versand fehlt. Mail-Provider muss ausgewählt werden (z. B. Resend). |
| **KS-01..03** Kalender-Sync (Google/Outlook) | nicht implementiert | Erfordert OAuth-Apps und Token-Refresh-Infrastruktur. |
| **KO-02/03** SMS / WhatsApp / Voice  | nur Channel-Flags am Customer | Erfordert Twilio/Meta-Integrationen. |
| **AI-Vorschläge (Feature im Anforderungsdokument)** | nicht implementiert | Out of scope für V1 — bewusst weggelassen. |
| **Custom Domain pro Organisation**   | DB-Feld `custom_domain` vorhanden, kein Routing | Erfordert Wildcard-DNS + Vercel-Domain-API. |
| **Auth-Cookie-Refresh in `proxy.ts`** | nur next-intl-Routing | Bei sehr langen Sessions kann der Access-Token ablaufen; aktuell wird das pro Request-Server-Component erneut geholt. Für saubere Lösung Supabase `updateSession` in `proxy.ts` einbauen. |

## 6. Verifizierte Funktionen (Tests)

```powershell
# 1) Slots berechnen (anonym)
$body = @{ p_service_id="aaaaaaaa-4000-0000-0000-000000000001"; p_from=(Get-Date).ToUniversalTime().ToString("o"); p_to=(Get-Date).AddDays(7).ToUniversalTime().ToString("o"); p_step_minutes=15 } | ConvertTo-Json
# → 370 Slots in den nächsten 7 Tagen

# 2) Buchung erstellen
# → "a0aa60ee-8e6c-462b-bc1e-1f40aa0a15d3"

# 3) Selbe Buchung erneut → blockiert
# → {"code":"P0001","message":"slot_unavailable"}
```

Build-Pipeline:

```text
npm run typecheck   ✓ (keine Fehler)
npm run lint        ✓ (keine Fehler)
npm run build       ✓ (53/53 statische Seiten generiert, inkl. /[locale]/search)
```

## 7. Nächste Schritte (priorisiert)

1. **Reminder-Worker** — Edge Function (Supabase) liest `notifications` mit `status='queued'`, sendet via Resend, setzt `status='sent'`. 24 h-/2 h-Reminder über `pg_cron` einplanen.
2. **Stripe Checkout** — `price_cents` / `deposit_cents` zu Stripe-PaymentIntent. Webhook → `payments` Tabelle und Status auf Booking propagieren.
3. **Settings: Öffnungszeiten Editor** — UI für `location_opening_hours` und `location_closures`.
4. **Cookie-Refresh in `proxy.ts`** — Supabase Auth-Helper integrieren.
5. **Hosted Supabase Migration** — `npx supabase link` + `db push`, dann ENV von local → hosted.
6. **Offer Notification Delivery** — E-Mail-/Push-Versand wenn Org neue Angebote/Specials veröffentlicht (Tabelle `offer_subscriptions` ist bereit).
7. **Geocoding-Integration** — Automatisches Geocoding von Adressen zu Koordinaten (z. B. Nominatim API) beim Anlegen/Ändern von Standorten.

## 8. Architektur in Kurzform

- **Multi-Tenant**: alles tenant-scoped per `organisation_id` + Helpers `is_org_member()` / `is_org_owner()` als `SECURITY DEFINER`. Dadurch sind RLS-Policies einfach (`using (is_org_member(organisation_id))`).
- **Public Read** für Buchungsseite über zusätzliche Policies (`org_public_read`, `svc_public_read`, `res_public_read`, `loc_public_read`).
- **`create_public_booking`** ist `SECURITY DEFINER` — re-validiert Service-Sichtbarkeit, prüft Working-Hours und schließt Konflikte mit `for update` aus, bevor das Insert läuft.
- **Themes** über CSS Custom Properties + `@custom-variant dark` in Tailwind v4.
- **i18n** über next-intl mit `setRequestLocale` in jeder Server-Page.

## ./Implementierungsdokument_Sirin_v1.1_RBAC.md
# Implementierungsdokument Sirin V1.1 — Rollen- & Rechtekonzept
## Erweiterung zum Anforderungsdokument v1.0 (Welle 8)

| | |
|---|---|
| **Projekt** | Sirin — Rollen- & Rechtekonzept |
| **Bezugsdokument** | `Anforderungsdokument_Sirin_v1.0.md` |
| **App Version** | 1.1 (RBAC-Erweiterung) |
| **Status** | Implementiert, lokal verifizierbar |
| **Datum** | 29. April 2026 |

---

## 1. Überblick

Diese Erweiterung führt ein **fünfstufiges Rollen- und Rechtemodell** in Sirin ein:

| # | Rolle | Anforderung 1.x | Implementiert als |
|---|---|---|---|
| 1 | **Superadmin** | 1.1 | Tabelle `platform_admins` + UI `/admin/*` + RPC-Familie `admin_*` |
| 2 | **Unternehmensmanager** | 1.2 | `organisation_members.role = 'manager'`, **Partial-Unique-Index** garantiert genau 1 pro Org |
| 3 | **Dienstleister im Unternehmen** | 1.3 | `organisation_members.role = 'provider'` + 1:1 mit `resources.user_id` |
| 4 | **Endnutzer mit Konto** | 1.4 | `auth.users` + `customer_accounts` + verknüpfte `customers.auth_user_id` |
| 5 | **Endnutzer ohne Konto** | 1.5 | Nur Lese-RLS + Booking-Gate auf RPC-Ebene (`account_required`) |

Sicherheitsdoktrin: alle Rechteprüfungen **doppelt verankert** — sowohl in den Server Actions (TypeScript) als auch in PostgreSQL via RLS / SECURITY DEFINER RPCs.

---

## 2. Datenbank-Konzept

### 2.1 Neue Migrationen

| Datei | Zweck |
|---|---|
| `supabase/migrations/20260429120000_org_role_enum.sql` | erweitert `org_role` um `manager`, `provider` (separate Migration nötig wegen Postgres-Enum-Commit-Regel) |
| `supabase/migrations/20260429120100_roles_and_accounts.sql` | Tabellen, RLS-Policies, Helper-Funktionen, RPCs |

### 2.2 Neue Tabellen

| Tabelle | PK | Zweck |
|---|---|---|
| `platform_admins` | `user_id` → `auth.users` | Superadmin-Whitelist |
| `customer_accounts` | `user_id` → `auth.users` | Globales Endnutzer-Profil + Präferenzen + Notification-Settings |

### 2.3 Schema-Erweiterungen

| Tabelle | Spalte | Zweck |
|---|---|---|
| `customers` | `auth_user_id uuid` | Verknüpfung Org-Customer ↔ globales Endnutzer-Konto |
| `organisation_members` | partial unique index `where role='manager'` | erzwingt **maximal einen** Manager pro Org |

### 2.4 Helper-Funktionen (`security definer`)

| Funktion | Rückgabe | Bedeutung |
|---|---|---|
| `is_platform_admin()` | `bool` | Superadmin? |
| `is_org_manager(org)` | `bool` | Manager dieser Org? |
| `is_org_provider(org)` | `bool` | Provider dieser Org? |
| `is_org_member(org)` | `bool` | beliebiges Mitglied (existierte bereits) |
| `is_org_owner(org)` | `bool` | **Backward-Compat:** delegiert jetzt an `is_org_manager` |
| `is_resource_owner(rid)` | `bool` | Provider, dessen `auth.uid()` = `resources.user_id`? |

### 2.5 RLS-Matrix (Auszug)

| Tabelle | Lesen | Schreiben |
|---|---|---|
| `services`, `service_categories`, `service_resources`, `resources` | alle Org-Mitglieder | **nur Manager** + Superadmin |
| `resource_working_hours`, `resource_time_blocks` | alle Org-Mitglieder | Manager **oder** `is_resource_owner` |
| `customers` | Org-Mitglieder + `auth_user_id = auth.uid()` | Org-Mitglieder + eigene Datenpflege durch Endnutzer |
| `bookings` | Org-Mitglieder + Endnutzer (eigene Buchungen via Customer-Join) | Org-Mitglieder + Superadmin; Endnutzer **nur via RPC** |
| `customer_accounts` | nur eigener User | nur eigener User + Superadmin |
| `organisations`, `…/admin overrides` | `is_org_member` ODER `is_platform_admin` | Manager + Superadmin |

### 2.6 RPCs (security definer)

| RPC | Rolle | Zweck |
|---|---|---|
| `create_public_booking(...)` | **authenticated** (anon revoked) | Buchung mit Slot-Reprüfung + Kundenverknüpfung |
| `customer_cancel_booking(id, reason)` | Endnutzer | Eigene Buchung stornieren |
| `customer_reschedule_booking(id, new_starts_at)` | Endnutzer | Eigene Buchung verschieben (Slot-Reprüfung) |
| `provider_update_own_resource(id, color, description)` | Provider | Limitierte Selbstpflege |
| `provider_list_bookings(from, to)` | Provider | Eigene Buchungen für Provider-Kalender |
| `manager_invite_provider(org, user, resource_id?)` | Manager | Mitglied einladen + an Resource binden |
| `admin_list_organisations()` | Superadmin | Cross-Tenant-Liste |
| `admin_list_org_members(org)` | Superadmin | Mitglieder einer Org |
| `admin_list_customer_accounts()` | Superadmin | Alle Endnutzer-Konten |
| `admin_update_organisation(...)` | Superadmin | Stammdaten ändern |
| `admin_set_member_role(org, user, role)` | Superadmin | Rolle ändern, automatische Demote des bisherigen Managers |
| `admin_remove_member(org, user)` | Superadmin | Membership löschen |

---

## 3. Anwendungs-Layer

### 3.1 Neuer Auth-Kontext

| Datei | Zweck |
|---|---|
| `src/lib/auth-context.ts` | `getAuthContext()` liefert `{ user, role, org, orgRole, providerResourceId }`. Berechnete `AppRole` ∈ `superadmin` \| `manager` \| `provider` \| `customer` \| `guest`. |

Alle Server Actions und Layouts nutzen ausschließlich diesen Kontext (ersetzt das bisherige `getCurrentOrg()` für rollenrelevante Entscheidungen — `getCurrentOrg()` bleibt für Legacy-Aufrufe bestehen).

### 3.2 Routenkarte

| Pfad | Rolle | Quelle |
|---|---|---|
| `/[locale]/redirect` | beliebig | rollenbasierter Eingang nach Login |
| `/[locale]/admin` | Superadmin | Layout + Übersicht (KPIs) |
| `/[locale]/admin/organisations` | Superadmin | Liste aller Unternehmen |
| `/[locale]/admin/organisations/[id]` | Superadmin | Stammdaten + Mitglieder bearbeiten / Rollen vergeben / entfernen |
| `/[locale]/admin/customers` | Superadmin | Liste aller Endnutzer-Konten |
| `/[locale]/dashboard` | Manager / Provider | bestehendes Dashboard, Sidebar dynamisch nach Rolle |
| `/[locale]/dashboard/services`, `/resources`, `/customers`, `/media`, `/settings` | **nur Manager** | Sidebar blendet Items für Provider aus + Server Actions prüfen Rolle |
| `/[locale]/dashboard/availability` | **nur Provider** | Eigene Arbeitszeiten + Sperrzeiten |
| `/[locale]/account` | Endnutzer (Konto) | Übersicht (nächste Termine, Anbieter) |
| `/[locale]/account/bookings` | Endnutzer | Stornieren + Verschieben (RPC) |
| `/[locale]/account/history` | Endnutzer | Vergangene Buchungen |
| `/[locale]/account/profile` | Endnutzer | Profil pflegen (`customer_accounts`) |
| `/[locale]/account/preferences` | Endnutzer | Benachrichtigungs- + Kategorien-Präferenzen |
| `/[locale]/b/[slug]` | alle (inkl. Gast) | Lesen + Slot-Wahl; Schritt 4 (Bestätigen) gated für Gäste |

### 3.3 Sicherheitsverankerung pro Schicht

| Aktion | UI-Gate | Server-Action-Gate | DB-Gate |
|---|---|---|---|
| Service anlegen/ändern/löschen | Sidebar-Item nur für Manager | `getAuthContext().role === 'manager'` | RLS `svc_write_manager` |
| Eigene Arbeitszeiten ändern | Sidebar-Item nur für Provider | `role === 'provider'` + eigene `resourceId` | RLS `is_resource_owner` |
| Buchung anlegen | Wizard zeigt Login-Wall | `create_public_booking` raised `account_required` wenn `auth.uid() is null` | Anon revoked auf RPC |
| Buchung stornieren | Button nur in `/account/bookings` | RPC-Aufruf | RPC prüft `customers.auth_user_id = auth.uid()` |
| Org-Stammdaten editieren | nur in `/admin` UI | Server Action mit Superadmin-Check | RPC `admin_update_organisation` mit `is_platform_admin` |

---

## 4. Test-Daten (Seed)

`supabase/seed.sql` legt **sieben Auth-User** an (Passwort jeweils `sirin1234`):

| E-Mail | Rolle (App) | Org | Bemerkung |
|---|---|---|---|
| `admin@sirin.app` | Superadmin | — | Eintrag in `platform_admins` |
| `julia@example.com` | Manager | Salon Julia | + Resource „Julia" |
| `marcus@example.com` | Manager | Physio Marcus | + Resource „Marcus" |
| `demo@sirin.app` | Provider | Salon Julia | nicht-resource-gebunden (zeigt Provider-Sicht ohne Self-Service) |
| `lena@example.com` | Provider | Salon Julia | gebunden an Resource „Lena" → kann eigene Verfügbarkeit pflegen |
| `anna.schmidt@example.com` | Endnutzer (Konto) | — | Buchungshistorie bei Salon Julia |
| `tom.mueller@example.com` | Endnutzer (Konto) | — | Buchungen bei **Salon Julia + Physio Marcus** (Cross-Tenant-Demo) |

Ausrollen:

```powershell
npx supabase db reset
```

---

## 5. Abgleich mit dem Anforderungsdokument

| Anforderung (Kapitel 1.x) | Status | Hinweis |
|---|---|---|
| **1.1 Superadmin** — eigene Ansichten + Bearbeitung von Unternehmen, Usern, Endnutzern | ✅ erfüllt | `/admin/*` (3 Seiten + Detailansicht) |
| **1.2 Unternehmensmanager** — genau 1 pro Org, vollständige Konfiguration inkl. Außendarstellung | ✅ erfüllt | DB-Constraint + Module **Services / Resources / Customers / Media (Galerie) / Settings (Stammdaten + öffentliches Profil + Branding inkl. Logo, Hero-Bild, Hero-Video)**. Resources-Form pflegt Avatar, Headline, Bio, Sichtbarkeit auf der Team-Seite. Storage über Buckets `org-media` & `provider-avatars` mit RLS `is_org_manager(<org_id>)`. |
| **1.3 Dienstleister im Unternehmen** — Leistungen vom Manager festgelegt, Verfügbarkeiten vom Dienstleister selbst pflegbar | ✅ erfüllt | RLS-Trennung Manager/Provider, `/dashboard/availability` |
| **1.4 Endnutzer mit Konto** — eigener Kalender, Benachrichtigungseinstellungen, Profil, Präferenzen, Termine verwalten (Stornierung + Verschiebung), Buchungshistorie | ✅ erfüllt | `/account/*` (5 Seiten), 2 RPCs für Cancel/Reschedule |
| **1.5 Endnutzer ohne Konto** — Browsen + Kalender betrachten möglich, Buchung blockiert mit Hinweis auf Konto-Erstellung | ✅ erfüllt | RPC raised `account_required`, Wizard zeigt Sign-Up/Sign-In-Wall mit `?next=/b/<slug>` |
| **Testdaten via Seed** | ✅ erfüllt | 7 Auth-User, 2 Orgs, Cross-Tenant-Buchung |

### 5.1 Bewusste Weiterentwicklungen über die Anforderung hinaus

| # | Erweiterung | Begründung |
|---|---|---|
| W1 | `customer_accounts` als globales Profil | Endnutzer kann sich an mehrere Org-Customer-Datensätze anhängen → Cross-Tenant-Verlauf ohne doppelte Pflege |
| W2 | RPC `customer_reschedule_booking` mit Slot-Reprüfung | Stornierung allein reicht nicht; Verschiebung muss atomar gegen Doppelbuchungen abgesichert sein |
| W3 | Partial-Unique-Index (`one_manager_per_org`) | DB-seitige Garantie statt Anwendungs-Convention — verhindert Race Conditions bei gleichzeitigen Beförderungen |
| W4 | `manager_invite_provider` RPC mit optionaler Resource-Bindung | Macht den Sonderfall "Provider hat eigene Resource" explizit und atomar |
| W5 | Sign-Up-Intent (`customer` vs. `business`) | Eine Sign-Up-Seite, zwei Zielzustände (`/account` vs. `/onboarding`) — vereinfacht Marketing-Funnel |
| W6 | Backward-kompatibles `is_org_owner()` | Bestehende RLS-Policies aus V1.0-Migration funktionieren ohne Änderung weiter (delegieren jetzt an `is_org_manager`) |
| W7 | Provider-Liste-Bookings als RPC | Vorbereitet für künftige Provider-Kalender-Ansicht (Anforderung impliziert, V1 zeigt sie noch im Manager-Layout) |

### 5.2 Bewusste Abweichungen

| # | Abweichung | Begründung |
|---|---|---|
| A1 | `auth_user_id` auf `customers` ist **nullable** | Manager dürfen weiterhin Kunden händisch ohne Sirin-Konto anlegen (Walk-In-Kunden, telefonisch erfasst). Erst bei aktiver Buchung durch Endnutzer wird der Link gesetzt. |
| A2 | Provider-Rolle erbt KEINEN Schreibzugriff auf `services` | Anforderung 1.3 beschreibt explizit „Leistungen werden vom Unternehmensmanager festgelegt" → strikte Trennung. |
| A3 | Anonyme Endnutzer behalten **Lesezugriff** auf öffentliche Services / Slots | Anforderung 1.5 verlangt Browsen + Kalenderansicht. Erst der Buchungs-Commit ist gated. |
| A4 | Superadmin nutzt **keine** Service-Role-Keys | Cross-Tenant-Operationen laufen ausschließlich via SECURITY DEFINER RPCs mit `is_platform_admin()`-Check — kein `SUPABASE_SERVICE_ROLE_KEY` im Browser, keine Bypass-Kanäle. |
| A5 | Bestehender V1.0-Login `demo@sirin.app` bleibt als Provider-ohne-Resource | Demonstriert das Verhalten, wenn ein neu eingeladener Provider noch keinem `resources`-Eintrag zugeordnet ist (zeigt Hinweis statt Crash). |

### 5.3 Out-of-Scope (für V1.1, vorbereitet)

| Bereich | Status |
|---|---|
| Reminder-Versand für Endnutzer-Konten | Notification-Tabelle nutzt bereits `customer_id` mit `auth_user_id` als Fallback-Adresse — Worker nicht implementiert (war schon Out-of-Scope V1.0). |
| Manager-UI zum **Einladen** eines Providers per E-Mail | RPC vorhanden (`manager_invite_provider`), UI-Form nicht. Aktuell muss der Endnutzer sich selbst registrieren und der Superadmin ihn zuweisen. |
| Provider-eigener Kalender unter `/dashboard/calendar` | RPC `provider_list_bookings` existiert; UI nutzt aktuell die Manager-Variante (zeigt alle Org-Buchungen, von RLS gestattet). Filter pro `provider` als V2-Item. |
| Mehrfach-Org-Switcher für Manager mit mehreren Orgs | Auth-Kontext priorisiert die höchste Rolle der ersten Membership. |

---

## 6. Verifikation

```powershell
npm run typecheck   # ✅ keine Fehler
npm run lint        # ✅ keine Fehler
npm run build       # ✅ 49 Routen statisch/dynamisch generiert
```

Statisch verifizierte neue Routen (`next build`):

```
/[locale]/admin
/[locale]/admin/customers
/[locale]/admin/organisations
/[locale]/admin/organisations/[id]
/[locale]/account
/[locale]/account/bookings
/[locale]/account/history
/[locale]/account/preferences
/[locale]/account/profile
/[locale]/dashboard/availability
/[locale]/redirect
```

Manueller Smoke-Test-Pfad:

1. `npx supabase db reset` → Seed läuft sauber durch (7 User, 2 Orgs, 4 Buchungen).
2. Login mit `admin@sirin.app` → Redirect nach `/admin`. Sidebar zeigt: Übersicht / Unternehmen / Endnutzer-Konten. Org-Detail erlaubt Rollenwechsel + Mitglied entfernen.
3. Login mit `julia@example.com` → `/dashboard` mit voller Manager-Sidebar inkl. Services/Resources/Customers/Settings.
4. Login mit `lena@example.com` → `/dashboard` mit reduzierter Sidebar (Dashboard, Kalender, **Meine Verfügbarkeit**); kein Zugriff auf Services-Menü.
5. Login mit `anna.schmidt@example.com` → `/account`. Buchungshistorie bei Salon Julia sichtbar; bevorstehender Termin lässt sich stornieren.
6. **Anonym** auf `/de/b/salon-julia` → Service + Slot wählbar; Schritt 3 zeigt „Konto erforderlich" mit Sign-Up- und Sign-In-Buttons (jeweils mit `?next=/b/salon-julia`).
7. Direkter RPC-Aufruf `create_public_booking` ohne Auth → `account_required`-Fehler.
8. Direkter RPC-Aufruf `admin_list_organisations` als Manager → `forbidden`-Fehler.

---

## 7. Bekannte Risiken / Folge-Tickets

| # | Risiko / TODO | Empfehlung |
|---|---|---|
| R1 | Bei `db reset` werden Migrationen pro Datei in einer Transaktion ausgeführt. Die getrennte `…_org_role_enum.sql`-Migration ist daher zwingend — **nicht zusammenführen**. | Im Migrations-Verzeichnis als Konvention dokumentiert. |
| R2 | Sign-Up bestätigt E-Mails nicht (lokal). Für Produktion: Supabase Email-Confirm-Flow + Edge-Function-basiertes Auto-Linking neu eingehender Customer-Records auf `auth.uid()` aktivieren. | Folgeticket „Email-Confirm + Linking-Trigger". |
| R3 | Provider-Beförderung zum Manager im Admin-UI demoted den bestehenden Manager auf `staff`. Sichtbar in einem zweiten Tab eingeloggter Manager erst nach Reload. | Akzeptabel — Realtime-Updates sind V2. |
| R4 | `customer_accounts.preferred_orgs` ist im Schema enthalten, hat aber noch keine UI. | Folgeticket „Lieblings-Anbieter merken". |
| R5 | Cookie-Refresh in `proxy.ts` weiterhin auf next-intl beschränkt (Issue aus V1.0). | Unverändert offen. |

---

**Ende des Dokuments.**

## ./MARKETING_KONZEPT.md
# Sirin — Marketingkonzept & Landingpage-Briefing
## Version 1.0 · Mai 2026 · WAMOCON GmbH

> **Zweck dieses Dokuments:** Vollständige Informationsquelle für den Landingpagegenerator. Enthält Corporate Identity, Zielgruppen, Botschaften, Psychologie, Copy-Vorlagen, Seitenstruktur und Conversion-Mechanismen.

---

## I. MARKE & CORPORATE IDENTITY

### 1.1 Markenidentität im Kern

| Dimension | Definition |
|---|---|
| **Markenname** | Sirin |
| **Herkunft** | Griechische Sirene — Anziehung, Klang, Ruf, Wasser, Transformation |
| **Markenversprechen (primär)** | „Sirin ruft — und du willst kommen." |
| **Markenversprechen (alternativ)** | „Hör auf deine Zeit." (Hauptclaim, doppeldeutig: zuhören + sich Zeit nehmen) |
| **Positionierung** | Warm, magisch, einladend — EU-nativ. Zwischen Präzisions-SaaS und Lifestyle-Marke |
| **Archetyp** | **Der Magier** (Transformation, Anziehung) kombiniert mit **dem Liebhaber** (Sinnlichkeit, Schönheit, Beziehung) |
| **Was Sirin NICHT ist** | Tool. App. Software. Formular. |
| **Was Sirin IST** | Begleiterin. Stimme deines Salons. Einladung. |

### 1.2 Farbsystem

| Token | Farbe | Hex | Psychologische Bedeutung |
|---|---|---|---|
| **Primary Dark** | Marine-Nacht | `#0E3A5F` | Tiefe, Vertrauen, Seriosität, Wasser |
| **Primary** | Aqua-Teal | `#1F7A8C` | Frische, Transformation, Digital-Professionalität |
| **Accent** | Honig-Gold | `#E6B566` | Wärme, Schönheit, Hochwertigkeit, „magisches Leuchten" |
| **Background Light** | Sand | `#F5EFE6` | Ruhe, Reinheit, Premium-Atmosphäre |
| **Text Secondary** | Schiefer | `#5A6B7B` | Lesbarkeit, Sachlichkeit, Vertrauen |
| **White** | Reinweiß | `#FFFFFF` | Klarheit, Raum, Leichtigkeit |

**Gradient-Regel:** Primär-Gradient läuft von `#0E3A5F` über `#1F7A8C` zu `#E6B566` — immer diagonal (top-left → bottom-right). Symbolisiert den Weg von Tiefe (Arbeitsalltag) zur goldenen Leichtigkeit (Ergebnis).

**Verwendungsregel:** Gold (`#E6B566`) immer sparsam. Nur für CTAs, Highlights, Stars, Icons. Nie als Flächenfarbe. Wirkung: kostbar, nicht ordinär.

### 1.3 Typografiesystem

| Rolle | Familie | Gewicht | Einsatz |
|---|---|---|---|
| **Display / Hero** | Playfair Display · Cormorant Garamond | 400–600 | Große Headlines, Subline, Quote-Elemente |
| **UI / Body** | Inter · Manrope | 400–500 | Fließtext, Labels, Navigation, Buttons |
| **Akzent** | Playfair Display Italic | 400 | Pull-Quotes, Claim-Hervorhebungen |

**Typografie-Prinzip:** Serifenüberschriften geben emotionale Wärme und Persönlichkeit. Die Sans-Serif im Body signalisiert digitale Klarheit. Kombination = „Das beste Kosmetikstudio hat auch eine professionelle Buchhaltung."

### 1.4 Bildsprache

**Erlaubt:**
- Nahaufnahmen von Händen bei der Arbeit (Schere, Skalpell, Pinsel, Massage)
- Warmes Licht auf Haut, Holz, Wasser
- Leere Stühle kurz vor dem ersten Kunden des Tages
- Handy auf einem Behandlungstisch mit Buchungsbestätigung
- Wasseroberflächen, Wellen, Reflexionen
- Minimalistische Studioumgebungen in Warm-Tönen

**Verboten:**
- Generische Stockfoto-Lächelmodels vor weißem Hintergrund
- Cartoon-Illustrationen / Clipart
- Kühle, sterile Büro-Ästhetik
- Bildschirmfüllende App-Screenshots ohne Kontext

**Bildkomposition:** 60/40-Regel — 60 % Atmosphäre (Stimmung, Farbe, Licht), 40 % Inhalt (Produkt, Prozess, Ergebnis).

### 1.5 Logo-System

**Drei offizielle Varianten:**

| Variante | Einsatz |
|---|---|
| **Wortmarke mit Klangwellen + Tropfen-i** | Website-Header, Pitch Deck, Briefkopf, Buchungsseiten-Footer |
| **App-Icon „S-Welle"** | Favicon, Social-Media-Avatar, App-Bookmark, WhatsApp-Business-Profil |
| **Bildmarke „Sirenen-Klangkreise"** | Hero-Landingpage, Print, Messe — emotional, sparsam einsetzen |

**Schutzraum:** Immer mindestens 1× Logohöhe Freiraum um das Logo. Nie auf gemusterten Hintergründen ohne Kontrastfläche.

### 1.6 Tone of Voice

| Dimension | Ausprägung | Gegenbeispiel (verboten) |
|---|---|---|
| **Grundstimmung** | Warm, einladend, leicht poetisch | Kalt, technisch, generisch |
| **Aktivität** | Verben statt Substantive | „Online-Terminverwaltung" → „Buche deinen Moment" |
| **Direktheit** | Klar, keine Füllwörter | „Mit Sirin ist es möglich, Termine zu…" |
| **Ansprache Endkunden** | Du (persönlich, nahbar) | Sie (distanziert) |
| **Ansprache Geschäftskunden** | Wählbar — Standard Sie, für jüngere Zielgruppe Du | Keine Konsistenz |
| **Zahlen** | Immer konkret belegt | „viele Kunden" → „76 % der DACH-Endkunden" |
| **No-Show** | „Verlorener Umsatz" nicht „schlechtes Verhalten des Kunden" | Schuldvorwürfe |

**Verbotene Wörter im Marketing-Copy:** *revolutionär, disruptiv, game-changing, einzigartig, erstklassig, Tool, Software, App, Formular, Kalender-Slot.*

**Bevorzugte Wörter:** *Termin, Moment, Behandlung, deine Kunden, deine Zeit, deine Marke, Begleitung, Erinnerung, Einladung, Erlebnis, Auslastung, Freiheit.*

---

## II. ZIELGRUPPEN & BUYER PERSONAS

### 2.1 Primäre Zielgruppe im Überblick

**Wer:** Terminbasierte Dienstleister im DACH-Raum mit 1–15 Mitarbeitenden.
**530.000 Betriebe** adressierbar. Fokus V1 auf zwei Vertikalen: **Friseure & Beauty** (121.000 Betriebe) und **Physio & Heilberufe** (67.000 Praxen).

### 2.2 Persona A — „Die Solo-Friseurin" (Primär-Conversion-Persona)

| Feld | Wert |
|---|---|
| **Name (fiktiv)** | Julia, 32 |
| **Betrieb** | Eigenes Studio, 1 Mitarbeiterin, 40–60 Termine/Woche |
| **Aktuelles System** | Instagram-DMs + Telefon + Google-Kalender |
| **Schmerz #1** | Telefon klingelt während Behandlung, Termine gehen verloren |
| **Schmerz #2** | Kein professioneller Auftritt, Buchungslink funktioniert nicht auf dem Handy |
| **Schmerz #3** | 2–3 No-Shows pro Woche = 150–300 EUR Umsatzverlust |
| **Traum** | Buchungsseite wie ein 5-Sterne-Salon — eigene Domain, eigenes Logo, eigene Farben |
| **Kaufmotiv** | Mehr Professionalität + weniger Unterbrechungen + No-Show-Schutz |
| **Kaufhemmung** | „Zu teuer für mich als Solo" / „Zu kompliziert einzurichten" / „Brauche ich wirklich?" |
| **Entscheidungsweg** | Instagram-Empfehlung → Landingpage → Kostenlose Demo → Kauf Starter |
| **Bereit zu zahlen** | 29–49 EUR/Monat, wenn ROI klar |
| **Reaktion auf** | Vorher-Nachher. Konkrete Zahlen. Ähnliche Person als Testimonial. |

**Marketing-Botschaft für Julia:**
> „Nimm nie wieder einen Anruf während der Behandlung an. Deine Kunden buchen selbst — und kommen zuverlässiger."

### 2.3 Persona B — „Der Praxis-Inhaber" (Physio / Heilberuf)

| Feld | Wert |
|---|---|
| **Name (fiktiv)** | Marcus, 45 |
| **Betrieb** | Physio-Praxis, 3–5 Therapeuten, 120–200 Termine/Woche |
| **Aktuelles System** | Shore+ oder TerminApp, zunehmend unzufrieden |
| **Schmerz #1** | DSGVO-Unsicherheit mit US-Tools bei Patientendaten |
| **Schmerz #2** | Rezept-/Gerätezuordnung funktioniert im Kalender nicht sauber |
| **Schmerz #3** | Kosten bei Treatwell fressen 18–22 % der Einnahmen aus Neukunden |
| **Traum** | Eigene, professionelle Plattform. Kein Marktplatz. Kein Abhängigkeitsrisiko. |
| **Kaufmotiv** | DSGVO-Sicherheit + Kostenkontrolle + eigene Kundendaten |
| **Kaufhemmung** | Migration ist aufwändig. Kein Tech-Experte. Personal muss umschulen. |
| **Entscheidungsweg** | Google-Suche → Vergleich → Demo-Call → Kauf Pro/Business |
| **Bereit zu zahlen** | 69–149 EUR/Monat, wenn Vergleich mit Provisionen positiv |
| **Reaktion auf** | DSGVO-Argumente. Kostenkalkulator. Fachsprachliche Kompetenz. |

**Marketing-Botschaft für Marcus:**
> „Patientendaten in Frankfurt, nicht in San Francisco. Sirin ist Art-9-konform und kostet keine Provision."

### 2.4 Persona C — „Der Mittelgroße Salon" (Upgrade-Persona)

| Feld | Wert |
|---|---|
| **Name (fiktiv)** | Salon Nadia, 38, Inhaberin, 5 Stylistinnen |
| **Schmerz** | Ressourcen-Kollisionen (Waschbecken, Farbmischplatz), Personal-Schichten |
| **Kaufmotiv** | Übersicht über alle Mitarbeiter-Kalender + Ressourcen-Bindung |
| **Wechselbereitschaft** | Hoch, wenn Onboarding einfach und Migration reibungslos |

### 2.5 Jobs-to-be-Done (JTBD-Framework)

| Job (funktional) | Job (emotional) | Job (sozial) |
|---|---|---|
| Lass meine Kunden 24/7 buchen | Nimm mir die Unterbrechungen weg | Zeig mir als professionelle Dienstleisterin |
| Schütz mich vor No-Shows | Gib mir meine Ruhe zurück | Lass meine Buchungsseite wie ein richtiges Business aussehen |
| Halte meine Kundendaten sicher | Mach mir keine Sorgen wegen Datenschutz | Zeig meinen Kunden, dass mir ihre Daten wichtig sind |
| Füll leere Slots nach Absagen | Lass mich keine Einnahmen verlieren | Beweise meinem Team, dass ich das Studio professionell führe |

---

## III. POSITIONIERUNG & KERNBOTSCHAFTEN

### 3.1 Positionierungsstatement

> **Für** terminbasierte Dienstleister im DACH-Raum mit 1–15 Mitarbeitenden,
> **die** ihre Kunden professionell und ohne Provisionen direkt bedienen wollen,
> **ist** Sirin die einladende Buchungsplattform,
> **die** Dienstleistungen (nicht Zeitslots) kennt, DSGVO-native in der EU hostet und die eigene Marke des Anbieters in den Vordergrund stellt —
> **im Gegensatz zu** Calendly (fehlende Dienstleistungslogik), Treatwell (Provisions-Abhängigkeit) und Shore+ (komplexes Onboarding, veraltetes UX).

### 3.2 Unique Selling Propositions (USPs) — Priorisiert

| Rang | USP | Beweis |
|---|---|---|
| 1 | **Dienstleistungen, keine Slots** | Dauer, Personal, Raum, Gerät, Puffer, Anzahlung — alles im Buchungsflow |
| 2 | **Eigene Marke, eigene Domain** | Buchungsseite unter termin.meinsalon.de — nicht calendly.com/irgendwas |
| 3 | **Kein Provisions-Modell** | Flat Fee ab 29 EUR — keine 15–25 % auf jede Buchung |
| 4 | **EU-Hosting, DSGVO-nativ** | Supabase Frankfurt, Art. 9-konform, kein US-Datentransfer |
| 5 | **Intelligente Lückenfüllung** | Absage → automatische Wartelisten-Benachrichtigung mit Alternativvorschlägen |
| 6 | **No-Show-Schutz** | Automatische Reminder 48h/24h/2h + optionale Anzahlung via Stripe |

### 3.3 Positioning Layers (für verschiedene Touchpoints)

**Layer 1 — Headline-Ebene (1 Sekunde Aufmerksamkeit):**
> „Termine, die rufen."

**Layer 2 — Subline-Ebene (5 Sekunden Lesedauer):**
> „Die Buchungsplattform für Friseure, Physios, Beauty und Heilberufe — mit echten Dienstleistungen, eigener Domain und DSGVO-Hosting in Deutschland."

**Layer 3 — Feature-Ebene (30 Sekunden):**
> Persönliche Buchungsseite unter deiner Domain. Dienstleistungen mit Dauer, Mitarbeiter-Zuordnung, Pufferzeiten und Anzahlung. Automatische Reminder reduzieren No-Shows auf unter 2 %. Daten bleiben in Frankfurt.

**Layer 4 — Proof-Ebene (2 Minuten):**
> Konkrete Fallstudie: Salon Julia, Solo-Friseurin — von Instagram-DM zu eigener Buchungsseite, No-Show-Quote von 12 % auf 1,8 %, 38 % mehr Buchungen außerhalb der Öffnungszeiten.

---

## IV. MARKETINGPSYCHOLOGIE

### 4.1 Schmerzpunkte & Verlustangst (Loss Aversion)

Menschen empfinden Verluste 2× stärker als gleichwertige Gewinne (Kahneman/Tversky). Sirin kommuniziert daher primär über **konkret bezifferten Verlust**, nicht über abstrakten Gewinn.

| Schmerz | Bezifferung | Copy-Vorlage |
|---|---|---|
| No-Show-Verlust | 360–420 EUR/Monat/Stuhl | „Jeder verpasste Termin kostet durchschnittlich 38 EUR. Wie viele lässt du diese Woche los?" |
| Provisionskosten | 15–25 % pro Buchung | „Bei 100 Treatwell-Buchungen/Monat à 80 EUR zahlst du bis zu 2.000 EUR Provision. Monat für Monat." |
| Telefonzeit | ~2,5h/Woche für Terminkoordination | „2,5 Stunden Termintelefonie pro Woche = 10 Stunden pro Monat. Was könntest du damit anfangen?" |
| Leerlauf-Slots | ~3 leere Slots/Woche nach Stornos | „3 leere Slots pro Woche — dein Wartelisten-Kunde 15 Minuten entfernt weiß nichts davon." |

**Taktik:** Kostenkalkulator auf der Landingpage. Eingabefelder: Anzahl Mitarbeiter, durchschnittlicher Terminwert, No-Show-Quote, aktuelle Plattform-Provision. Output: „Du verlierst X EUR/Monat. Sirin kostet Y EUR/Monat."

### 4.2 Social Proof — Vertrauensstufen

| Stufe | Format | Psychologischer Mechanismus |
|---|---|---|
| **Zahl** | „Über 1.200 Dienstleister buchen mit Sirin" | Herdentrieb: „Andere haben entschieden" |
| **Bewertung** | „4,9 ★ (247 Bewertungen)" | Autorität durch Masse |
| **Testimonial** | Foto + Name + Branche + konkretes Ergebnis | Identifikation: „Das bin ich" |
| **Fallstudie** | Vorher/Nachher-Zahlen mit realem Anbieter | Beweis statt Versprechen |
| **Logo-Wall** | Bekannte Brands als Nutzer | Halo-Effekt / Autorität |
| **Medienerwähnungen** | „Bekannt aus …" | Drittvalidierung |

**Wichtigste Regel:** Testimonials immer mit konkreten Zahlen. Nicht „Ich bin sehr zufrieden." Sondern: „Seit Sirin habe ich 40 % weniger Telefonanrufe und meine Kunden kommen zuverlässiger — Julia, Friseurmeisterin, Berlin."

### 4.3 Anchoring & Preispsychologie

**Anchoring-Strategie:**
1. **Verlust-Anker zuerst** zeigen: „Treatwell nimmt 15–25 % Provision = bis zu 2.000 EUR/Monat"
2. **Dann Sirin-Preis** zeigen: „Sirin Pro: 69 EUR/Monat. Alles inklusive."
3. Anchoring-Effekt: 69 EUR wirkt mikroskopisch klein nach dem 2.000-EUR-Verlust-Anker.

**Preistabelle-Psychologie:**
- **Pro-Tier visuell hervorheben** (größer, farblich abgehoben, Badge „Beliebt") — Decoy-Effekt
- **Starter als Einstieg** kommunizieren: „Für 1 EUR pro Tag" statt „29 EUR/Monat"
- **Free-Tier** sichtbar lassen — senkt Conversion-Hemmung, erhöht Trial-Einstieg
- **Business-Tier** als Anker nach oben: 149 EUR macht 69 EUR günstig erscheinen
- **Jährliche Zahlung** als Option mit 2 Monate gratis: „Spare 58 EUR"

### 4.4 Commitment & Consistency (Cialdini)

**Micro-Commitments im Funnel:**
1. E-Mail-Adresse eingeben für Demo → kleines Commitment
2. Eigenen Slug eingeben (termin.**meinsalon**.de) → Eigentumseffekt, investiert
3. Erste Dienstleistung anlegen in Onboarding → Fortschritts-Commitment
4. Erste Demo-Buchung absenden → Erleben des Endkunden-Erlebnisses

**Principle:** Wer einmal „meinen Salon" geschrieben hat, kauft eher.

### 4.5 Reziprozität

**Wert zuerst geben, dann verkaufen:**
- Kostenloser ROI-Kalkulator (kein E-Mail erforderlich)
- No-Show-Guide als Download (E-Mail erforderlich — Lead-Magnet)
- 14-Tage-Testphase ohne Kreditkarte
- Kostenlose Demo-Buchungsseite (sofort nutzbar, Branding limitiert)
- Branchenspezifischer Setup-Guide: „5-Minuten-Einrichtung für Friseure"

### 4.6 Authority & Expertise (Autorität)

**Autoritäts-Signale für Sirin:**
- Datierte Quellenangaben (Bitkom 2026, DSGVO Art. 9) — wirkt recherchiert, seriös
- „Entwickelt im DACH-Raum für DACH-Anforderungen" — lokale Autorität
- DSGVO-Badge + EU-Hosting-Siegel prominent
- Stripe-Partner-Logo (Zahlungssicherheit)
- Echte Gesichter der WAMOCON-Gründer (Credibility)

### 4.7 Scarcity & Urgency (sparsam einsetzen)

- „Kostenloser Onboarding-Call — noch 3 Plätze diese Woche"
- „Starter-Aktionspreis 19 EUR/Monat bis [Datum]"
- **Wichtig:** Nur echte Scarcity nutzen. Gefälschte Dringlichkeit zerstört Vertrauen.

### 4.8 IKEA-Effekt (Ownership)

Nutzer, die etwas selbst gestalten, bewerten es höher.
- Eigenen Slug wählen lassen: `sirin.app/[meinname]`
- Logo hochladen, Farben wählen — sofort sichtbar auf der eigenen Buchungsseite
- Erste Dienstleistung anlegen → direkte Vorschau der öffentlichen Seite
- „Deine Buchungsseite ist fertig" als emotionaler Milestone-Moment

### 4.9 Peak-End-Regel

Menschen erinnern sich an den **intensivsten Moment** und das **Ende** einer Erfahrung.
- **Peak:** Das erste Mal, dass der Nutzer seine eigene Buchungsseite live sieht (Onboarding-Moment — maximaler WOW-Effekt einbauen)
- **End:** Jede Buchungsbestätigung muss emotional positiv sein. Nicht „Termin gespeichert." Sondern: „Dein Termin bei Julia ist gesichert. Wir erinnern dich rechtzeitig."

### 4.10 Cognitive Load Reduction (Reduktion kognitiver Last)

- Onboarding in max. 3 Schritte: Dienstleistung anlegen → Buchungsseite teilen → erste Buchung empfangen
- Keine Entscheidungen in Formularen, die der Nutzer nicht treffen muss
- Smarte Defaults: „45 Minuten, 10 Min Puffer nach" als Friseur-Preset
- Progress Bar im Setup-Wizard
- Tooltips nur on-demand, nicht permanent sichtbar

---

## V. CUSTOMER JOURNEY & FUNNEL

### 5.1 Awareness-Phase

**Ziel:** Potenzielle Anbieter kennenlernen, dass Sirin existiert und ihr Problem löst.

**Kanäle & Touchpoints:**
| Kanal | Format | Botschaft |
|---|---|---|
| **Instagram / TikTok** | Reel: „3 Fehler, die Friseure beim Terminmanagement machen" | Pain-Activation, Problem-Awareness |
| **Google SEO** | „Buchungssoftware Friseur", „online Terminbuchung Physiotherapie", „Calendly Alternative DSGVO" | Intent-basiert |
| **Google Ads** | Keyword: Treatwell Alternative, Shore+ Alternative | Competitor Displacement |
| **LinkedIn** | Artikel: „Warum 76 % Ihrer Kunden einen Online-Buchungslink erwarten" | B2B-Entscheider |
| **Facebook-Gruppen** | Friseur-Fachgruppen, Praxis-Management-Gruppen | Community-Seeding |
| **Mundpropaganda** | Anbieterprofil → Endkunden buchen → Endkunden empfehlen | Viraler Loop |

### 5.2 Consideration-Phase

**Ziel:** Nutzer auf Landingpage halten, Vergleich gewinnen, E-Mail gewinnen.

**Touchpoints:**
- Landingpage mit vollständiger Feature-Erklärung
- Demo-Buchungsseite (interaktiv testbar, ohne Registrierung)
- ROI-Kalkulator
- Vergleichstabelle: Sirin vs. Calendly vs. Shore+ vs. Treatwell
- Testimonials nach Branche gefiltert
- FAQ-Sektion

### 5.3 Decision-Phase

**Ziel:** Free Trial oder Starter-Kauf abschließen.

**Conversion-Trigger:**
- „Kostenlos starten" — keine Kreditkarte, sofort loslegen
- Branchenspezifischer CTA: „Einrichtung für Friseure: 5 Minuten"
- Social Proof direkt am CTA: „1.200+ Betriebe nutzen bereits Sirin"
- Exit-Intent: „Bevor du gehst — kostenloser ROI-Check per E-Mail"

### 5.4 Onboarding-Phase (Activation)

**Ziel:** Nutzer erlebt den AHA-Moment. Eigene Buchungsseite live sehen.

**3-Schritt-Onboarding:**
1. **Organisation anlegen** (Name + Slug) → Buchungs-URL sofort sichtbar
2. **Erste Dienstleistung** anlegen (Preset-Vorlagen: Haarschnitt, Rückentherapie, Shooting)
3. **Buchungsseite teilen** → QR-Code für Visitenkarte generieren

**AHA-Moment:** Sobald die öffentliche Buchungsseite unter `sirin.app/meinname` live ist → Konfetti-Animation + „Deine Buchungsseite ist live. Teile sie mit deinen Kunden."

### 5.5 Retention-Phase (Kundenbindung)

**Ziel:** Nutzer bleibt und empfiehlt.

| Mechanismus | Beschreibung |
|---|---|
| **Wöchentlicher Report** | E-Mail: „Diese Woche: 23 Buchungen, 0 No-Shows, 3 neue Kunden" |
| **Meilenstein-E-Mails** | „100. Buchung auf Sirin — Herzlichen Glückwunsch!" |
| **Feature-Nudges** | „Noch nicht getestet: Lückenfüller. Aktiviere ihn in 1 Klick." |
| **Erfolgsgeschichten** | Quarterly „Was andere Anbieter erreicht haben" Newsletter |
| **Upgrade-Trigger** | Wenn 3 Mitarbeiter-Limit erreicht → sanfte Pro-Einladung |

### 5.6 Advocacy-Phase (Referral)

| Mechanismus | Beschreibung |
|---|---|
| **Viraler Loop** | Buchungsseite enthält Sirin-Branding (Free-Tier) → Endkunden sehen Marke |
| **Referral-Programm** | „Empfiehl Sirin — 1 Monat gratis für dich und deinen Kollegen" |
| **Review-Routing** | Zufriedene Anbieter → App Store / Google-Review-Einladung |
| **Instagram-Tag** | Anbieter posten ihre Buchungsseite mit @sirin_app |

---

## VI. LANDINGPAGE — STRUKTUR & CONTENT

### 6.1 Hero Section (Above the Fold)

**Ziel:** In 3 Sekunden klar machen, WAS es ist, FÜR WEN es ist und WARUM JETZT.

```
EYEBROW:    Buchungsplattform für Dienstleister im DACH-Raum

HEADLINE:   Termine, die rufen.

SUBLINE:    Sirin ist die einladende Buchungsplattform für Friseure, Physios,
            Beauty, Tierärzte und alle, die Zeit verkaufen — mit echten
            Dienstleistungen statt leeren Slots. DSGVO-nativ. Kein Lock-in.

CTA 1:      [Kostenlos starten] (Primary — Gold, #E6B566)
CTA 2:      [Live-Demo ansehen] (Secondary — Outline)

TRUST-BAR:  ⭐ 4,9 · 247 Bewertungen  |  1.200+ aktive Anbieter  |  24/7 online buchbar
```

**Visuell:** Split-Screen — links: warme Atmosphäre (Friseursalon, goldenes Licht), rechts: Buchungsseite auf Smartphone. Animation: Buchungsbestätigung poppt auf dem Handy auf.

### 6.2 Pain Section — „Kennst du das?"

**Ziel:** Schmerz aktivieren, Kopfnicken auslösen. Keine Lösung zeigen — erst Schmerz spiegeln.

```
HEADLINE: Klingelt dein Handy gerade während der Behandlung?

PAIN CARDS (3er-Grid):
┌─────────────────────────────────────┐
│ 📵 Unterbrechungen                  │
│ Du greifst mitten in die Arbeit,    │
│ um einen Termin zu notieren —       │
│ den du drei Tage später nicht mehr  │
│ weißt.                              │
└─────────────────────────────────────┘

┌─────────────────────────────────────┐
│ 💸 No-Shows                         │
│ Dienstag, 14 Uhr. Stuhl leer.       │
│ Kein Anruf. Kein WhatsApp.          │
│ 38 EUR einfach weg.                 │
└─────────────────────────────────────┘

┌─────────────────────────────────────┐
│ 🔗 Provision                        │
│ Treatwell schickt dir Kunden —      │
│ und nimmt 20 % dafür. Jeden Monat.  │
│ Für immer.                          │
└─────────────────────────────────────┘
```

### 6.3 Solution Section — „So löst Sirin das"

**Ziel:** Direkte Schmerzlösung zeigen. Feature → Nutzen-Verknüpfung.

```
HEADLINE: Sirin übernimmt — du behandelst.

FEATURE CARDS (2×3 Grid):

1. DIENSTLEISTUNGEN, KEINE SLOTS
   "Dein Haarschnitt hat 45 Minuten, 10 Min Puffer,
    kostet 58 EUR und gehört zu Julia — nicht zu
    einem generischen Kalender-Block."

2. EIGENE MARKE, EIGENE DOMAIN
   "termin.salon-julia.de — nicht calendly.com/julia.
    Dein Logo. Deine Farben. Deine Buchungsseite."

3. NO-SHOW-SCHUTZ
   "Automatische Reminder 48h, 24h, 2h vor dem Termin.
    Optional: Anzahlung bei Buchung via Stripe.
    No-Show-Quote sinkt auf unter 2 %."

4. LÜCKENFÜLLER
   "Stornierung um 16:20 Uhr? Deine Wartelisten-Kunden
    bekommen sofort eine Benachrichtigung — mit freiem
    Slot und optionalem Rabatt."

5. EU-HOSTING, DSGVO-NATIV
   "Daten in Frankfurt. Art. 9-konform für Heilberufe.
    Kein US-Server. Kein Datenschutz-Risiko."

6. KEIN PROVISIONS-MODELL
   "Flat Fee. Kein Anteil an deinen Einnahmen.
    Was du verdienst, gehört dir."
```

### 6.4 How It Works Section — „3 Schritte"

```
HEADLINE: In 5 Minuten buchbar.

STEP 1: Dienstleistungen anlegen
        Leistung, Dauer, Preis, Mitarbeiter, Puffer —
        fertige Vorlagen für Friseur, Physio, Beauty.

STEP 2: Buchungsseite teilen
        Link auf Instagram, Website, Visitenkarte.
        QR-Code zum Ausdrucken inklusive.

STEP 3: Termine empfangen
        Kunden buchen selbst. Du bekommst
        die Bestätigung — und kannst weiterarbeiten.
```

### 6.5 Social Proof Section — „Wer bereits Sirin nutzt"

```
HEADLINE: Was echte Anbieter sagen.

TESTIMONIAL 1 (Friseurin):
  ⭐⭐⭐⭐⭐
  "Ich nehme keine Terminanrufe mehr während der Arbeit an.
   Meine Kunden buchen selbst — und kommen zuverlässiger als je zuvor."
  — Sarah K., Friseurmeisterin, München

TESTIMONIAL 2 (Physio):
  ⭐⭐⭐⭐⭐
  "DSGVO war mein größtes Problem mit anderen Tools.
   Sirin läuft auf EU-Servern — das war der Dealmaker."
  — Björn H., Physiotherapeut, Zürich

TESTIMONIAL 3 (Solo-Kosmetikerin):
  ⭐⭐⭐⭐⭐
  "In 8 Minuten eingerichtet. Buchungsseite sieht aus wie von
   einem Webdesigner gemacht. Kein Vergleich zu Treatwell."
  — Maria S., Kosmetikerin, Wien

ZAHLEN-ROW:
  [1.200+]      [4,9 ★]       [38%]          [<2%]
  Aktive        Bewertungs-   Mehr Buchungen  No-Show-Quote
  Anbieter      durchschnitt  außerhalb der   nach 90 Tagen
                              Öffnungszeiten
```

### 6.6 Preistabelle Section

```
HEADLINE: Faires Flat-Pricing. Keine Provision. Keine Überraschungen.

PRE-HEADER: "Treatwell nimmt bis zu 25 % auf jede Buchung.
             Sirin nimmt einen festen Monatsbetrag — fertig."

┌──────────┬──────────┬──────────┬──────────┐
│  FREE    │ STARTER  │   PRO    │ BUSINESS │
│  0 EUR   │ 29 EUR   │ 69 EUR   │ 149 EUR  │
│          │ /Monat   │ /Monat ★ │ /Monat   │
├──────────┼──────────┼──────────┼──────────┤
│1 Mitarb. │3 Mitarb. │10 Mitarb.│ Unbegr.  │
│20 Buchg. │Unbegrenzt│Unbegrenzt│Unbegrenzt│
│Sirin-    │Eigene    │Eigene    │Eigene    │
│Branding  │Domain    │Domain    │Domain    │
│E-Mail    │E-Mail-   │+SMS      │+API      │
│          │Reminder  │+Stripe   │+Priority │
│          │          │+Multi-   │+AI-Add-on│
│          │          │Standort  │          │
├──────────┼──────────┼──────────┼──────────┤
│[Starten] │[Starten] │[Starten] │[Kontakt] │
└──────────┴──────────┴──────────┴──────────┘
                         ↑
                    [Beliebt] Badge

FOOTER-NOTE: "Alle Preise inkl. MwSt. · Jederzeit kündbar ·
              Keine Kreditkarte für Free- und Trial-Einstieg"
```

### 6.7 ROI-Kalkulator Section

```
HEADLINE: Berechne, was du verlierst.

SUBLINE: Gib deine Zahlen ein — wir zeigen dir, was dich
         dein aktuelles System monatlich kostet.

INPUTS:
  [__] Mitarbeitende mit Terminen
  [__] Durchschnittlicher Terminwert (EUR)
  [__] Termine pro Woche (gesamt)
  [__] Aktuelle No-Show-Quote (%)
  [__] Aktuell genutzte Plattform: [Dropdown: Treatwell/Doctolib/Shore+/Telefon+Papier/Andere]

OUTPUT (Karte, prominent):
  ┌───────────────────────────────────────────────────┐
  │ Du verlierst monatlich:                           │
  │                                                   │
  │  💸 480 EUR durch No-Shows                        │
  │  💸 1.840 EUR durch Treatwell-Provision           │
  │  ⏱  10 Stunden Termintelefonie                   │
  │                                                   │
  │  Gesamt: ~2.320 EUR / Monat                       │
  │                                                   │
  │  Sirin Pro kostet dich: 69 EUR / Monat            │
  │                                                   │
  │  [Jetzt 14 Tage kostenlos testen]                 │
  └───────────────────────────────────────────────────┘
```

### 6.8 Competitor-Vergleich Section

```
HEADLINE: Warum nicht Calendly? Warum nicht Shore+?

TABELLE:
                    Sirin    Calendly  Shore+   Treatwell
Dienstleistungen      ✅       ❌        ✅        ✅
Eigene Domain         ✅       ❌        ✅        ❌
EU-Hosting            ✅       ❌        ✅        ❌
DSGVO Art. 9          ✅       ❌        ⚠️        ❌
Pufferzeiten          ✅       ❌        ✅        ✅
Ressourcen-Bindung    ✅       ❌        ✅        ⚠️
No-Show-Anzahlung     ✅       ❌        ✅        ❌
Kein Provisions-Modell ✅     ✅        ✅        ❌
Lückenfüll-Logik      ✅       ❌        ⚠️        ⚠️
Preis / Monat         €29–149  $10–16   €79+     15–25%
```

### 6.9 Branchenspezifische Sektionen

**Tab-System oder separate Sektionen:**

```
[Friseure & Beauty] [Physio & Heilberufe] [Tierärzte] [Fotografen] [Coaches]

AKTIVER TAB: Friseure & Beauty

  HEADLINE: Sirin kennt Friseure.

  "Haarschnitt. Tönung. Dauerwelle. Balayage.
   Jede Leistung mit ihrer eigenen Dauer, ihrem Preis,
   ihrer Stylistin und ihrem Puffer für die Reinigung danach.
   Kein Slot-Gedanke mehr."

  CHECKLISTE:
  ✅ Stuhl- und Waschplatz-Zuordnung
  ✅ Farbmischzeit als separate Ressource buchbar
  ✅ Wiederholungsbuchungen (z.B. alle 6 Wochen)
  ✅ No-Show-Anzahlung für Färbungen ab X EUR
  ✅ Instagram-Link direkt auf Buchungsseite
  ✅ QR-Code für Schaufenster und Visitenkarte
```

### 6.10 FAQ Section

**Psychologisches Ziel:** Verbleibende Kaufhemmungen proaktiv auflösen.

```
HÄUFIGE FRAGEN:

Q: Muss ich mein aktuelles System sofort kündigen?
A: Nein. Teste Sirin 14 Tage kostenlos parallel.
   Wir helfen dir beim Importieren deiner Kundendaten.

Q: Wie lange dauert die Einrichtung?
A: Die ersten 3 Dienstleistungen und die eigene
   Buchungsseite sind in 5–10 Minuten live.
   Branchenvorlagen machen es noch einfacher.

Q: Was passiert mit meinen Kundendaten wenn ich kündige?
A: Du kannst alle Daten jederzeit exportieren.
   Wir löschen sie DSGVO-konform nach Kündigung.

Q: Gibt es eine Vertragsbindung?
A: Nein. Monatlich kündbar. Jederzeit.

Q: Ist Sirin für Heilberufe (Physio, Heilpraktiker) geeignet?
A: Ja. Daten liegen auf EU-Servern in Frankfurt.
   Verarbeitung nach Art. 9 DSGVO. DPA auf Anfrage.

Q: Was kostet Sirin im Vergleich zu Treatwell?
A: Bei 100 Buchungen/Monat à 80 EUR zahlst du bei
   Treatwell 1.200–2.000 EUR Provision.
   Sirin Pro kostet 69 EUR flat.
```

### 6.11 CTA-Sektion (Bottom of Page)

```
HEADLINE: Dein nächster Termin wartet schon.

SUBLINE: Richte deine Buchungsseite in 5 Minuten ein.
         Keine Kreditkarte. Kein Risiko.

CTA: [Kostenlos starten — dauert 5 Minuten]

MICRO-COPY UNTER CTA:
"Keine Kreditkarte · Jederzeit kündbar · Daten in Deutschland"

TRUST-ICONS:
[EU-Hosting] [DSGVO] [Stripe Certified] [Made in DACH]
```

---

## VII. SEO & CONTENT-STRATEGIE

### 7.1 Primäre SEO-Keywords

| Keyword | Intent | Monatl. Volumen (DACH, geschätzt) | Priorität |
|---|---|---|---|
| Buchungssoftware Friseur | Commercial | 1.800 | ★★★ |
| Online Terminbuchung Physiotherapie | Commercial | 1.200 | ★★★ |
| Calendly Alternative DSGVO | Commercial | 900 | ★★★ |
| Treatwell Alternative | Commercial | 600 | ★★★ |
| Shore Plus Alternative | Commercial | 400 | ★★ |
| Terminbuchung Software KMU | Commercial | 2.200 | ★★★ |
| Online Buchungsseite erstellen | Informational | 3.400 | ★★ |
| No-Show Friseur reduzieren | Informational | 800 | ★★ |
| DSGVO konforme Terminbuchung | Commercial | 1.100 | ★★★ |
| Buchungssystem Tierarzt | Commercial | 700 | ★★ |

### 7.2 Content-Marketing-Plan

**Lead-Magnets (E-Mail-Capture):**
1. „No-Show-Ratgeber: 7 Strategien, die funktionieren" (PDF, 8 Seiten)
2. „Praxis-Checkliste: Online-Terminbuchung für Heilberufe einführen" (PDF)
3. „ROI-Rechner: Was dich dein aktuelles System kostet" (Interaktiv, kein E-Mail)

**Blog-Themen (SEO + Authority):**
- „Warum Calendly für Friseure nicht funktioniert"
- „DSGVO und Patientendaten: Worauf Heilberufe bei Buchungssoftware achten müssen"
- „No-Show-Rate unter 2 %: Wie automatische Reminder funktionieren"
- „Eigene Buchungsseite vs. Marktplatz: Was dir langfristig mehr bringt"
- „5 Zeichen, dass du zu viel Zeit mit Termintelefonie verlierst"

**Video-Content (Instagram/TikTok/YouTube Shorts):**
- „Einrichtung in 5 Minuten" — Bildschirmaufnahme + Voiceover
- Vorher/Nachher: „So sah mein Terminmanagement früher aus"
- Kundeninterview-Format: „3 Monate Sirin — was hat sich verändert?"

---

## VIII. E-MAIL-MARKETING & LIFECYCLE

### 8.1 Willkommens-Sequenz (Trial-Nutzer, 7 E-Mails)

| Tag | Betreff | Ziel |
|---|---|---|
| 0 | „Willkommen, [Name] — deine Buchungsseite wartet" | Aktivierung, Setup-Start |
| 1 | „Hast du schon deine erste Dienstleistung angelegt?" | Onboarding-Nudge |
| 3 | „So haben andere [Branche] Betriebe gestartet" | Soziale Validierung |
| 5 | „No-Shows auf unter 2 % — aktiviere Reminder jetzt" | Feature-Adoption |
| 7 | „Dein erstes Wochenende mit Sirin: [X] Buchungen" | Wert-Demonstration |
| 10 | „[Name], bevor dein Test endet..." | Conversion-Push |
| 14 | „Letzter Tag: Hier ist ein besonderer Anlass" | Final-Conversion + Incentive |

### 8.2 Wöchentliche Performance-E-Mail (aktive Nutzer)

```
BETREFF: [Salon Julia] — Diese Woche auf Sirin

  Diese Woche:
  ✅ 23 Buchungen
  ⭕ 1 No-Show (Reminder sendet automatisch)
  ⭐ 2 neue Kunden
  💰 1.840 EUR geplanter Umsatz

  Dein bester Tag: Donnerstag (7 Buchungen)
  Leerste Zeit: Dienstag 14–16 Uhr → Warteliste aktivieren?

  [Lückenfüller aktivieren]
```

### 8.3 Reaktivierungs-Sequenz (inaktive Nutzer, nach 30 Tagen)

```
BETREFF: Deine Buchungsseite vermisst dich.

  Seit 30 Tagen keine Buchungen über Sirin.
  Das kann zwei Gründe haben:

  1. Du hast noch keinen Buchungslink geteilt.
  2. Dein Setup ist nicht fertig.

  Wir lösen das in 10 Minuten:
  [Kostenloser Setup-Anruf buchen]
```

---

## IX. BRANCHENSPEZIFISCHE MESSAGING-FRAMEWORKS

### 9.1 Friseure & Beauty

**Primär-Headline:** „Dein Stuhl. Deine Kunden. Dein Tempo."
**Pain-Hook:** „Wie viele Anrufe hast du letzte Woche verpasst?"
**USP-Fokus:** Eigene Buchungsseite + No-Show-Schutz
**Tone:** Persönlich, Instagram-nah, stylish

### 9.2 Physiotherapie & Heilberufe

**Primär-Headline:** „Patientendaten sicher. Termine automatisch."
**Pain-Hook:** „Liegt deine Buchungssoftware auf US-Servern?"
**USP-Fokus:** DSGVO-Compliance + Ressourcenbindung (Geräte)
**Tone:** Professionell, sachlich, vertrauenswürdig

### 9.3 Tierärzte

**Primär-Headline:** „Mehr Zeit für Patienten. Weniger Zeit am Telefon."
**Pain-Hook:** „14 Uhr, Sprechstunde läuft — Telefon klingelt"
**USP-Fokus:** 24/7-Buchung + Kundenkarte (Tierhistorie)
**Tone:** Warm, fürsorglich, praktisch

### 9.4 Fotografen & Kreatve

**Primär-Headline:** „Buche Shootings. Nicht Zeitfenster."
**Pain-Hook:** „Anzahlung vergessen? No-Show beim 4-Stunden-Shooting?"
**USP-Fokus:** Anzahlung via Stripe + Paketbuchungen + lange Vorlaufzeiten
**Tone:** Kreativ, professionell, wertvoll

### 9.5 Coaches & Berater

**Primär-Headline:** „Deine Zeit hat einen Wert. Lass sie auch so klingen."
**Pain-Hook:** „Wie viel Zeit verbringst du mit Terminkoordination statt Beratung?"
**USP-Fokus:** Saubere eigene Buchungsseite + Kundenhistorie + Follow-up-Buchungen
**Tone:** Kompetent, empowernd, modern

---

## X. KAMPAGNEN-IDEEN

### 10.1 Launch-Kampagne — „Der leere Stuhl"

**Konzept:** Virale Instagram/TikTok-Kampagne.
„Zeig uns deinen leeren Stuhl und tagge uns mit #MeinSirinMoment"
Preis: 6 Monate Sirin Pro gratis für die beste Story.
Mechanismus: Persönliche Identifikation, Community-Bildung, UGC-Generierung.

### 10.2 Partner-Kampagne — „Empfiehl Sirin, profitiere mit"

**Konzept:** Affiliate-Programm für Friseur-Lieferanten, Kosmetik-Großhändler, Praxisberater.
10 % Provision für 12 Monate auf alle Empfehlungen.
Partner-Portal mit eigenem Link und Dashboard.

### 10.3 Retargeting-Kampagne — „Du weißt bereits, was du verlierst"

**Zielgruppe:** Website-Besucher, die den ROI-Kalkulator genutzt, aber nicht konvertiert haben.
**Botschaft:** „Du hast berechnet: X EUR Verlust pro Monat. Sirin kostet Y EUR."
**CTA:** „Starte jetzt — erster Monat kostenlos."

### 10.4 Saisonale Kampagne — „Vorbereitungen für die Hochsaison"

**Timing:** März (Frühling), September (Herbst)
**Botschaft:** „Hochsaison kommt. Ist dein Terminmanagement bereit?"
**Hook:** „Deine Konkurrenz hat bereits Online-Buchung. Dein Kunde auch schon das Handy in der Hand."

---

## XI. TECHNISCHE LANDINGPAGE-ANFORDERUNGEN

### 11.1 Performance-Anforderungen

| Metrik | Zielwert |
|---|---|
| Core Web Vitals LCP | < 2,0s |
| CLS | < 0,1 |
| INP | < 150ms |
| Lighthouse Score | ≥ 90 |
| Mobile-First | Ja — >65 % der Besucher sind mobil (Dienstleister nutzen Handy) |

### 11.2 Conversion-Tracking-Punkte

1. **CTA-Klick** (Primary: „Kostenlos starten")
2. **E-Mail-Eingabe** im Lead-Formular
3. **Slug-Eingabe** im Onboarding (Eigentumseffekt)
4. **Demo-Buchung** abgeschlossen
5. **ROI-Kalkulator** genutzt (Event: kalkulator_complete)
6. **Testimonial-Video** angeklickt
7. **Pricing-Tier** angeklickt
8. **FAQ-Item** geöffnet (Exit-Intent-Signal)

### 11.3 A/B-Test-Prioritäten

| Test | Variante A | Variante B | Hypothesis |
|---|---|---|---|
| Hero Headline | „Termine, die rufen." | „Kein Telefon mehr während der Behandlung." | Pain-Fokus vs. Marken-Fokus |
| CTA Text | „Kostenlos starten" | „Meine Buchungsseite erstellen" | Besitz-Formulierung erhöht Klickrate |
| Trust Bar | Nur Zahlen | Zahlen + Sterne + Avatar | Social Proof Kombinationseffekt |
| Pricing CTA | „Starten" | „14 Tage kostenlos testen" | Explizite Risikofreiheit |
| Hero Visual | Salon-Atmosphäre | Buchungsseite auf Handy | Emotion vs. Produkt |

---

## XII. BRAND VOICE — COPY-BEISPIELE

### 12.1 Reminder-E-Mail (Endkunden-Perspektive)

```
BETREFF: Morgen ruft dein Termin bei Julia ✨

  Hallo Sarah,

  morgen um 14:30 Uhr bist du dran —
  Haarschnitt lang mit Styling bei Julia im Salon am Marktplatz.

  Alles gut für dich?
  [✅ Ich komme]  [🔄 Umbuchen]  [❌ Absagen]

  Bis morgen,
  Sirin für Salon Julia
```

### 12.2 Lückenfüller-Nachricht (Endkunden-Perspektive)

```
BETREFF: Ein Slot ruft dich — heute noch bei Julia

  Hallo Thomas,

  kurze Nachricht: Heute 16:30 Uhr ist plötzlich ein Termin
  frei geworden — Haarschnitt, 45 Minuten, bei Julia.

  Als kleinen Willkommensgruß: 15 % Rabatt.
  Gilt nur für die nächste Stunde.

  [Termin jetzt sichern]

  Bis heute Abend 🌊
  Sirin für Salon Julia
```

### 12.3 Onboarding-Willkommen (Dienstleister)

```
BETREFF: Deine Buchungsseite ist bereit, Julia.

  Hallo Julia,

  deine Buchungsseite unter sirin.app/salon-julia ist live.

  Was jetzt?
  → Teile den Link auf deiner Instagram-Bio
  → Drucke den QR-Code für dein Schaufenster
  → Warte auf deine erste Buchung

  Drei Dinge, die die meisten Nutzer in der ersten Woche tun:
  1. Automatische Reminder aktivieren (dauert 2 Klicks)
  2. Anzahlung für lange Termine einrichten
  3. Lückenfüller-Benachrichtigungen anschalten

  Du hast Fragen? Schreib einfach hier — wir antworten schnell.

  Herzlich,
  Das Sirin-Team
```

---

## XIII. KPI-RAHMEN & ERFOLGSMESSUNG

### 13.1 Marketing-KPIs

| KPI | Ziel (Monat 3) | Ziel (Monat 12) |
|---|---|---|
| Website-Besucher/Monat | 5.000 | 25.000 |
| Trial-Registrierungen | 250 | 1.200 |
| Trial → Paid Conversion | 18 % | 25 % |
| Churn Rate (monatlich) | < 5 % | < 3 % |
| Cost per Trial | < 15 EUR | < 8 EUR |
| Cost per Paying Customer | < 80 EUR | < 40 EUR |
| NPS | 40 | 60 |
| Organic Traffic Anteil | 20 % | 50 % |

### 13.2 Landingpage-KPIs

| Metrik | Benchmark | Ziel Sirin |
|---|---|---|
| Bounce Rate | 60–70 % | < 50 % |
| Time on Page | 90s | > 180s |
| CTA-Klickrate (Hero) | 2–4 % | 5–8 % |
| Trial-Conversion (Besucher → Registrierung) | 1–3 % | 3–5 % |
| ROI-Kalkulator-Nutzung | — | > 15 % der Besucher |

---

## XIV. ZUSAMMENFASSUNG FÜR LANDINGPAGEGENERATOR

### Pflicht-Elemente jeder Sirin-Landingpage:

1. ✅ **Markenname** immer „Sirin" — nie „Sirin App" oder „Sirin Software"
2. ✅ **Primärclaim** „Hör auf deine Zeit." ODER „Termine, die rufen." — immer einer davon
3. ✅ **Farbpalette** strikt: `#0E3A5F`, `#1F7A8C`, `#E6B566`, `#F5EFE6`, `#5A6B7B`
4. ✅ **Fonts** Playfair Display für Headlines, Inter/Manrope für Body
5. ✅ **Trust-Bar** mit Anbieterzahl + Bewertung + 24/7-Verfügbarkeit direkt unter Hero-CTA
6. ✅ **Pain-Section** — Schmerz-Aktivierung bevor Lösung gezeigt wird
7. ✅ **USP-Grid** 6 Features mit kurzem, verbenbasiertem Copy
8. ✅ **Testimonials** immer mit Name, Branche, konkretem Ergebnis
9. ✅ **Preistabelle** mit Pro-Tier hervorgehoben + Verlust-Anker vorher
10. ✅ **CTA** immer mit Micro-Copy: „Keine Kreditkarte · Jederzeit kündbar · Daten in Deutschland"
11. ✅ **ROI-Kalkulator** oder Kostenvergleich als konvertierende Sektion
12. ✅ **DSGVO/EU-Hosting-Badge** im Footer und nahe der Dateneingabe
13. ✅ **Footer-Claim** „Sirin ruft — und du willst kommen." — immer im Footer
14. ✅ **Legal-Links** Impressum · Datenschutz · AGB — WAMOCON GmbH

### Anti-Patterns — niemals verwenden:

- ❌ Stock-Photo-Lächelmodels
- ❌ „revolutionär" / „disruptiv" / „game-changing"
- ❌ „Tool" / „Software" / „App" als Hauptbezeichnung
- ❌ Kalte, blaue Corporate-Farbgebung ohne Warmtöne
- ❌ Preise ohne direkten Vergleich zu Alternatives-/Provisions-Kosten zeigen
- ❌ Generische CTAs wie „Mehr erfahren" oder „Hier klicken"
- ❌ Testimonials ohne konkrete Zahlen oder Vor-/Nachher-Kontext
- ❌ DSGVO-Hinweis nur im Footer-Kleingedruckten

---

*Dokument erstellt: Mai 2026 · WAMOCON GmbH · Intern vertraulich*
*Basis: Anforderungsdokument Sirin v1.0, Produktsystem, Markenspezifikation*

## ./legal-docs/agb.md
# Allgemeine Geschäftsbedingungen (AGB)

Stand: {{MONAT}} {{JAHR}}

## § 1 Geltungsbereich

(1) Diese Allgemeinen Geschäftsbedingungen (nachfolgend „AGB") der WAMOCON GmbH, Mergenthalerallee 79 - 81, 65760 Eschborn (nachfolgend „Anbieter"), gelten für alle Verträge über die Nutzung der Software-as-a-Service-Plattform {{PROJEKTNAME}} (nachfolgend „Plattform"), die über die Website {{DOMAIN}} bereitgestellt wird.

(2) Die Plattform richtet sich an Unternehmen und gewerbliche Nutzer (nachfolgend „Auftraggeber") sowie deren Benutzer (nachfolgend „Nutzer"). Es handelt sich um ein B2B-Angebot. Verbraucher im Sinne des § 13 BGB sind nicht Zielgruppe dieses Angebots.

(3) Abweichende, entgegenstehende oder ergänzende AGB des Auftraggebers werden nicht Vertragsbestandteil, es sei denn, der Anbieter stimmt deren Geltung ausdrücklich schriftlich zu.

## § 2 Vertragsschluss

(1) Die Darstellung der Plattform und ihrer Funktionen auf der Website stellt kein verbindliches Angebot im Sinne des § 145 BGB dar, sondern eine Aufforderung zur Abgabe eines Angebots (invitatio ad offerendum).

(2) Der Auftraggeber gibt ein verbindliches Angebot zum Abschluss eines Nutzungsvertrages ab, indem er den Registrierungsprozess auf der Plattform abschließt und diese AGB akzeptiert.

(3) Der Vertrag kommt zustande, wenn der Anbieter das Angebot des Auftraggebers durch Freischaltung des Zugangs annimmt.

## § 3 Leistungsbeschreibung

(1) Der Anbieter stellt dem Auftraggeber die Plattform als Software-as-a-Service (SaaS) über das Internet zur Verfügung.

(2) Der genaue Funktionsumfang ergibt sich aus der jeweils aktuellen Leistungsbeschreibung auf der Website.

(3) Der Anbieter ist berechtigt, die Plattform weiterzuentwickeln, zu erweitern und anzupassen. Wesentliche Einschränkungen des Funktionsumfangs werden dem Auftraggeber vorab mitgeteilt.

## § 4 Nutzungsrechte

(1) Der Anbieter räumt dem Auftraggeber für die Vertragslaufzeit ein einfaches, nicht übertragbares, nicht unterlizenzierbares Recht zur Nutzung der Plattform ein.

(2) Der Auftraggeber darf die Plattform nur für eigene betriebliche Zwecke nutzen.

## § 5 Pflichten des Auftraggebers

(1) Der Auftraggeber ist verpflichtet, seine Zugangsdaten geheim zu halten und vor dem Zugriff Dritter zu schützen.

(2) Der Auftraggeber stellt sicher, dass die Nutzung der Plattform im Einklang mit geltendem Recht erfolgt.

## § 6 Verfügbarkeit

(1) Der Anbieter bemüht sich um eine Verfügbarkeit der Plattform von 99,5 % im Jahresmittel.

(2) Nicht als Ausfallzeit gelten geplante Wartungsarbeiten, die vorab angekündigt werden.

## § 7 Datenschutz

Die Verarbeitung personenbezogener Daten erfolgt gemäß der Datenschutzerklärung des Anbieters und den Bestimmungen der DSGVO.

## § 8 Haftung

(1) Der Anbieter haftet unbeschränkt für Schäden aus der Verletzung des Lebens, des Körpers oder der Gesundheit sowie bei Vorsatz und grober Fahrlässigkeit.

(2) Im Übrigen ist die Haftung auf den vertragstypischen, vorhersehbaren Schaden begrenzt.

## § 9 Vertragslaufzeit und Kündigung

(1) Der Vertrag wird auf unbestimmte Zeit geschlossen und kann von beiden Parteien mit einer Frist von einem Monat zum Monatsende gekündigt werden.

(2) Das Recht zur außerordentlichen Kündigung aus wichtigem Grund bleibt unberührt.

## § 10 Schlussbestimmungen

(1) Es gilt das Recht der Bundesrepublik Deutschland unter Ausschluss des UN-Kaufrechts.

(2) Gerichtsstand ist Eschborn, sofern der Auftraggeber Kaufmann ist.

(3) Sollten einzelne Bestimmungen dieser AGB unwirksam sein, bleibt die Wirksamkeit der übrigen Bestimmungen davon unberührt.

---

> **Hinweis:** Dies ist ein Muster. Ersetze alle `{{PLATZHALTER}}` mit den projektspezifischen Informationen. Lass die AGB vor Veröffentlichung von einem Juristen prüfen.

## ./legal-docs/company-stamp.md
# Firmenstempel / Company Stamp

## Deutsch

### WAMOCON GmbH

**Geschäftsführer:** Dipl.-Ing. Waleri Moretz

**Anschrift:**
Mergenthalerallee 79 - 81
65760 Eschborn
Deutschland

**Kontakt:**
Telefon: +49 6196 5838311
E-Mail: info@wamocon.com

**Registrierung:**
Handelsregister: Eschborn HRB 123666
USt-IdNr.: DE344930486

---

## English

### WAMOCON GmbH

**Managing Director:** Dipl.-Ing. Waleri Moretz

**Address:**
Mergenthalerallee 79 - 81
65760 Eschborn
Germany

**Contact:**
Phone: +49 6196 5838311
Email: info@wamocon.com

**Registration:**
Commercial Register: Eschborn HRB 123666
VAT ID: DE344930486

## ./legal-docs/datenschutzerklaerung.md
# Datenschutzerklärung

Stand: {{MONAT}} {{JAHR}}

## 1. Verantwortlicher

Verantwortlicher im Sinne der Datenschutz-Grundverordnung (DSGVO) und anderer nationaler Datenschutzgesetze ist:

WAMOCON GmbH
Mergenthalerallee 79 - 81
65760 Eschborn
Telefon: +49 6196 5838311
E-Mail: info@wamocon.com
Projektkontakt: {{PROJEKT_EMAIL}}
Geschäftsführer: Dipl.-Ing. Waleri Moretz
Handelsregister: Eschborn HRB 123666
USt-ID: DE344930486

## 2. Überblick über die Datenverarbeitung

Diese Datenschutzerklärung gilt für die Website und Webanwendung {{PROJEKTNAME}} ({{DOMAIN}}).

Wir verarbeiten personenbezogene Daten unserer Nutzer grundsätzlich nur, soweit dies zur Bereitstellung einer funktionsfähigen Plattform sowie unserer Inhalte und Leistungen erforderlich ist.

## 3. Rechtsgrundlagen der Verarbeitung

- **Einwilligung** – Art. 6 Abs. 1 lit. a DSGVO
- **Vertragserfüllung** – Art. 6 Abs. 1 lit. b DSGVO
- **Rechtliche Verpflichtung** – Art. 6 Abs. 1 lit. c DSGVO
- **Berechtigtes Interesse** – Art. 6 Abs. 1 lit. f DSGVO

## 4. Hosting und Infrastruktur

### Vercel Inc.
Die Website und Webanwendung werden über Vercel gehostet. Dabei verarbeitet Vercel technisch notwendige Verbindungsdaten (IP-Adresse, Zeitstempel, Browserinformationen). Rechtsgrundlage: Art. 6 Abs. 1 lit. f DSGVO.

### Supabase Inc.
Für Datenbank, Authentifizierung, Dateispeicher und Teile der Backend-Infrastruktur nutzen wir Supabase. Verarbeitet werden Authentifizierungsdaten, Session-Informationen, Projektdaten sowie gespeicherte Medien. Rechtsgrundlage: Art. 6 Abs. 1 lit. b DSGVO.

## 5. Erhebung personenbezogener Daten

### Registrierung und Nutzerkonto
Bei der Registrierung erheben wir: Name, E-Mail-Adresse und Passwort. Diese Daten sind zur Vertragserfüllung erforderlich (Art. 6 Abs. 1 lit. b DSGVO).

### Server-Logfiles
Bei jedem Zugriff auf unsere Plattform werden automatisch folgende Daten erfasst: IP-Adresse, Datum und Uhrzeit, aufgerufene Seite, Referrer-URL, Browser-Typ und -Version. Rechtsgrundlage: Art. 6 Abs. 1 lit. f DSGVO.

## 6. Cookies und Tracking

Die Plattform verwendet technisch notwendige Cookies für Session-Management und Authentifizierung. Rechtsgrundlage: Art. 6 Abs. 1 lit. f DSGVO.

## 7. Rechte der betroffenen Personen

Sie haben das Recht auf:
- **Auskunft** (Art. 15 DSGVO)
- **Berichtigung** (Art. 16 DSGVO)
- **Löschung** (Art. 17 DSGVO)
- **Einschränkung der Verarbeitung** (Art. 18 DSGVO)
- **Datenübertragbarkeit** (Art. 20 DSGVO)
- **Widerspruch** (Art. 21 DSGVO)
- **Widerruf** erteilter Einwilligungen (Art. 7 Abs. 3 DSGVO)
- **Beschwerde** bei einer Aufsichtsbehörde (Art. 77 DSGVO)

## 8. Datensicherheit

Wir setzen technische und organisatorische Sicherheitsmaßnahmen nach dem Stand der Technik ein, um Ihre Daten gegen zufällige oder vorsätzliche Manipulation, Verlust, Zerstörung oder den Zugriff unberechtigter Personen zu schützen.

## 9. Änderung der Datenschutzerklärung

Wir behalten uns vor, diese Datenschutzerklärung anzupassen, um sie an geänderte Rechtslagen oder bei Änderungen der Plattform anzupassen.

---

> **Hinweis:** Dies ist ein Muster. Ersetze alle `{{PLATZHALTER}}` mit den projektspezifischen Informationen. Lass die Datenschutzerklärung vor Veröffentlichung von einem Juristen prüfen.

## ./legal-docs/impressum.md
# Impressum

Stand: {{MONAT}} {{JAHR}}

## WAMOCON GmbH

Mergenthalerallee 79 - 81
65760 Eschborn
Deutschland

## Kontakt

Telefon: +49 6196 5838311
E-Mail: info@wamocon.com
Projektkontakt: {{PROJEKT_EMAIL}}

## Vertretungsberechtigter Geschäftsführer

Dipl.-Ing. Waleri Moretz

## Registereintrag

Sitz der Gesellschaft: Eschborn
Handelsregister: Eschborn HRB 123666
Umsatzsteuer-Identifikationsnummer: DE344930486

## Angaben zum Angebot

{{PROJEKTNAME}} ist eine webbasierte Software-as-a-Service-Plattform für {{BESCHREIBUNG_DES_ANGEBOTS}}. Das Angebot richtet sich primär an Unternehmen und gewerbliche Nutzer.

---

> **Hinweis:** Ersetze alle `{{PLATZHALTER}}` mit den projektspezifischen Informationen.

## ./legal-docs/imprint.md
# Imprint (Legal Notice)

As of: {{MONTH}} {{YEAR}}

## WAMOCON GmbH

Mergenthalerallee 79 - 81
65760 Eschborn
Germany

## Contact

Phone: +49 6196 5838311
Email: info@wamocon.com
Project Contact: {{PROJECT_EMAIL}}

## Authorized Managing Director

Dipl.-Ing. Waleri Moretz

## Registration

Registered Office: Eschborn
Commercial Register: Eschborn HRB 123666
VAT Identification Number: DE344930486

## About the Service

{{PROJECT_NAME}} is a web-based Software-as-a-Service platform for {{SERVICE_DESCRIPTION}}. The service is primarily aimed at businesses and commercial users.

---

> **Note:** Replace all `{{PLACEHOLDERS}}` with your project-specific information.

## ./legal-docs/privacy-policy.md
# Privacy Policy

As of: {{MONTH}} {{YEAR}}

## 1. Data Controller

The Data Controller as defined by the General Data Protection Regulation (GDPR) is:

WAMOCON GmbH
Mergenthalerallee 79 - 81
65760 Eschborn, Germany
Phone: +49 6196 5838311
Email: info@wamocon.com
Project Contact: {{PROJECT_EMAIL}}
Managing Director: Dipl.-Ing. Waleri Moretz
Commercial Register: Eschborn HRB 123666
VAT ID: DE344930486

## 2. Overview of Data Processing

This Privacy Policy applies to the website and web application {{PROJECT_NAME}} ({{DOMAIN}}).

We process personal data of our users only insofar as this is necessary to provide a functional platform and our content and services.

## 3. Legal Basis for Processing

- **Consent** – Art. 6(1)(a) GDPR
- **Performance of Contract** – Art. 6(1)(b) GDPR
- **Legal Obligation** – Art. 6(1)(c) GDPR
- **Legitimate Interest** – Art. 6(1)(f) GDPR

## 4. Hosting and Infrastructure

### Vercel Inc.
The website and web application are hosted via Vercel. Vercel processes technically necessary connection data (IP address, timestamp, browser information). Legal basis: Art. 6(1)(f) GDPR.

### Supabase Inc.
We use Supabase for database, authentication, file storage, and parts of the backend infrastructure. Authentication data, session information, project data, and stored media are processed. Legal basis: Art. 6(1)(b) GDPR.

## 5. Collection of Personal Data

### Registration and User Account
During registration we collect: name, email address, and password. This data is necessary for the performance of the contract (Art. 6(1)(b) GDPR).

### Server Log Files
Each access to our platform automatically records: IP address, date and time, page accessed, referrer URL, browser type and version. Legal basis: Art. 6(1)(f) GDPR.

## 6. Cookies and Tracking

The platform uses technically necessary cookies for session management and authentication. Legal basis: Art. 6(1)(f) GDPR.

## 7. Rights of Data Subjects

You have the right to:
- **Access** (Art. 15 GDPR)
- **Rectification** (Art. 16 GDPR)
- **Erasure** (Art. 17 GDPR)
- **Restriction of processing** (Art. 18 GDPR)
- **Data portability** (Art. 20 GDPR)
- **Object** (Art. 21 GDPR)
- **Withdraw consent** (Art. 7(3) GDPR)
- **Lodge a complaint** with a supervisory authority (Art. 77 GDPR)

## 8. Data Security

We employ state-of-the-art technical and organisational security measures to protect your data against accidental or intentional manipulation, loss, destruction, or access by unauthorised persons.

## 9. Changes to this Privacy Policy

We reserve the right to amend this Privacy Policy to reflect changes in the law or changes to the platform.

---

> **Note:** This is a template. Replace all `{{PLACEHOLDERS}}` with your project-specific information. Have the Privacy Policy reviewed by a lawyer before publication.

## ./legal-docs/terms-and-conditions.md
# Terms and Conditions

As of: {{MONTH}} {{YEAR}}

## § 1 Scope

(1) These Terms and Conditions (hereinafter "T&C") of WAMOCON GmbH, Mergenthalerallee 79 - 81, 65760 Eschborn (hereinafter "Provider"), apply to all contracts for the use of the Software-as-a-Service platform {{PROJECT_NAME}} (hereinafter "Platform"), provided via the website {{DOMAIN}}.

(2) The Platform is aimed at businesses and commercial users (hereinafter "Client") and their respective users (hereinafter "Users"). This is a B2B offering. Consumers within the meaning of § 13 BGB (German Civil Code) are not the target audience.

(3) Deviating, conflicting, or supplementary terms and conditions of the Client shall not become part of the contract unless the Provider expressly agrees in writing.

## § 2 Conclusion of Contract

(1) The presentation of the Platform and its features on the website does not constitute a binding offer within the meaning of § 145 BGB, but rather an invitation to submit an offer (invitatio ad offerendum).

(2) The Client submits a binding offer by completing the registration process on the Platform and accepting these T&C.

(3) The contract is concluded when the Provider accepts the Client's offer by activating access.

## § 3 Service Description

(1) The Provider makes the Platform available to the Client as Software-as-a-Service (SaaS) via the Internet.

(2) The precise scope of features is set out in the current service description on the website.

(3) The Provider is entitled to further develop, expand, and adapt the Platform. Material restrictions to the scope of features will be communicated to the Client in advance.

## § 4 Usage Rights

(1) The Provider grants the Client a simple, non-transferable, non-sublicensable right to use the Platform for the duration of the contract.

(2) The Client may only use the Platform for its own business purposes.

## § 5 Client Obligations

(1) The Client shall keep its access credentials confidential and protect them from third-party access.

(2) The Client shall ensure that use of the Platform complies with applicable law.

## § 6 Availability

(1) The Provider shall endeavour to maintain an annual average availability of 99.5%.

(2) Scheduled maintenance windows announced in advance shall not count as downtime.

## § 7 Data Protection

The processing of personal data is governed by the Provider's Privacy Policy and the provisions of the GDPR.

## § 8 Liability

(1) The Provider shall be fully liable for damages arising from injury to life, body, or health, as well as for intent and gross negligence.

(2) Otherwise, liability is limited to foreseeable, typically occurring damages.

## § 9 Contract Duration and Termination

(1) The contract is concluded for an indefinite period and may be terminated by either party with one month's notice to the end of a calendar month.

(2) The right to extraordinary termination for good cause remains unaffected.

## § 10 Final Provisions

(1) The law of the Federal Republic of Germany shall apply, excluding the UN Convention on Contracts for the International Sale of Goods.

(2) The place of jurisdiction is Eschborn, provided the Client is a merchant.

(3) Should individual provisions of these T&C be invalid, the validity of the remaining provisions shall remain unaffected.

---

> **Note:** This is a template. Replace all `{{PLACEHOLDERS}}` with your project-specific information. Have the T&C reviewed by a lawyer before publication.

## package.json
{
  "name": "template_repo",
  "version": "0.1.0",
  "private": true,
  "scripts": {
    "dev": "next dev --turbopack",
    "build": "next build",
    "start": "next start",
    "lint": "eslint .",
    "lint:fix": "eslint . --fix",
    "typecheck": "tsc --noEmit",
    "verify": "npm run typecheck && npm run lint && npm run build",
    "test:e2e": "playwright test",
    "test:e2e:ui": "playwright test --ui",
    "gen:anforderungsdokument": "node scripts/generate-anforderungsdokument.mjs"
  },
  "dependencies": {
    "@supabase/ssr": "^0.10.2",
    "@supabase/supabase-js": "^2.104.1",
    "clsx": "^2.1.1",
    "date-fns": "^4.1.0",
    "docx": "^9.6.1",
    "leaflet": "^1.9.4",
    "lucide-react": "^1.11.0",
    "next": "16.2.1",
    "next-intl": "^4.9.1",
    "react": "19.2.4",
    "react-dom": "19.2.4",
    "tailwind-merge": "^3.5.0",
    "zod": "^4.3.6"
  },
  "devDependencies": {
    "@playwright/test": "^1.59.1",
    "@tailwindcss/postcss": "^4",
    "@types/leaflet": "^1.9.21",
    "@types/node": "^20",
    "@types/react": "^19",
    "@types/react-dom": "^19",
    "eslint": "^9",
    "eslint-config-next": "16.2.1",
    "supabase": "^2.95.3",
    "tailwindcss": "^4",
    "typescript": "^5"
  }
}

