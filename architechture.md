# Flutter App Architecture

This project follows a **layered MVVM-inspired architecture** with strict separation of concerns.
The structure is designed for scalability, maintainability, and clarity for both developers and AI tools (Cursor).

---

## Project Structure

``` 
lib/
├── Helper/
├── Lang/
├── LocalDB/
├── Localization/
├── Model/
├── Network/
├── Repository/
├── Response/
├── Style/
├── Utils/
├── View/
│ ├── BottomNavigation/
│ │ ├── BottomNavigationBar.dart
│ │ ├── BottomNavigationViewModel.dart
│ ├── BottomScreen/
│ ├── Settings/
│ ├── Splash/
├── main.dart
```
yaml
Copy code

---

## Architectural Layers

### View (`lib/View/`)
**Responsibility**
- UI rendering
- User interaction
- Widget composition

**Rules**
- No API calls
- No database access
- No business logic
- Reads state from ViewModel only

Each feature lives in its own folder.

---

### ViewModel (inside feature folders)
**Responsibility**
- UI state management
- Handles user actions
- Calls Repository methods
- Exposes observable state (Provider / ChangeNotifier)

**Rules**
- No Widget code
- No direct API calls
- No BuildContext storage

**Example**
BottomNavigationBar.dart
BottomNavigationBarViewModel.dart

yaml
Copy code

---

### Repository (`lib/Repository/`)
**Responsibility**
- Single source of truth for data
- Decides data source (API, cache, local DB)

**Rules**
- No UI imports
- Calls Network and LocalDB
- Returns Models or Responses

**Flow**
View → ViewModel → Repository → Network / LocalDB

yaml
Copy code

---

### Network (`lib/Network/`)
**Responsibility**
- API communication
- HTTP clients
- Request/response mapping

**Rules**
- No UI logic
- No ViewModel imports
- No state management

---

### Model (`lib/Model/`)
**Responsibility**
- Domain entities

**Rules**
- Pure Dart classes
- Serializable (toJson / fromJson)
- No Flutter imports

---

### Response (`lib/Response/`)
**Responsibility**
- API response wrappers
- Pagination
- Status + metadata handling

Used to decouple API response shape from domain models.

---

### LocalDB (`lib/LocalDB/`)
**Responsibility**
- Local persistence (SQLite, Hive)

**Rules**
- No UI access
- Accessed only via Repository

---

### Localization (`lib/Lang/`, `lib/Localization/`)
**Responsibility**
- Language keys
- Translations
- Locale management

---

### Style (`lib/Style/`)
**Responsibility**
- Design system

**Includes**
- Colors
- Text styles
- Spacing
- Themes

**Rule**
- No hardcoded styles in UI

---

### Utils (`lib/Utils/`)
**Responsibility**
- Generic reusable helpers

**Examples**
- Date formatting
- Validators
- Extensions
- Debouncers
- Shared Preference Helper Class
- Firebase Helper Class etc

**NOTE**
- This folder will always contain a Constants.dart file.
- Content of the Constants.dat
* padding - From 0 to 120 in 2's multiplication
* fontsize - From 0 to 36 in 2's multiplication
* borderRadius - From 0 to 50 in 2's multiplication


No business logic allowed.

---

### Helper (`lib/Helper/`)
**Responsibility**
- App-level helpers

**Examples**
- Navigation helper
- Asset helper
- Dialog / Snackbar helper

More opinionated than Utils.

---

## Entry Point

### `main.dart`
**Responsibilities**
- App initialization
- Dependency injection
- Provider setup
- Theme & localization config
- Initial route (Splash)

No business logic allowed.

---

## Dependency Rules (Strict)

### Allowed
View → ViewModel → Repository → Network / LocalDB
Repository → Model / Response

shell
Copy code

### Not Allowed
View → Network
View → Repository
Network → ViewModel
Model → UI

yaml
Copy code

---

## Naming Conventions

- Folder names: PascalCase
- File names: camelCase
- One feature per folder under `View/`

---

## Design Principles

- Single Responsibility
- Predictable data flow
- Testable components
- Cursor-friendly navigation
- Scales well for large apps

---

## Notes for Cursor / AI Tools

- UI logic belongs in ViewModel
- Data access belongs in Repository
- Never place API calls in View
- Respect folder boundaries strictly

---
