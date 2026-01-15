==================================================
ENGINE INDEX — MASTER ENTRY POINT
ENGINE: MASTER VERSE SYSTEM
VERSION: v4.6
STATUS: ACTIVE
==================================================

PURPOSE
• This file is the SINGLE authoritative entry point for the engine.
• All execution, validation, and exports MUST begin here.
• No other file may be referenced directly without being listed here.
• This file contains NO data and NO execution logic — references only.

==================================================
1) VERSION GOVERNANCE (LOCKED)
==================================================

• Versions are LINEAR.
• Only ONE ACTIVE version may exist at a time.

STATUS:
• v3.9 → SEALED / READ-ONLY
• v4.6 → ACTIVE / EVOLVING

SEALED RULE:
• SEALED versions may NOT receive:
  - fixes
  - overrides
  - extensions
• SEALED versions exist ONLY for audit and determinism.

==================================================
2) FILE VERSIONING RULE (LOCKED)
==================================================

• File names NEVER include version numbers.
• Versioning lives INSIDE each file header only.

✔ engine_index.md
✘ engine_index_v4.6.md

• When a file changes:
  - The file is REPLACED
  - Git history is the only record of change

==================================================
3) REPOSITORY ISOLATION (CRITICAL)
==================================================

• This engine lives in its OWN repository.
• Engines NEVER share:
  - data
  - rules
  - templates
  - execution logic

• No cross-engine imports are allowed.

==================================================
4) FOLDER ROLE GOVERNANCE (LOCKED)
==================================================

Each folder has ONE role and may NEVER absorb another.

• /data/      → canonical truth only (NO logic)
• /rules/     → execution + enforcement logic (NO data)
• /templates/ → execution copy formats + errors

If a file grows too large:
• SPLIT by role
• NEVER merge roles to reduce file count

==================================================
5) CANONICAL FILE MAP (LOCKED)
==================================================

ENTRY POINT
• ./engine_index.md

--------------------------------
MASTER DATA (CANONICAL TRUTH)
--------------------------------

BASELINE (SEALED):
• ./data/master_verse_table/v3_9/verses_01_10.md
• ./data/master_verse_table/v3_9/verses_11_20.md
• ./data/master_verse_table/v3_9/verses_21_30.md

ACTIVE OVERRIDES (ONLY IF PRESENT):
• ./data/master_verse_table/v4_0/verses_11_20.md

--------------------------------
RULES / LOGIC
--------------------------------

• ./rules/execution_engine.md
• ./rules/execution_context.md
• ./rules/execution_triggers.md
• ./rules/approve_export_commands.md
• ./rules/design_locked_01_06.md
• ./rules/design_creative_07_10.md
• ./rules/design_7_vs_8_separation.md
• ./rules/locked_design_checksum.md

--------------------------------
TEMPLATES
--------------------------------

• ./templates/execution_copy_template.md
• ./templates/error_codes.md

==================================================
6) LOAD ORDER & PRECEDENCE (LOCKED)
==================================================

ENGINE LOAD SEQUENCE (MANDATORY):

1) Read engine_index.md
2) Load v3.9 master data
3) Apply ACTIVE override data (v4.x), if present
4) Load rules
5) Load templates

PRECEDENCE RULES:
• Data overrides data only
• Rules NEVER override verse text
• Templates NEVER alter logic
• If no override exists → v3.9 remains canonical

==================================================
7) EXECUTION TRUST MODEL (ABSOLUTE)
==================================================

• Engine trusts ONLY files present in this repository.
• No conversational memory.
• No inferred context.
• No implied defaults.

If ANY referenced file is missing:
→ EXECUTION MUST FAIL — MISSING_CANONICAL_FILE

==================================================
8) CHANGE DISCIPLINE (LOCKED)
==================================================

Every file change MUST declare:
• VERSION
• CHANGE TYPE (ADDITIVE / OVERRIDE / EXTENSION)
• SCOPE (GLOBAL or TARGETED)

Unlabeled changes are INVALID.

==================================================
9) SCALE & SIZE SAFETY
==================================================

• If a data file exceeds practical copy/export limits:
  - Split into numbered siblings:
    e.g. MASTER_TABLE_01.md, MASTER_TABLE_02.md
• engine_index.md MUST reference ALL parts explicitly.

==================================================
10) FINAL AUTHORITY RULE
==================================================

• engine_index.md is the ONLY public entry point.
• If something is not listed here:
  → It does NOT exist to the engine.

==================================================
END ENGINE INDEX — MASTER ENTRY POINT
==================================================
