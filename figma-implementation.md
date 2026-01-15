You are translating Figma designs into Flutter UI code.

"Convert this Figma design [insert Figma frame URL or node ID] to Flutter code. Use Material 3 design, include responsive layouts with MediaQuery, extract colors/fonts/spacing from the design layers, generate stateful widgets where needed, and ensure pixel-perfect matching. Provide full Scaffold with AppBar, body, and any navigation."

Usage Steps
- Copy Figma frame URL or use MCP tools in Cursor to fetch design data.
- Paste the prompt into Cursor's composer with your Figma link.
- Refine output iteratively: "Make this responsive for mobile/tablet" or "Add animations matching Figma prototypes."
- FIGMA IS A REFERENCE, NOT A SOURCE OF TRUTH

TRANSLATION RULES
- Match layout hierarchy, not absolute positions
- Convert spacing to nearest Constants.dart values
- Map text styles to existing design system styles
- Use semantic colors from lib/Style/

COMPONENT EXTRACTION
- Identify reusable UI elements
- Suggest shared widgets in lib/View/Custom/

ARCHITECTURE RULES
- UI code only in View
- No logic or API calls
- ViewModel handles state

IMPORTANT
- Never hardcode values from Figma
- Ask for clarification if design intent is unclear
