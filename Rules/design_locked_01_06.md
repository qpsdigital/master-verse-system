==================================================
MASTER EXECUTION SYSTEM — LOCKED DESIGNS 1–6
VERSION: v4.6
CHANGE TYPE: HARD LOCK (NON-NEGOTIABLE)
FILE ROLE: RULES / LOGIC (LOCKED DESIGN GOVERNANCE)
==================================================

PURPOSE
• Defines deterministic, non-creative behavior for Designs 1–6.
• Prevents creative or generative leakage.
• Guarantees predictable, repeatable, chest-ready outputs.
• Ensures locked designs remain visually consistent regardless of renderer.
• This file is REQUIRED for execution correctness.

SCOPE
• Applies ONLY to:
  DESIGN 1, DESIGN 2, DESIGN 3, DESIGN 4, DESIGN 5, DESIGN 6
• Applies to ALL verses (1–30) and tiers (A–F).
• Evaluated BEFORE preview is accepted.

--------------------------------------------------
1) LOCKED DESIGN SET (ABSOLUTE)
--------------------------------------------------
The following designs are LOCKED:

• DESIGN 1
• DESIGN 2
• DESIGN 3
• DESIGN 4
• DESIGN 5
• DESIGN 6

Locked means:
• No creative interpretation
• No stylistic variance
• No expressive freedom
• No generative behavior

--------------------------------------------------
2) ALLOWED VISUAL CHARACTERISTICS (LOCKED)
--------------------------------------------------
For Designs 1–6, ALL of the following MUST be true:

✔ Single dominant typographic hierarchy  
✔ Clean, vector-only typography  
✔ Flat color only (no gradients)  
✔ No texture of any kind  
✔ No background elements  
✔ No atmospheric or generative effects  
✔ High legibility at chest distance  
✔ Predictable, centered layout  
✔ Apparel-first composition  

--------------------------------------------------
3) DISALLOWED FEATURES (ABSOLUTE)
--------------------------------------------------
If ANY of the following are detected, execution MUST FAIL:

• Texture (grain, noise, dust, distress, brush, splatter)
• Glow, shadow, blur, bevel, emboss
• Gradients or color blends
• Background shapes, frames, or atmospherics
• Multiple competing focal points
• Expressive typography
• Graffiti, hand-drawn, or chaotic styling
• Creative motifs of any kind
• Renderer behaviors intended for Designs 7–10

Violation →
OUTPUT INVALID — LOCKED_DESIGN_VIOLATION

--------------------------------------------------
4) RENDERER ISOLATION (MANDATORY)
--------------------------------------------------
When DESIGN ∈ {1–6}:

• Engine MUST route execution to:
  LOCKED_RENDERER_ONLY

• Creative or generative renderers are FORBIDDEN
• Renderer crossover is FORBIDDEN

Failure →
ENGINE FAILURE — RENDERER_LEAKAGE

--------------------------------------------------
5) LOCKED DESIGN CHECKSUM (MANDATORY)
--------------------------------------------------
Before a PREVIEW is accepted, the engine MUST compute
a LOCKED DESIGN CHECKSUM.

The checksum validates:

✔ No disallowed features present  
✔ Typography-only composition  
✔ Deterministic layout structure  
✔ Renderer isolation enforced  

If checksum FAILS:

• PREVIEW MUST NOT be shown
• PRODUCTION MUST NOT be allowed
• Engine MUST abort execution

Failure →
OUTPUT INVALID — LOCKED_DESIGN_CHECKSUM_FAILED

--------------------------------------------------
6) PREVIEW VALIDITY RULE
--------------------------------------------------
A PREVIEW for Designs 1–6 is VALID ONLY IF:

• Locked design checksum PASSES
• Layout conforms to locked hierarchy definition

A preview that “looks fine” but violates rules
is INVALID and must NOT be displayed.

--------------------------------------------------
7) PRODUCTION SAFETY
--------------------------------------------------
• Production export is allowed ONLY if:
  - A valid locked-design preview exists
• Any attempt to export an invalid preview →
OUTPUT INVALID — INVALID_PREVIEW_EXPORT

--------------------------------------------------
8) BACKWARD COMPATIBILITY
--------------------------------------------------
• v3.9 historical outputs remain valid
• v4.x executions MUST enforce this file
• No exceptions or overrides allowed

--------------------------------------------------
END OF FILE
--------------------------------------------------
