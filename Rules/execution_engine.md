==================================================
MASTER EXECUTION SYSTEM — EXECUTION ENGINE (CANONICAL)
VERSION: v4.6
CHANGE TYPE: ADDITIVE + OVERRIDE (CONSOLIDATED)
FILE ROLE: RULES / LOGIC (ENGINE CORE)
==================================================

PURPOSE
• Defines the canonical execution engine behavior for the Master Verse System.
• Governs how EXECUTION COPY blocks are interpreted, validated, and executed.
• Enforces deterministic workflow:
  EXECUTION COPY → PREVIEW (REGISTERED) → EXPORT (RUN Command1) → PRODUCTION URL
• Engine is READ-ONLY to master data; it never mutates source tables.

SCOPE
• Applies to ALL verses, tiers, and designs unless explicitly overridden elsewhere.
• Uses Master Table v3.9 as baseline plus any active v4.x overrides referenced by ENGINE_INDEX.

--------------------------------------------------
0) DEFINITIONS
--------------------------------------------------
• "Engine": the logic that parses commands, validates inputs, registers previews, and exports production.
• "Master Data": verse/tier text files (data-only) referenced by ENGINE_INDEX.
• "EXECUTION COPY": a portable command block pasted by the user.
• "PREVIEW": a render artifact for visual validation, not production-ready.
• "REGISTERED PREVIEW": a preview stored in engine state with an ID and metadata.
• "PRODUCTION": the export artifact generated from the most recent registered preview.

--------------------------------------------------
1) INPUTS & VALIDATION (HARD LOCKED)
--------------------------------------------------
1.1 VERSE RANGE
• VERSE must be integer 1–30.
• If out of range → OUTPUT INVALID — VERSE_OUT_OF_RANGE.

1.2 TIER RANGE
• TIER must be one of A, B, C, D, E, F.
• Case-insensitive accepted.
• If invalid → OUTPUT INVALID — TIER_OUT_OF_RANGE.

1.3 DESIGN RANGE
• DESIGN must be integer 1–10.
• If invalid → OUTPUT INVALID — DESIGN_OUT_OF_RANGE.

1.4 MASTER TABLE PRESENCE
• Engine must resolve verse + tier from active master data set.
• If verse/tier not available (including intentionally omitted tiers) →
  OUTPUT INVALID — TIER_NOT_AVAILABLE.

--------------------------------------------------
2) SOURCE OF TRUTH & OVERRIDES (HARD LOCKED)
--------------------------------------------------
2.1 BASELINE
• Master Table v3.9 is the historical baseline.

2.2 ACTIVE DATA RESOLUTION
• The engine resolves active canonical text using ENGINE_INDEX references:
  - v3.9 files for all verses by default
  - Any v4.x data override files supersede v3.9 only for their declared scope

2.3 READ-ONLY RULE
• Engine MUST NOT modify any master data files.
• Any attempt to rewrite data → ENGINE FAILURE — DATA_MUTATION_FORBIDDEN.

--------------------------------------------------
3) EXECUTION COPY PARSING (COMMAND MODEL)
--------------------------------------------------
3.1 EXECUTION COPY = COMMAND
• Any block labeled "EXECUTION COPY" is interpreted as a command contract.
• Conversational interpretation is forbidden.

3.2 REQUIRED HEADER FIELDS
An EXECUTION COPY block MUST declare:
• VERSE: <1–30>
• TIER: <A–F>
• DESIGN: <1–10>

3.3 EXECUTION CONTEXT (See rules/execution_context.md)
• Context must be declared as LIVE or ARCHIVE.
• LIVE permits execution; ARCHIVE forbids execution.

3.4 EXECUTE TRIGGER (MANDATORY FOR RUN)
• To force immediate preview generation, EXECUTION COPY must include:
  EXECUTE
(on its own line, immediately after EXECUTION CONTEXT).
• If EXECUTE missing:
  - Engine may treat as declarative/reference
  - Preview generation is NOT required

--------------------------------------------------
4) TIER VALIDATION (HARD LOCKED)
--------------------------------------------------
4.1 CANONICAL PULL
• Engine pulls tier text verbatim from resolved master data.
• Tier text is immutable in output formatting (no paraphrase, no reorder).

