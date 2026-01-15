==================================================
MASTER EXECUTION SYSTEM — DESIGN 7 vs DESIGN 8 SEPARATION
VERSION: v4.6
CHANGE TYPE: OVERRIDE (CREATIVE DISAMBIGUATION)
FILE ROLE: RULES / LOGIC (DESIGN DIFFERENTIATION)
==================================================

PURPOSE
• Permanently prevents visual and conceptual overlap between Design 7 and Design 8.
• Enforces clear creative intent per design number.
• Eliminates renderer ambiguity and accidental duplication.
• Guarantees that each design produces DISTINCT visual outcomes.

SCOPE
• Applies ONLY to:
  DESIGN 7 and DESIGN 8
• Applies to ALL verses (1–30) and tiers (A–F).
• Evaluated AFTER general creative rules (Designs 7–10).

--------------------------------------------------
1) DESIGN IDENTITY (LOCKED)
--------------------------------------------------

DESIGN 7 — TYPE-FIRST EXPRESSION
• Primary identity: TYPOGRAPHY
• Message clarity is the sole priority
• Motifs are secondary or optional

DESIGN 8 — MOTIF-INTEGRATED COMPOSITION
• Primary identity: SYMBOL + TEXT
• Motif is structural, not decorative
• Text and motif are visually inseparable

--------------------------------------------------
2) DESIGN 7 — HARD CONSTRAINTS (ABSOLUTE)
--------------------------------------------------
When DESIGN = 7, ALL of the following MUST be true:

✔ Typography occupies ≥ 70% of visual dominance  
✔ Text remains readable with motif removed  
✔ Motifs (if used):
  - Must be SMALL
  - Must be ACCENT-ONLY
  - Must NOT frame, contain, or intersect text  
✔ Layout is text-driven, not image-driven  
✔ No graffiti, spray, or chaotic effects  
✔ No expressive background textures  

If ANY condition fails →
OUTPUT INVALID — DESIGN_7_RULE_VIOLATION

--------------------------------------------------
3) DESIGN 8 — HARD CONSTRAINTS (ABSOLUTE)
--------------------------------------------------
When DESIGN = 8, ALL of the following MUST be true:

✔ ONE symbolic motif is REQUIRED  
✔ Motif MUST:
  - Frame, anchor, intersect, or contain text
  - Be structurally necessary to composition  
✔ Typography may adapt to motif shape or flow  
✔ Motif and text share dominance (~50/50)  
✔ Controlled texture allowed ONLY inside motif  

If ANY condition fails →
OUTPUT INVALID — DESIGN_8_RULE_VIOLATION

--------------------------------------------------
4) MUTUAL EXCLUSION RULE (CRITICAL)
--------------------------------------------------
• A render MUST satisfy ONLY ONE of the two rule sets.
• If a render satisfies BOTH:
  → ENGINE FAILURE — DESIGN_COLLISION_DETECTED

• If a render satisfies NEITHER:
  → OUTPUT INVALID — DESIGN_IDENTITY_UNCLEAR

--------------------------------------------------
5) RENDERER ROUTING (LOCKED)
--------------------------------------------------
The engine MUST route renderers as follows:

• DESIGN 7 →
  TYPE_PRIMARY_RENDERER

• DESIGN 8 →
  MOTIF_PRIMARY_RENDERER

Renderer crossover is STRICTLY FORBIDDEN.

Failure →
ENGINE FAILURE — RENDERER_ROUTING_VIOLATION

--------------------------------------------------
6) PREVIEW VALIDITY RULE
--------------------------------------------------
A PREVIEW is considered VALID ONLY IF:

• Design identity is visually obvious
• Rule set for the design number is fully satisfied
• No fallback or hybrid behavior is present

Invalid previews MUST NOT be shown.

--------------------------------------------------
7) EXPORT SAFETY
--------------------------------------------------
• Only previews that pass this separation rule
  may be exported via RUN Command1
• Export freezes identity permanently
• Any mutation after export →
  OUTPUT INVALID — POST_EXPORT_MUTATION

--------------------------------------------------
8) BACKWARD COMPATIBILITY
--------------------------------------------------
• v3.9 outputs remain historically valid
• v4.x executions MUST enforce this separation
• No impact to Designs 1–6 or 9–10

--------------------------------------------------
END OF FILE
--------------------------------------------------
