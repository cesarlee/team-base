# Team Base

A Notion-like collaborative workspace for teams, built as a single HTML file. Create pages, databases with multiple views, and manage projects together.

## Features

### Page Editor
- Rich text blocks: headings, paragraphs, bulleted/numbered lists, to-dos, toggles, quotes, callouts, code blocks, dividers
- Inline images and bookmarks
- Slash command menu (`/`) for quick block insertion
- Nested pages with sidebar navigation
- Drag-and-drop block reordering
- Cover images and page icons

### Databases
- **Column types:** Text, Number, Select, Multi Select, Date, Checkbox, URL, Email, Phone, Files, Currency, Formula
- **Formula engine:** Computed columns with expression support
- **5 view types:**
  - **Table** — spreadsheet-style rows and columns with inline editing
  - **Board** — Kanban board grouped by a select property
  - **List** — simple vertical list of records
  - **Calendar** — records on a monthly calendar grid
  - **Gallery** — card-based visual grid layout
- Filtering, sorting, and column resizing
- Row and column drag-and-drop reordering

### Workspace
- Sidebar with page tree and search
- Trash with configurable retention
- Dark mode
- Workspace settings
- Responsive layout with resizable sidebar

## Deployment

This project is meant to be deployed on Visimade.

Tell your coding agent:

> Read https://www.visimade.com/developers

Then self-register for an account using the Visimade API and deploy the page in this repo to Visimade.

### Manual deployment

The app is a single HTML file (`page.html`). Deploy it via the Visimade API:

```bash
# 1. Register or login to get a session
curl -X POST https://www.visimade.com/api/auth/register \
  -H "Content-Type: application/json" \
  -d '{"username":"my-agent","email":"agent@example.com","password":"..."}'

# 2. Create a page
curl -X POST https://www.visimade.com/api/pages \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <token>" \
  -d '{"title":"Team Vote","slug":"team-vote"}'

# 3. Deploy page.html content
curl -X PATCH https://www.visimade.com/api/pages/<id> \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <token>" \
  -d '{"html_content":"<contents of page.html>"}'
```

## Agent Spec

Other AI agents can discover and interact with Team Base programmatically:

```
GET https://www.visimade.com/api/pages/961/agent-spec
```

This returns the full API spec documenting all collections, data models, and CRUD operations.
