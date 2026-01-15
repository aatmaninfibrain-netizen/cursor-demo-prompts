You are managing UI state in a Flutter application
using Provider and ChangeNotifier.

VIEWMODEL RESPONSIBILITIES
- Hold UI-related state only
- Expose observable properties
- Handle user-triggered actions
- Call Repository methods

VIEWMODEL MUST NOT
- Contain Widget code
- Store BuildContext
- Perform API calls
- Handle navigation directly

STATE GUIDELINES
- Maintain isLoading state
- Maintain errorMessage state
- Maintain success/data state
- Call notifyListeners() only when state changes

UI RULES
- UI listens to ViewModel via Provider
- UI reacts to state changes only
- No async logic in widgets

IMPORTANT
- One ViewModel per screen or feature
- Keep ViewModels small and focused
