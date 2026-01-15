==================================================
ENGINE ERROR CODES — CANONICAL REFERENCE
VERSION: v4.6
FILE ROLE: EXECUTION TEMPLATE (ERROR CONTRACT)
==================================================

PURPOSE
• Defines ALL possible engine error outputs.
• Ensures errors are deterministic, machine-parseable, and auditable.
• Prevents vague, conversational, or inconsistent failures.
• Acts as the ONLY allowed error vocabulary.

If an error is not listed here, it MUST NOT be emitted.

--------------------------------------------------
ERROR FORMAT (LOCKED)
--------------------------------------------------

All errors MUST follow this format:

OUTPUT <SEVERITY> — <ERROR_CODE>

Where:
• SEVERITY ∈ { INVALID | ERROR | ENGINE_FAILURE }
• ERROR_CODE ∈ defined list below
• No free-form text allowed in execution responses

--------------------------------------------------
SEVERITY DEFINITIONS
--------------------------------------------------

INVALID
• User input or execution copy violation
• No engine fault
• No retry without correction

ERROR
• Recoverable execution failure
• Retry may succeed

ENGINE_FAILURE
• System violation
• Deterministic failure
• Requires engine fix, not user action

--------------------------------------------------
EXECUTION COPY ERRORS
--------------------------------------------------

OUTPUT INVALID — CONTEXT_OUT_OF_RANGE  
• EXECUTION CONTEXT is missing or not LIVE / ARCHIVE

OUTPUT INVALID — EXECUTION_NOT_INVOKED  
• EXECUTE keyword missing

OUTPUT INVALID — VERSION_UNSUPPORTED  
• Requested VERSION not recognized

OUTPUT INVALID — VERSE_OUT_OF_RANGE  
• Verse not between 1–30

OUTPUT INVALID — VERSE_NOT_FOUND  
• Verse missing from master data

OUTPUT INVALID — TIER_OUT_OF_RANGE  
• Tier not A–F

OUTPUT INVALID — TIER_NOT_AVAILABLE  
• Tier not defined for verse

OUTPUT INVALID — DESIGN_OUT_OF_RANGE  
• Design not between 1–10

--------------------------------------------------
DATA & VALIDATION ERRORS
--------------------------------------------------

OUTPUT INVALID — TIER_TEXT_MISMATCH  
• Canonical tier text mismatch detected

OUTPUT INVALID — MASTER_DATA_MISSING  
• Required data file not found

OUTPUT INVALID — DATA_VERSION_CONFLICT  
• Multiple active versions detected

--------------------------------------------------
DESIGN ENFORCEMENT ERRORS
--------------------------------------------------

OUTPUT INVALID — LOCKED_DESIGN_CHECKSUM_FAILED  
• Design 1–6 violated locked constraints

OUTPUT INVALID — RENDERER_LEAKAGE  
• Creative renderer used for locked design

OUTPUT INVALID — DESIGN_7_OVERREACH  
• Design 7 exceeded typography-first constraints

OUTPUT INVALID — DESIGN_8_UNDEREXPRESSION  
• Design 8 missing required motif integration

OUTPUT INVALID — DESIGN_COLLISION_DETECTED  
• Render satisfies multiple design rule sets

--------------------------------------------------
PREVIEW & EXECUTION ERRORS
--------------------------------------------------

OUTPUT INVALID — PREVIEW_NOT_REGISTERED  
• Preview failed to register in engine state

OUTPUT INVALID — PREVIEW_SUPPRESSED  
• Preview blocked despite valid execution

OUTPUT INVALID — EXECUTION_SUPPRESSED  
• Execution blocked in LIVE context

OUTPUT INVALID — APPROVE_WITHOUT_PREVIEW  
• Export attempted without preview

--------------------------------------------------
EXPORT / RUN Command1 ERRORS
--------------------------------------------------

OUTPUT INVALID — RUN_COMMAND1_FORMAT_INVALID  
• RUN Command1 malformed

OUTPUT INVALID — RUN_COMMAND1_PRECONDITION_FAILED  
• Preconditions not met

OUTPUT INVALID — POST_RUN_COMMAND1_MUTATION  
• Attempted mutation after export

--------------------------------------------------
HARD FAILURE CONDITIONS
--------------------------------------------------

ENGINE_FAILURE — EXECUTION_NOT_INVOKED  
• Valid execution copy did not execute

ENGINE_FAILURE — PREVIEW_SUPPRESSED  
• Preview not generated when required

ENGINE_FAILURE — RENDERER_LEAKAGE  
• Renderer isolation failed

ENGINE_FAILURE — RUN_COMMAND1_NOT_EXECUTED  
• Export command acknowledged without output

ENGINE_FAILURE — EXPORT_FUNCTION_MISSING  
• Export function not callable

ENGINE_FAILURE — PNG_EXPORT_FAILED  
• Export failed after valid command

--------------------------------------------------
DISALLOWED BEHAVIOR (ABSOLUTE)
--------------------------------------------------

The engine MUST NOT:
• Invent new error codes
• Return explanatory text during execution
• Ask questions during execution
• Return partial success messages
• Mix errors with previews or exports

--------------------------------------------------
FINAL AUTHORITY
--------------------------------------------------

This file is the SINGLE source of truth for:
• Error codes
• Failure semantics
• Execution diagnostics

All engines MUST conform.

--------------------------------------------------
END OF FILE
--------------------------------------------------
