==================================================
MASTER EXECUTION SYSTEM — APPROVAL & EXPORT COMMANDS
VERSION: v4.6
CHANGE TYPE: OVERRIDE + ADDITIVE (GLOBAL, HARD LOCK)
FILE ROLE: RULES / LOGIC (EXPORT & STATE TRANSITION)
==================================================

PURPOSE
• Defines the ONLY valid commands that transition the system
  from preview state to production output.
• Eliminates conversational ambiguity.
• Prevents silent acknowledge-without-output failures.
• Guarantees deterministic export behavior in every new chat.
• This file is REQUIRED for correct production execution.

SCOPE
• Applies to ALL EXECUTION COPY workflows.
• Applies to ALL designs (1–10), tiers (A–F), and verses (1–30).
• Evaluated AFTER execution context and preview registration.

--------------------------------------------------
1) COMMAND AUTHORITY MODEL (ABSOLUTE)
--------------------------------------------------
• Commands are NOT conversational.
• Commands are NOT confirmations.
• Commands are NOT UI actions.

A command:
• Triggers execution immediately
• Bypasses conversational flow
• Either produces output or fails loudly

If a command is acknowledged without execution →
ENGINE FAILURE — COMMAND_ACK_WITHOUT_EXECUTION

--------------------------------------------------
2) APPROVE COMMAND (LEGACY — SUPPORTED)
--------------------------------------------------
COMMAND:
APPROVE

STATUS:
• SUPPORTED for backward compatibility
• NOT the preferred export mechanism

BEHAVIOR:
• Case-insensitive
• May be issued multiple times
• Each APPROVE attempts export of most recent preview

LIMITATIONS:
• APPROVE may still be misinterpreted by UI layers
• APPROVE does NOT freeze creative state reliably

RECOMMENDATION:
• APPROVE is allowed
• RUN Command1 is preferred

--------------------------------------------------
3) RUN Command1 (CANONICAL EXPORT COMMAND)
--------------------------------------------------
COMMAND:
RUN Command1

• Case-insensitive
• Must be sent as a standalone message
• NO additional characters, punctuation, or text allowed

Examples (valid):
• RUN Command1
• run command1
• Run Command1

Any deviation →
OUTPUT INVALID — RUN_COMMAND1_FORMAT_INVALID

--------------------------------------------------
4) RUN Command1 — PRECONDITIONS (MANDATORY)
--------------------------------------------------
RUN Command1 is VALID only if ALL are true:

• EXECUTION CONTEXT = LIVE
• EXECUTE trigger was present in EXECUTION COPY
• A REGISTERED PREVIEW exists in current chat
• Preview corresponds to same verse / tier / design

If any condition fails →
OUTPUT INVALID — RUN_COMMAND1_PRECONDITION_FAILED

--------------------------------------------------
5) RUN Command1 — EXECUTION SEQUENCE (LOCKED)
--------------------------------------------------
Upon valid RUN Command1, the engine MUST perform
the following steps IN ORDER:

1) Resolve MOST RECENT REGISTERED PREVIEW
2) Freeze preview as FINAL_STATE
3) Disable ALL creative, preview, and interpretation logic
4) Invoke production renderer ONLY
5) Generate production output:
   • EXACTLY one (1) transparent PNG
   • Apparel-ready
   • Print-safe
   • No background
6) Save production file
7) Return production URL in the SAME response

No deviation is permitted.

--------------------------------------------------
6) OUTPUT REQUIREMENTS (ABSOLUTE)
--------------------------------------------------
• Production URL MUST be returned immediately
• No explanations
• No acknowledgements
• No follow-up messages

Failure →
ENGINE FAILURE — RUN_COMMAND1_NOT_EXECUTED

--------------------------------------------------
7) PREVIEW ≠ PRODUCTION (REINFORCED)
--------------------------------------------------
• PREVIEW artifacts are NEVER production-ready
• Production output is generated ONLY via:
  - RUN Command1
  - or APPROVE (legacy)

Any system that treats preview as production →
ENGINE FAILURE — PREVIEW_USED_AS_PRODUCTION

--------------------------------------------------
8) POST-EXPORT LOCK (HARD)
--------------------------------------------------
After successful RUN Command1:

• Creative logic is permanently disabled for this instance
• Preview artifacts may be pruned
• Reissuing RUN Command1:
  - Re-exports SAME frozen state only
• Any attempt to alter design →
OUTPUT INVALID — POST_EXPORT_MUTATION

--------------------------------------------------
9) EXPORT FAILURE HANDLING
--------------------------------------------------
If export fails:

• Engine MUST return a failure code
• MUST NOT retry silently
• MUST NOT acknowledge success

Failure codes include:
• RUN_COMMAND1_NOT_EXECUTED
• EXPORT_RENDER_FAILED
• EXPORT_WRITE_FAILED

--------------------------------------------------
10) BACKWARD COMPATIBILITY
--------------------------------------------------
• v3.9 APPROVE behavior remains supported
• v4.x systems SHOULD use RUN Command1
• No retroactive mutation of sealed versions

--------------------------------------------------
END OF FILE
--------------------------------------------------
