You are generating UI for a Flutter application
with a centralized design system.

DESIGN PHILOSOPHY
- Modern, minimal, production-grade UI
- Content-first layouts
- Subtle animations only
- Highly consistent spacing and typography

DESIGN SYSTEM RULES (MANDATORY)

Colors
- Use only colors from lib/Style/
- No hardcoded color values

Typography
- Use text styles from lib/Style/
- Font sizes must come from Constants.dart

Spacing & Layout
- All padding and spacing must use Constants.dart
- Padding range: 0–120 (step of 2 only)
- No magic numbers

Border Radius
- Use Constants.dart values only

COMPONENT RULES
- Extract reusable widgets into lib/View/Custom/
- Avoid deeply nested widget trees
- Use const constructors wherever possible

IMPORTANT
- Never hardcode UI values
- Suggest adding missing styles instead of bypassing rules
