==================================================
MASTER EXECUTION SYSTEM — EXECUTION CONTEXT
VERSION: v4.6
CHANGE TYPE: ADDITIVE (GLOBAL, HARD LOCK)
FILE ROLE: RULES / LOGIC (CONTEXT & EXECUTION ELIGIBILITY)
==================================================

PURPOSE
• Explicitly declares whether an EXECUTION COPY block is allowed to execute.
• Removes all inference from conversational history, chat state, or AI discretion.
• Prevents silent or defensive non-execution.
• Guarantees deterministic behavior across new chats, long chats, and exports.
• This file is REQUIRED for correct engine operation.

SCOPE
• Applies to ALL EXECUTION COPY blocks.
• Applies to ALL designs (1–10), tiers (A–F), and verses (1–30).
• Interpreted BEFORE any preview or export logic.

--------------------------------------------------
1) EXECUTION CONTEXT HEADER (MANDATORY)
--------------------------------------------------
Every EXECUTION COPY block MUST declare an execution context.

Required line (case-insensitive):

EXECUTION CONTEXT: <VALUE>

• This line MUST appear:
  - Immediately after the EXECUTION COPY header
  - Before VERSE / TIER / DESIGN declarations
• If missing:
  - Engine MUST NOT assume intent
  - Engine MAY default to non-executing behavior
  - Export commands MUST fail

--------------------------------------------------
2) ALLOWED CONTEXT VALUES (HARD LOCKED)
--------------------------------------------------
Only the following values are permitted:

• LIVE
• ARCHIVE

Values are case-insensitive.

Any other value →
OUTPUT INVALID — CONTEXT_OUT_OF_RANGE

--------------------------------------------------
3) CONTEXT BEHAVIOR (ABSOLUTE)
--------------------------------------------------

3.1 EXECUTION CONTEXT = LIVE
--------------------------------
When context is LIVE:

• Execution is PERMITTED
• Engine MUST honor execution triggers (EXECUTE)
• Engine MUST generate PREVIEW when EXECUTE is present
• Engine MUST allow export commands (RUN Command1) if preconditions are met
• Engine MUST NOT rely on chat history or inference
• Blocking execution is FORBIDDEN

Failure to execute under LIVE + EXECUTE →
ENGINE FAILURE — EXECUTION_SUPPRESSED

--------------------------------
3.2 EXECUTION CONTEXT = ARCHIVE
--------------------------------
When context is ARCHIVE:

• Execution is FORBIDDEN
• PREVIEW generation MUST NOT occur
• Export commands MUST fail
• Content is treated as reference / backup only
• No state may be registered

If execution occurs under ARCHIVE →
ENGINE FAILURE — ARCHIVE_CONTEXT_VIOLATION

--------------------------------------------------
4) CONTEXT + EXECUTE INTERACTION (LOCKED)
--------------------------------------------------
Execution Context and EXECUTE trigger interact as follows:

| CONTEXT | EXECUTE PRESENT | RESULT |
|--------|------------------|--------|
| LIVE   | YES              | PREVIEW REQUIRED |
| LIVE   | NO               | Declarative / Reference |
| ARCHIVE | YES             | INVALID (EXECUTION BLOCKED) |
| ARCHIVE | NO              | Reference Only |

• EXECUTE without LIVE →
OUTPUT INVALID — EXECUTE_IN_ARCHIVE_CONTEXT

--------------------------------------------------
5) CONTEXT PRECEDENCE RULE (HARD LOCKED)
--------------------------------------------------
• EXECUTION CONTEXT ALWAYS overrides:
  - Conversational flow
  - Chat memory
  - Prior messages
  - UI affordances

• The engine MUST NOT infer intent.
• The engine MUST NOT “helpfully” execute without LIVE.
• The engine MUST NOT “helpfully” block execution when LIVE is declared.

--------------------------------------------------
6) EXPORT SAFETY BINDING
--------------------------------------------------
• RUN Command1 is VALID ONLY when:
  - EXECUTION CONTEXT = LIVE
  - A registered preview exists

• If RUN Command1 is issued under ARCHIVE →
OUTPUT INVALID — EXPORT_IN_ARCHIVE_CONTEXT

--------------------------------------------------
7) BACKWARD COMPATIBILITY
--------------------------------------------------
• v3.9 EXECUTION COPY blocks without EXECUTION CONTEXT remain valid,
  but execution MAY be defensive.
• v4.x blocks WITH EXECUTION CONTEXT = LIVE remove all ambiguity.
• No retroactive changes to v3.9 behavior.

--------------------------------------------------
8) FAILURE CLASSIFICATION (LOCKED)
--------------------------------------------------
• LIVE + EXECUTE and no preview →
ENGINE FAILURE — CONTEXT_LIVE_EXECUTION_BLOCKED

• ARCHIVE and any execution →
ENGINE FAILURE — CONTEXT_ARCHIVE_EXECUTED

--------------------------------------------------
END OF FILE
--------------------------------------------------
