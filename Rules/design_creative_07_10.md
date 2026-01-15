==================================================
MASTER EXECUTION SYSTEM — CREATIVE DESIGNS 7–10
VERSION: v4.6
CHANGE TYPE: RULES (CREATIVE GOVERNANCE)
FILE ROLE: RULES / LOGIC (CREATIVE RANGE)
==================================================

PURPOSE
• Defines controlled creative freedom for Designs 7–10.
• Enables expressive layouts while preserving tier integrity.
• Ensures creativity is intentional, bounded, and repeatable.
• Explicitly separates creative logic from locked designs (1–6).

SCOPE
• Applies ONLY to:
  DESIGN 7, DESIGN 8, DESIGN 9, DESIGN 10
• Applies to ALL verses (1–30) and tiers (A–F).
• Evaluated AFTER execution context and tier validation.

--------------------------------------------------
1) CREATIVE DESIGN SET
--------------------------------------------------
The following designs are CREATIVE:

• DESIGN 7
• DESIGN 8
• DESIGN 9
• DESIGN 10

Creative means:
• Visual interpretation is allowed
• Layout variation is allowed
• Stylistic expression is allowed
• BUT tier text remains IMMUTABLE

--------------------------------------------------
2) GLOBAL CREATIVE CONSTRAINTS (LOCKED)
--------------------------------------------------
For Designs 7–10, ALL of the following MUST be true:

✔ Tier text is pulled verbatim from Master Table  
✔ No words added, removed, or paraphrased  
✔ Verse reference formatting preserved  
✔ High apparel legibility maintained  
✔ Composition remains chest-ready  
✔ Canvas: 4500 × 5400 px  
✔ 50px internal guard margin enforced  

Violation →
OUTPUT INVALID — TIER_INTEGRITY_VIOLATION

--------------------------------------------------
3) ALLOWED CREATIVE ELEMENTS
--------------------------------------------------
The following MAY be used intentionally:

TYPOGRAPHY
• Multiple fonts
• Variable weights and sizes
• Script, serif, sans, brush styles
• Dominant + secondary hierarchy
• Curved, angled, stacked text (creative designs only)

MOTIFS (OPTIONAL, DESIGN-DEPENDENT)
• Crosses
• Crowns
• Books
• Hearts
• Mountains
• Footprints
• Rays / light elements

TEXTURE & EFFECTS
• Subtle distressing
• Controlled grain
• Brush strokes
• Shadows, glow, highlights
• Texture may exist ONLY where intentional

--------------------------------------------------
4) DISALLOWED BEHAVIOR (GLOBAL)
--------------------------------------------------
The following are NEVER allowed:

• Altering tier text content
• Adding scripture words not in the tier
• Obscuring readability
• Overcrowding or visual clutter
• Bleeding beyond guard margin
• Using locked-design renderers

Violation →
OUTPUT INVALID — CREATIVE_OVERREACH

--------------------------------------------------
5) DESIGN-SPECIFIC INTENT (SUMMARY)
--------------------------------------------------

DESIGN 7 — TYPE-PRIMARY
• Typography is the hero
• Motifs (if present) are SMALL and ACCENT-ONLY
• Text must read clearly without motif support

DESIGN 8 — MOTIF-INTEGRATED
• A single symbolic motif is REQUIRED
• Motif and text are visually interdependent
• Motif may frame, anchor, or intersect text

DESIGN 9 — EXPRESSIVE COMPOSITION
• Balanced use of text, motif, and texture
• Clear hierarchy but expressive layout
• Strong emotional or stylistic tone allowed

DESIGN 10 — MAXIMAL CREATIVE
• Highest creative freedom
• Complex compositions allowed
• Still must maintain tier legibility
• Cannot violate apparel readability rules

--------------------------------------------------
6) RENDERER ROUTING (MANDATORY)
--------------------------------------------------
When DESIGN ∈ {7–10}:

• Engine MUST route execution to:
  CREATIVE_RENDERER_ONLY

• Locked renderer usage is FORBIDDEN

Failure →
ENGINE FAILURE — RENDERER_MISROUTED

--------------------------------------------------
7) PREVIEW ACCEPTANCE RULE
--------------------------------------------------
A PREVIEW for Designs 7–10 is VALID ONLY IF:

• Tier text integrity is preserved
• Guard margins are respected
• Design intent matches the selected design number
• No locked-design rules are violated

--------------------------------------------------
8) EXPORT SAFETY
--------------------------------------------------
• Creative previews may ONLY be exported
  via RUN Command1
• Export freezes the most recent preview
• No mutation allowed post-export

--------------------------------------------------
9) BACKWARD COMPATIBILITY
--------------------------------------------------
• v3.9 outputs remain historically valid
• v4.x executions MUST enforce this file
• No impact to Designs 1–6

--------------------------------------------------
END OF FILE
--------------------------------------------------
