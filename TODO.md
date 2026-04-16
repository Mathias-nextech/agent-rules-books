# TODO: Unified Software Engineering Rule Set

Goal: synthesize the existing book-inspired rule sets into one unified rule set that preserves all unique principles, removes duplicated guidance, and resolves apparent conflicts through explicit context-specific rules.

## Scope

- Source material:
  - `a-philosophy-of-software-design`
  - `clean-architecture`
  - `clean-code`
  - `code-complete`
  - `designing-data-intensive-applications`
  - `domain-driven-design`
  - `domain-driven-design-distilled`
  - `implementing-domain-driven-design`
  - `patterns-of-enterprise-application-architecture`
  - `refactoring`
  - `release-it`
  - `the-pragmatic-programmer`
  - `working-effectively-with-legacy-code`
- Target artifacts:
  - `unified-software-engineering/codex/AGENTS.md`
  - `unified-software-engineering/cursor/.cursor/rules/unified-software-engineering.mdc`
  - `unified-software-engineering/claude/.claude/rules/unified-software-engineering.md`
  - `README.md` updated so the unified rule set is discoverable and positioned correctly.

## Conflict-Resolution Policy

- Do not concatenate book rules. Normalize each principle into a single operational instruction.
- Keep context-specific guidance instead of forcing one global rule when books intentionally differ.
- Resolve common tensions this way:
  - Small functions vs deep modules: prefer cohesive units that are small enough to understand and deep enough to hide meaningful complexity; avoid micro-method noise.
  - Clean Architecture vs enterprise layering: for core business policy, dependencies point inward; for simpler enterprise transaction-script designs, keep responsibilities explicit without fake layers.
  - Rich domain model vs simple transaction script: choose the smallest business-logic pattern that fits actual domain complexity.
  - DRY vs premature abstraction: remove duplicated knowledge, not coincidental text.
  - Comments vs self-documenting code: improve names and structure first; comments are for contracts, rationale, invariants, and non-obvious facts.
  - Strong consistency vs eventual consistency: protect immediate invariants inside the smallest useful boundary; make cross-boundary consistency explicit and usually eventual unless product requirements prove otherwise.
  - Refactor aggressively vs preserve behavior: make small, behavior-preserving structural changes with proportionate validation.

## Checkpoints

### 1. Inventory and Coverage

- [x] List all existing canonical `codex/AGENTS.md` source files.
- [x] Inspect headings and source sizes to understand scope.
- [x] Read the source rule sets closely enough to identify unique principle families.
- [x] Build the unified section map so every book has a visible home in the synthesis.

Checkpoint validation:
- [x] All 13 source books are represented in the section map.
- [x] No target section exists only because of a book title; sections are organized by engineering decision area.

Unified section map:

- Purpose, priority, and conflict rules:
  - all books, especially Clean Code, Code Complete, The Pragmatic Programmer, A Philosophy of Software Design.
- Working workflow:
  - Refactoring, Working Effectively with Legacy Code, The Pragmatic Programmer, Code Complete.
- Naming, language, comments, and communication:
  - Clean Code, Code Complete, Domain-Driven Design, The Pragmatic Programmer, A Philosophy of Software Design.
- Construction, routines, control flow, variables, and contracts:
  - Clean Code, Code Complete, Refactoring, The Pragmatic Programmer.
- Module, interface, and dependency design:
  - A Philosophy of Software Design, Clean Architecture, Clean Code, Refactoring.
- Architecture and business logic placement:
  - Clean Architecture, Patterns of Enterprise Application Architecture, Domain-Driven Design.
- Domain modeling and DDD:
  - Domain-Driven Design, Domain-Driven Design Distilled, Implementing Domain-Driven Design.
- Enterprise application patterns:
  - Patterns of Enterprise Application Architecture, Clean Architecture, Implementing Domain-Driven Design.
- Data-intensive systems:
  - Designing Data-Intensive Applications, Release It!, Implementing Domain-Driven Design.
- Production readiness:
  - Release It!, Designing Data-Intensive Applications, The Pragmatic Programmer.
