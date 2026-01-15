==================================================
ENGINE INDEX — MASTER ENTRY POINT
ENGINE: Master Verse System
VERSION: v4.6
STATUS: ACTIVE
==================================================

PURPOSE
- This file is the single authoritative entry point for the engine.
- All execution, validation, and export behavior begins here.
- This file contains NO verse data and NO procedural logic — references only.
- If something is not listed here, it does not exist to the engine.

==================================================
1) VERSION GOVERNANCE (LOCKED)
==================================================
- Versions are LINEAR (no branching).
- Only ONE ACTIVE version may exist at a time.

STATUS
- v3.9 → SEALED / READ-ONLY (historical baseline)
- v4.6 → ACTIVE / EVOLVING

SEALED RULE
- SEALED versions may NOT receive fixes, overrides, or extensions.
- SEALED versions exist only for audit + determinism.

==================================================
2) FILE VERSIONING & REPLACEMENT (LOCKED)
==================================================
- Filenames NEVER include version numbers.
- VERSIONING lives inside each file header only.
- When a file changes, you REPLACE the file (same path).
- Git history is the only record of prior versions.

VALID
- ENGINE_INDEX.md

INVALID
- ENGINE_INDEX_v4.6.md

==================================================
3) ENGINE ISOLATION (CRITICAL)
==================================================
- This engine lives in its OWN repository.
- Engines never share:
  - data
  - rules
  - templates
  - execution logic
- No cross-engine imports are allowed.

==================================================
4) FOLDER ROLES (LOCKED)
==================================================
- /data/      → canonical truth only (NO logic)
- /rules/     → enforcement + execution rules (NO verse data)
- /templates/ → execution copy formats + error catalog (NO logic)

If something grows too large:
- SPLIT within the same role
- NEVER merge roles to reduce file count

==================================================
5) CANONICAL FILE MAP (LOCKED)
==================================================

ENTRY POINT
- ./ENGINE_INDEX.md

--------------------------------
MASTER DATA (CANONICAL TRUTH)
--------------------------------
BASELINE (SEALED v3.9)
- ./data/master_verse_table/v3_9/verses_01_10.md
- ./data/master_verse_table/v3_9/verses_11_20.md
- ./data/master_verse_table/v3_9/verses_21_30.md

ACTIVE OVERRIDES (v4.x) — ONLY IF PRESENT
- ./data/master_verse_table/v4_0/verses_11_20.md

--------------------------------
RULES / LOGIC (ENFORCEMENT)
--------------------------------
- ./rules/execution_engine.md
- ./rules/execution_context.md
- ./rules/execution_triggers.md
- ./rules/approve_export_commands.md
- ./rules/design_locked_01_06.md
- ./rules/design_creative_07_10.md
- ./rules/design_7_vs_8_separation.md
- ./rules/locked_design_checksum.md

--------------------------------
TEMPLATES (OUTPUT CONTRACTS)
--------------------------------
- ./templates/execution_copy_template.md
- ./templates/error_codes.md

==================================================
6) LOAD ORDER & PRECEDENCE (LOCKED)
==================================================
ENGINE LOAD SEQUENCE (MANDATORY)
1) Read ENGINE_INDEX.md
2) Load v3.9 master data (sealed baseline)
3) Apply active override data (v4.x), IF present
4) Load rules
5) Load templates

PRECEDENCE RULES
- Data overrides data only (v4.x may override v3.9 data where explicitly defined).
- Rules NEVER override verse text.
- Templates NEVER alter logic.
- If no override exists, v3.9 remains canonical.

==================================================
7) EXECUTION TRUST MODEL (ABSOLUTE)
==================================================
- Engine trusts ONLY files present in this repository.
- No conversational memory.
- No inferred context.
- No implied defaults.

If ANY referenced file is missing:
→ EXECUTION MUST FAIL — MISSING_CANONICAL_FILE

==================================================
8) CHANGE DISCIPLINE (LOCKED)
==================================================
Every file change MUST declare:
- VERSION
- CHANGE TYPE (ADDITIVE / OVERRIDE / EXTENSION)
- SCOPE (GLOBAL or TARGETED)

Unlabeled changes are INVALID.

==================================================
9) SCALE & SIZE SAFETY
==================================================
If a data file exceeds practical copy/export limits:
- Split into numbered siblings, e.g.:
  ./data/master_verse_table/v3_9/verses_01_10__part_1.md
  ./data/master_verse_table/v3_9/verses_01_10__part_2.md
- ENGINE_INDEX.md must reference ALL parts explicitly.

==================================================
10) FINAL AUTHORITY RULE
==================================================
- ENGINE_INDEX.md is the only public entry point.
- If it’s not listed here, it does not exist to the engine.

==================================================
END ENGINE INDEX — MASTER ENTRY POINT
==================================================
