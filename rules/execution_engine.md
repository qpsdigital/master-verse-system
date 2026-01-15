==================================================
RULES — EXECUTION ENGINE (CORE)
VERSION: v4.6
CHANGE TYPE: ADDITIVE (FOUNDATION)
SCOPE: GLOBAL
==================================================

PURPOSE
- Defines the deterministic execution engine behavior.
- Ensures the engine is file-driven (repo truth only), not chat-memory-driven.
- Enforces validation BEFORE any preview/export logic.
- This file contains rules only (no verse data, no templates).

==================================================
1) TRUST MODEL (ABSOLUTE)
==================================================
- The engine trusts ONLY what exists in the repository paths listed in ENGINE_INDEX.md.
- No conversational memory is trusted.
- No implied defaults.
- No inferred context.

If any referenced file is missing:
→ EXECUTION MUST FAIL — MISSING_CANONICAL_FILE

==================================================
2) INPUTS (SUPPORTED)
==================================================
The engine supports these command-driven inputs:

A) EXECUTION COPY BLOCK (recommended)
- A structured block containing:
  - VERSION (optional; defaults handled by execution_context.md)
  - EXECUTION CONTEXT (LIVE or ARCHIVE)
  - EXECUTE trigger (see execution_triggers.md)
  - VERSE number (1–30)
  - TIER (A–F)
  - DESIGN (1–10)

B) Direct command messages (handled by approve_export_commands.md)
- Export trigger command (current canonical export keyword is defined there)

==================================================
3) VALIDATION FIRST (MANDATORY)
==================================================
Before any PREVIEW generation is allowed, the engine MUST validate:

- Verse range valid
- Tier valid
- Design valid
- Verse exists in loaded master table
- Tier exists for verse (including intentionally omitted tiers)
- Tier text pulled is canonical for the resolved version set
- Execution context + trigger rules satisfied

If any validation fails:
→ OUTPUT INVALID with the appropriate error code

==================================================
4) CANONICAL DATA RESOLUTION (LOCKED)
==================================================
Resolution order for tier text:

1) Load SEALED baseline data (v3.9)
2) Apply ACTIVE override data (v4.x) ONLY where explicitly defined
3) The resulting merged view is the canonical data for execution

Rules:
- Overrides may replace a tier only for verses/tier keys present in override files.
- All other tiers remain sourced from v3.9.
- Rules files may NOT modify text.

==================================================
5) PREVIEW GENERATION CONTRACT
==================================================
If execution proceeds:

- Engine MUST generate a PREVIEW artifact (registered state)
- Canvas: 4500 × 5400
- Guard margin: 50px
- Centering enforced (horizontal + vertical)
- Preview is NEVER production-ready

Preview registration MUST include:
- preview_id
- verse
- tier
- design
- version (render counter)
- renderer type
- timestamp

If preview cannot be registered:
→ OUTPUT INVALID — PREVIEW_NOT_REGISTERED

==================================================
6) DESIGN RANGE BEHAVIOR (LOCKED)
==================================================
- Designs 1–6: locked hierarchy, deterministic, no creative leakage
- Designs 7–10: creative freedom within defined constraints
- Renderer routing MUST follow the design range (see design_* rules)

==================================================
7) OUTPUT RULE
==================================================
- PREVIEW output must be produced as the first executable artifact.
- Production/export behavior is governed ONLY by approve_export_commands.md.
- No production output is permitted unless export trigger conditions are met.

==================================================
8) NO SIDE-EFFECTS (ABSOLUTE)
==================================================
The engine may NOT modify:
- master tables
- rules files
- templates
- engine index

Execution is read-only with respect to repository definitions.

==================================================
END RULES — EXECUTION ENGINE (CORE)
==================================================

