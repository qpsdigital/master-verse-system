==================================================
EXECUTION COPY — CANONICAL TEMPLATE
VERSION: v4.6
FILE ROLE: EXECUTION TEMPLATE (CONTRACT)
==================================================

PURPOSE
• Defines the ONLY valid execution format the engine will accept.
• Eliminates conversational ambiguity.
• Enforces deterministic PREVIEW → EXPORT flow.
• Acts as a strict contract, not guidance.

This template is REQUIRED for:
• ALL verse executions
• ALL designs (1–10)
• ALL tiers (A–F)
• ALL future chats

Deviation from this format → OUTPUT INVALID.

--------------------------------------------------
EXECUTION COPY — REQUIRED STRUCTURE
--------------------------------------------------

Every execution MUST follow this exact order:

1) EXECUTION COPY header
2) EXECUTION CONTEXT declaration
3) EXECUTE trigger
4) VERSION declaration (optional, defaults to v3.9)
5) VERSE declaration
6) TIER declaration
7) DESIGN declaration
8) END marker

--------------------------------------------------
CANONICAL EXECUTION COPY TEMPLATE
--------------------------------------------------

==============================
EXECUTION COPY
==============================

EXECUTION CONTEXT: LIVE

EXECUTE

VERSION: v4.6

VERSE: <INTEGER 1–30>

TIER: <A | B | C | D | E | F>

DESIGN: <INTEGER 1–10>

==============================
END EXECUTION COPY
==============================

--------------------------------------------------
FIELD DEFINITIONS (LOCKED)
--------------------------------------------------

EXECUTION CONTEXT
• REQUIRED
• Allowed values:
  - LIVE → execution required
  - ARCHIVE → reference only
• Case-insensitive
• Any other value → OUTPUT INVALID — CONTEXT_OUT_OF_RANGE

EXECUTE
• REQUIRED for execution
• Must appear on its own line
• Absence → non-executing reference block

VERSION
• Optional
• If omitted → defaults to v3.9 behavior
• v4.x enables advanced enforcement

VERSE
• Integer only
• Range: 1–30
• Must exist in Master Verse Table

TIER
• Allowed values: A, B, C, D, E, F
• Case-insensitive
• Must exist for verse

DESIGN
• Integer only
• Range: 1–10
• Determines locked vs creative logic

--------------------------------------------------
ENGINE BEHAVIOR (ABSOLUTE)
--------------------------------------------------

When a VALID execution copy is pasted:

• Engine MUST:
  - Validate verse range
  - Validate tier existence
  - Validate design range
  - Resolve canonical tier text from data files
  - Route to correct renderer
  - Generate PREVIEW
  - Register PREVIEW in state

Blocking execution is FORBIDDEN.

--------------------------------------------------
PREVIEW RULES
--------------------------------------------------
• PREVIEW is ALWAYS generated first
• PREVIEW is NEVER production-ready
• PREVIEW registers:
  - verse
  - tier
  - design
  - version
  - renderer
  - timestamp

--------------------------------------------------
EXPORT RULE (REFERENCE)
--------------------------------------------------
• Export is triggered ONLY by:
  RUN Command1
• Export freezes PREVIEW state
• Export returns EXACT PNG from preview

--------------------------------------------------
COMMON INVALID STATES
--------------------------------------------------
• Missing EXECUTE → NO EXECUTION
• Missing CONTEXT → OUTPUT INVALID
• Missing VERSE / TIER / DESIGN → OUTPUT INVALID
• Out-of-range values → OUTPUT INVALID
• Attempted creative logic on locked designs → OUTPUT INVALID

--------------------------------------------------
STRICTNESS NOTICE
--------------------------------------------------
This template is intentionally rigid.

Flexibility causes:
• execution drift
• renderer leakage
• export failure
• audit ambiguity

This file prevents all of the above.

--------------------------------------------------
END OF FILE
--------------------------------------------------
