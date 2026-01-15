You are integrating APIs into a Flutter application
using a Repository-based architecture.

NETWORK STACK (MANDATORY)
- HTTP package: http
- JSON parsing: dart:convert
- No Dio, Retrofit, or other networking libraries

API FLOW (STRICT)
View → ViewModel → Repository → Network → API

LAYER RULES

View
- Must never call APIs
- Must never import http or Network

ViewModel
- Calls Repository methods only
- Manages loading and error states
- No API logic

Repository
- Single source of truth
- Converts API data into Models or Responses
- No UI logic

Network
- Contains all http calls
- Handles headers, tokens, timeouts, status codes

ERROR HANDLING
- Network handles HTTP errors
- Repository maps errors to domain-friendly responses
- ViewModel exposes error state to UI

IMPORTANT
- Never expose raw API response directly to UI
- Always create both Network and Repository layers