4.2 USER-SUPPLIED TEXT (OPTIONAL)
• If user provides tier text, engine compares it to canonical.
• If mismatch:
  - Engine MUST ignore user text
  - Engine MUST use canonical text
  - Engine MUST log mismatch internally
  - Output remains valid (unless policy elsewhere says reject mismatch)

4.3 MISMATCH HARD FAIL (OPTIONAL STRICT MODE)
• If strict mode is enabled by ENGINE_INDEX, mismatch →
  OUTPUT INVALID — TIER_TEXT_MISMATCH.
(If strict mode not enabled, mismatch is corrected by canonical substitution.)

--------------------------------------------------
5) PREVIEW GENERATION & REGISTRATION (STATEFUL)
--------------------------------------------------
5.1 PREVIEW REQUIREMENT
If and only if:
• EXECUTION CONTEXT = LIVE
• AND EXECUTE trigger present
Then:
• Engine MUST generate a preview artifact.

5.2 PREVIEW CANVAS
• Canvas: 4500 × 5400 px
• Guard margin: 50px
• Centering: horizontal + vertical enforced

5.3 INTERNAL DESIGN COMMENT
• Internal comment is mandatory:
  "Keep modern and manly."
• If missing in block, engine inserts it automatically.

5.4 PREVIEW FILENAME
• Preview filename pattern:
  verse<ordinal>__<VerseRef>__tier_<A–F>__design_<01–10>__v<render#>__PREVIEW.png

5.5 REGISTERED PREVIEW (MANDATORY)
• Every preview MUST be registered in engine state as:
  PREVIEW_ID: unique id
  verse, tier, design
  render_version (v#)
  renderer_type
  timestamp

If preview cannot be registered →
OUTPUT INVALID — PREVIEW_NOT_REGISTERED.

5.6 PREVIEW IS NOT PRODUCTION
• Preview files are NEVER production-ready.
• Production requires export command (RUN Command1).

--------------------------------------------------
6) DESIGN ROUTING (LOCKED vs CREATIVE)
--------------------------------------------------
6.1 DESIGN GROUPS
• Locked designs: 1–6
• Creative designs: 7–10

6.2 RENDERER ROUTING
• If design ∈ {1–6}:
  - Engine MUST use LOCKED_RENDERER_ONLY
  - Creative/generative renderers forbidden
• If design ∈ {7–10}:
  - Engine uses CREATIVE_RENDERER (as defined in creative rules files)

6.3 LOCKED DESIGN CHECKSUM
• For designs 1–6:
  - Engine MUST run LOCKED DESIGN CHECKSUM before accepting preview
  - If checksum fails → OUTPUT INVALID — LOCKED_DESIGN_CHECKSUM_FAILED

(Checksum definition is in rules/locked_design_checksum.md)

--------------------------------------------------
7) EXPORT / PRODUCTION (SEE approve_export_commands.md)
--------------------------------------------------
7.1 EXPORT COMMAND
• The canonical export command is:
  RUN Command1
• "PNG" is deprecated and invalid (handled in export rules).

7.2 EXPORT FROM MOST RECENT REGISTERED PREVIEW
• Export always uses the most recent registered preview for that verse/tier/design in current chat state.

7.3 NO POST-EXPORT MUTATION
• After export freeze:
  - No creative re-entry
  - No layout changes
  - No style changes
• Re-export permitted only if it exports the same frozen state.

--------------------------------------------------
8) CHAT STATE ISOLATION (HARD LOCKED)
--------------------------------------------------
• Preview/production state is scoped to the current chat only.
• Engine must not assume state from another chat.
• If export requested without local registered preview →
  OUTPUT INVALID — EXPORT_WITHOUT_PREVIEW.

--------------------------------------------------
9) FAILURE CLASSIFICATION (HARD LOCKED)
--------------------------------------------------
• If LIVE + EXECUTE present and preview not produced →
  ENGINE FAILURE — PREVIEW_SUPPRESSED.
• If export command received and no production URL returned in same response →
  ENGINE FAILURE — EXPORT_NOT_EXECUTED.

--------------------------------------------------
END OF FILE
--------------------------------------------------
