# 🌟 Feature Documentation Template

## 1. 📌 Feature Overview
- **Feature Name**: 
- **Repo(s) Involved**: 
- **Feature Owner(s)**: 
- **Release Version**: May-July 2025
- **Purpose**:  
  _Brief description of the feature and the user/business problem it solves._

---

## 2. 🧠 User Flow (Simple Flowchart or Diagram)

_Attach a simple diagram showing how the user interacts with the feature step-by-step. Use [Excalidraw](https://excalidraw.com/) or similar tools._

Example:  
User ➝ Login ➝ Dashboard ➝ Click “Create KB” ➝ Fill Form ➝ Save ➝ Backend saves to DB ➝ Confirmation shown

---

## 3. 🖼️ Frontend Details

### Screens / Components Involved:
| Screen | Component(s) | Description |
|--------|---------------|-------------|
| KB Creation | `KBCreateForm.jsx`, `Sidebar.jsx` | Form to create new knowledge base |
| KB View | `KBViewer.jsx`, `Header.jsx` | Displays KB with tags, edit options |

### Screenshot(s):
_(Insert annotated screenshots of relevant UI here)_

---

## 4. 🔧 Backend Details

### Modules / Files Involved:
| Module/File | Description |
|-------------|-------------|
| `kbController.py` | Handles API routes for KB operations |
| `kbService.py` | Business logic for storing/updating KB |
| `authMiddleware.py` | Ensures only authenticated users can access KB APIs |

### APIs Used:
| Method | Endpoint | Purpose |
|--------|----------|---------|
| POST   | `/kb`     | Create new KB entry |
| GET    | `/kb/:id` | Fetch KB by ID |
| PUT    | `/kb/:id` | Update KB content |

### Database Tables:
| Table | Fields |
|-------|--------|
| `knowledge_base` | `id`, `title`, `content`, `created_by`, `created_at` |

---

## 5. 📝 Feature Flow (Step-by-Step)

- User logs in and accesses the dashboard.
- User clicks on "Create Knowledge Base".
- A form opens (handled by `KBCreateForm.jsx`) where user inputs title and content.
- On submit, frontend calls `POST /kb` with the form data.
- Backend validates input, saves to `knowledge_base` table.
- On success, a success toast is shown and the user is redirected to the KB viewer.
- Viewer page fetches KB using `GET /kb/:id`.

---

## 6. 📎 Notes / Edge Cases / Permissions

- Only logged-in users can create or edit KB.
- Admin users can edit/delete any KB.
- If backend fails, user sees an error message.
- Draft-saving feature to be added in future sprints.

---

## 7. 🔗 Related Links

- API Postman Collection: `[Insert Postman link here]`
- GitHub PRs (all PRs which have worked on this Feature): `[Insert PR link here]`

---