- Refactoring and legacy code:
  - Refactoring, Working Effectively with Legacy Code, Clean Code, A Philosophy of Software Design.
- Testing and verification:
  - all books, with specialized coverage from DDD, DDIA, Release It!, Refactoring, and Legacy Code.
- Automation, delivery, and feedback:
  - The Pragmatic Programmer, Code Complete, Release It!, Refactoring.
- Forbidden patterns and review checklist:
  - all books, deduplicated into decision-area checks.

### 2. Synthesis Design

- [x] Define the unified rule hierarchy:
  - purpose and priority
  - conflict-resolution rules
  - default work workflow
  - naming and communication
  - module/API/function construction
  - architecture and boundaries
  - domain modeling
  - enterprise application patterns
  - data-intensive systems
  - production readiness
  - refactoring and legacy code
  - testing and verification
  - automation and delivery
  - review checklist and forbidden patterns
- [x] Deduplicate repeated rules into one canonical phrasing.
- [x] Preserve unique details from specialized books:
  - DDD strategic design, context maps, distillation, aggregates, specifications, factories.
  - DDIA source of truth, consistency, idempotency, ordering, schema evolution, derived data.
  - Release It! timeouts, retries, circuit breakers, bulkheads, backpressure, observability, readiness.
  - Legacy-code seams, characterization tests, dependency breaking, sprout/wrap techniques.
  - PoEAA business-logic pattern selection, service layer, mappers/gateways, identity map, unit of work, remote facade, DTOs.
  - APoSD deep modules, information hiding, interface quality, special-general decomposition.
  - Clean Code and Code Complete construction, naming, routines, variables, comments, defensive programming.
  - Pragmatic Programmer DRY as knowledge, orthogonality, automation, feedback loops, tracer bullets.

Checkpoint validation:
- [x] Each specialized topic appears once, not repeated under several headings.
- [x] Apparent conflicts are handled as explicit decision rules.

### 3. Canonical Codex File

- [x] Create `unified-software-engineering/codex/AGENTS.md`.
- [x] Use the existing Codex convention: title `# AGENTS.md`, operational instructions, review checklist, final instruction.
- [x] Keep the file comprehensive but usable as an agent rule file.
- [x] Avoid copying book text; write practical synthesized rules.

Checkpoint validation:
- [x] The file can stand alone without requiring the individual book rule files.
- [x] It tells the agent when to use simpler vs richer patterns.
- [x] It contains no unresolved contradiction such as "always use DDD" and "avoid DDD ceremony" without context.

### 4. Tool Variants

- [x] Create Cursor variant at `unified-software-engineering/cursor/.cursor/rules/unified-software-engineering.mdc`.
- [x] Add Cursor frontmatter with `description` and `alwaysApply`.
- [x] Create Claude variant at `unified-software-engineering/claude/.claude/rules/unified-software-engineering.md`.
- [x] Ensure the body matches the canonical synthesized rule set except for tool-specific intro/title conventions.

Checkpoint validation:
- [x] All three files exist in the repository convention.
- [x] Cursor file has valid frontmatter.
- [x] Filenames use lowercase kebab-case.

### 5. README Update

- [x] Add a short section that explains the unified rule set.
- [x] Make clear it is a synthesized default and should not usually be combined with all individual book rules.
- [x] Keep the existing book list intact.
- [x] Keep ignored local source archives out of the README.

Checkpoint validation:
- [x] README still explains books, choosing rules, repository layout, and supported tools.
- [x] The unified set is discoverable before users choose individual books.

### 6. Verification

- [x] Run file inventory checks for the new directory.
- [x] Verify all Markdown/Cursor files are present.
- [x] Check TODO completion state.
- [x] Check git diff for unintended edits.
- [x] Review final unified file against the source coverage map.

Checkpoint validation:
- [x] `rg --files --hidden -g '!.git/**' unified-software-engineering` lists the three expected files.
- [x] `git diff --stat` shows only intended files.
- [x] No source book directories were modified accidentally.
