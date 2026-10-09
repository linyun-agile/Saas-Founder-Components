# Founder Prototype Labs

## Stage 1 — Lab 1: SaaS Dashboard

Build a small SaaS dashboard using modern frontend components.

The purpose of this lab is **not** to learn every detail of React or Next.js. The goal is to become familiar with the reusable UI building blocks commonly used in modern web applications.

By the end of this lab, you should be able to look at a SaaS interface and identify components such as:

- Sidebar
- Navbar
- Card
- Table
- Badge
- Dialog
- Dropdown Menu
- Tooltip
- Avatar
- Input
- Select
- Router

Instead of thinking:

> “How do I build this interaction from scratch?”

you should begin thinking:

> “What existing UI component or pattern solves this problem?”

---

# 1. Project

You are building a fictional AI SaaS dashboard called:

# PromptDesk

PromptDesk allows users to manage AI projects and monitor their model usage.

For this lab, there is:

- no backend
- no database
- no authentication
- no API calls

All data can be hard-coded.

The focus is purely on:

```text
Page structure
+
Reusable UI components
+
Navigation
```

---

# 2. Learning Goals

After completing this lab, you should understand the role of:

| Concept | Purpose |
|---|---|
| UI Kit | Provides reusable interface primitives |
| Component | Reusable piece of UI |
| Layout | Defines the structure shared by multiple pages |
| Router | Maps URLs to pages |
| Navigation | Allows users to move between pages |
| Dialog | Temporary modal interface |
| Dropdown Menu | Contextual menu attached to a trigger |
| Tooltip | Small explanatory hover UI |
| Table | Displays structured data |
| Badge | Displays compact status information |
| Avatar | Represents a user |
| Input | Collects user text |
| Select | Lets users choose from predefined options |

The most important goal is to develop **component recognition**.

---

# 3. Tech Stack

Use the following stack for this lab:

```text
Next.js
React
TypeScript
Tailwind CSS
shadcn/ui
Lucide Icons
```

Recommended package manager:

```text
pnpm
```

Using `npm` or `yarn` is also fine.

---

# 4. What You Are Building

The application contains four pages:

```text
/dashboard
/projects
/usage
/settings
```

The basic layout should look like:

```text
┌────────────────────────────────────────────────────────┐
│ Sidebar │ PromptDesk                    Bell   Avatar  │
│         ├──────────────────────────────────────────────┤
│         │                                              │
│Dashboard│  Overview                                    │
│Projects │                                              │
│Usage    │  ┌──────────┐ ┌──────────┐ ┌──────────┐    │
│Settings │  │ Projects │ │ Tokens   │ │ Cost     │    │
│         │  │    12    │ │   8.2K   │ │  $24.50  │    │
│         │  └──────────┘ └──────────┘ └──────────┘    │
│         │                                              │
│         │  Recent Projects                             │
│         │                                              │
│         │  ┌───────────────────────────────────────┐   │
│         │  │ Project       Model      Usage Status │   │
│         │  │ Research      GPT-5      2450  Active │   │
│         │  │ Copy Writer   Claude     1820  Active │   │
│         │  │ Translator    Gemini      890  Paused │   │
│         │  └───────────────────────────────────────┘   │
│         │                                              │
└────────────────────────────────────────────────────────┘
```

Do not worry about matching this layout exactly.

The important part is the component structure.

---

# 5. Suggested Project Structure

A possible project structure:

```text
app/
├── layout.tsx
│
├── dashboard/
│   └── page.tsx
│
├── projects/
│   └── page.tsx
│
├── usage/
│   └── page.tsx
│
└── settings/
    └── page.tsx

components/
├── app-sidebar.tsx
├── top-nav.tsx
├── stat-card.tsx
├── project-table.tsx
└── ui/
    └── ...

lib/
└── utils.ts
```

You do not have to follow this structure exactly.

However, avoid putting the entire application inside a single component.

---

# 6. Setup

Create a Next.js application.

```bash
pnpm create next-app@latest promptdesk
```

Recommended options:

```text
TypeScript          Yes
ESLint              Yes
Tailwind CSS        Yes
src/ directory      Optional
App Router          Yes
Turbopack           Yes
Import alias        @/*
```

Enter the project:

```bash
cd promptdesk
```

Run the development server:

```bash
pnpm dev
```

Open:

```text
http://localhost:3000
```

---

# 7. Install shadcn/ui

Initialize shadcn:

```bash
pnpm dlx shadcn@latest init
```

Add the components needed for this lab.

```bash
pnpm dlx shadcn@latest add button
pnpm dlx shadcn@latest add card
pnpm dlx shadcn@latest add badge
pnpm dlx shadcn@latest add table
pnpm dlx shadcn@latest add dialog
pnpm dlx shadcn@latest add input
pnpm dlx shadcn@latest add select
pnpm dlx shadcn@latest add avatar
pnpm dlx shadcn@latest add dropdown-menu
pnpm dlx shadcn@latest add tooltip
pnpm dlx shadcn@latest add separator
```

You may install additional shadcn components if useful.

---

# 8. Install Icons

Install Lucide:

```bash
pnpm add lucide-react
```

Possible icons:

```text
LayoutDashboard
FolderKanban
ChartNoAxesCombined
Settings
Bell
Plus
User
LogOut
ChevronDown
```

The exact icons are not important.

---

# 9. Task A — Application Layout

Create the basic SaaS layout.

The page should contain:

```text
Sidebar
Top Navigation
Main Content Area
```

## Requirements

- Sidebar appears on the left.
- Top navigation appears above the content area.
- Main content fills the remaining space.
- Sidebar navigation appears on every application page.

Suggested structure:

```text
Application Layout
│
├── Sidebar
│
└── Main Area
    │
    ├── Top Nav
    │
    └── Page Content
```

---

# 10. Task B — Sidebar

Create:

```text
components/app-sidebar.tsx
```

The sidebar should contain:

```text
PromptDesk

Dashboard
Projects
Usage
Settings
```

Each item should have:

```text
Icon
Label
Link
```

Example conceptual structure:

```text
Dashboard
→ /dashboard

Projects
→ /projects

Usage
→ /usage

Settings
→ /settings
```

Use Next.js navigation rather than manually changing component state.

## Goal

Understand the relationship:

```text
Navigation Item
↓
URL
↓
Router
↓
Page
```

---

# 11. Task C — Top Navigation

Create:

```text
components/top-nav.tsx
```

Include:

```text
PromptDesk
Notifications
User Avatar
```

The right side should eventually contain:

```text
Bell icon
Avatar
```

The Avatar will later open a dropdown menu.

---

# 12. Task D — Dashboard Page

Create:

```text
/dashboard
```

Page title:

```text
Overview
```

The dashboard should contain:

```text
Stat Cards
Recent Projects Table
New Project Button
```

---

# 13. Task E — StatCard Component

Create:

```text
components/stat-card.tsx
```

The component should accept data similar to:

```tsx
<StatCard
  title="Total Projects"
  value="12"
  description="+2 this month"
/>
```

Display at least three cards:

```text
Total Projects
12
+2 this month
```

```text
Tokens Used
8.2K
+12% this week
```

```text
Current Cost
$24.50
This month
```

## Important Concept

Distinguish between:

### UI Primitive

```text
Card
```

and:

### Product Component

```text
StatCard
```

`Card` is generic.

`StatCard` represents a specific concept in your product.

---

# 14. Task F — Project Table

Create:

```text
components/project-table.tsx
```

Use hard-coded data.

Example:

| Project | Model | Usage | Status |
|---|---|---:|---|
| Research Agent | GPT-5 | 2,450 | Active |
| Copy Writer | Claude | 1,820 | Active |
| Translator | Gemini | 890 | Paused |

Use the shadcn:

```text
Table
Badge
```

components.

Use a Badge for project status.

Example:

```text
Active
Paused
```

The table does not need sorting, filtering, or pagination.

---

# 15. Task G — New Project Dialog

Add a button to the Dashboard:

```text
+ New Project
```

When clicked, open a Dialog.

The Dialog should contain:

```text
Create Project

Project Name
[_____________________]

Model
[ GPT-5           ▼ ]

Cancel
Create Project
```

Use:

```text
Button
Dialog
Input
Select
```

The form does not need to actually create anything.

## Goal

Experience composing multiple UI primitives into one feature.

Conceptually:

```text
New Project Feature
│
├── Button
├── Dialog
├── Input
└── Select
```

---

# 16. Task H — User Dropdown

Clicking the Avatar should open a menu.

Example:

```text
Richard
richard@example.com

────────────

Profile
Settings
Log out
```

Use:

```text
Avatar
DropdownMenu
Separator
```

Do not manually implement dropdown positioning using:

```text
position: absolute
display: none
z-index
```

unless you are doing so purely for experimentation.

The point of this lab is to learn when a UI primitive already exists.

---

# 17. Task I — Tooltip

Add a Tooltip to the notification Bell.

When the mouse hovers over the icon:

```text
Notifications
```

should appear.

Use the existing Tooltip primitive.

---

# 18. Task J — Router

Implement the four routes:

```text
/dashboard
/projects
/usage
/settings
```

Only `/dashboard` needs significant content.

The other pages can initially be simple.

Example:

## Projects

```text
Projects

Your projects will appear here.
```

## Usage

```text
Usage

Usage analytics will appear here.
```

## Settings

```text
Settings

Manage your PromptDesk preferences.
```

The sidebar navigation must correctly navigate between these routes.

---

# 19. Hard-Coded Data

You can use data similar to:

```ts
const projects = [
  {
    id: 1,
    name: "Research Agent",
    model: "GPT-5",
    usage: 2450,
    status: "Active",
  },
  {
    id: 2,
    name: "Copy Writer",
    model: "Claude",
    usage: 1820,
    status: "Active",
  },
  {
    id: 3,
    name: "Translator",
    model: "Gemini",
    usage: 890,
    status: "Paused",
  },
]
```

There is intentionally no backend in this lab.

Database persistence will be introduced in a later stage.

---

# 20. Required Components

By the end of the lab, you should have used these components at least once:

```text
Button
Card
Badge
Table
Dialog
Input
Select
Avatar
Dropdown Menu
Tooltip
Separator
```

You should also have used:

```text
Next.js Router
Next.js Link
Lucide Icons
Reusable React Components
```

---

# 21. Acceptance Tests

The lab is complete when all of the following conditions are satisfied.

## Routes

- [ ] `/dashboard` works
- [ ] `/projects` works
- [ ] `/usage` works
- [ ] `/settings` works
- [ ] Sidebar navigation works

## Layout

- [ ] Sidebar exists
- [ ] Top navigation exists
- [ ] Main content area exists
- [ ] Layout is shared across pages

## Dashboard

- [ ] Dashboard contains an Overview heading
- [ ] At least three stat cards are displayed
- [ ] Recent Projects table is displayed
- [ ] Project status uses Badge components

## Dialog

- [ ] `New Project` button exists
- [ ] Clicking it opens a Dialog
- [ ] Dialog contains an Input
- [ ] Dialog contains a Select
- [ ] Dialog can be closed

## User Menu

- [ ] Avatar exists
- [ ] Clicking Avatar opens Dropdown Menu
- [ ] Menu contains Profile
- [ ] Menu contains Settings
- [ ] Menu contains Log out

## Tooltip

- [ ] Notification button exists
- [ ] Hovering shows a Tooltip

## Code Structure

- [ ] `StatCard` is reusable
- [ ] Sidebar is a separate component
- [ ] Top Nav is a separate component
- [ ] Project Table is a separate component
- [ ] No single page component contains the entire application implementation

---

# 22. Concept Check

Before considering the lab finished, make sure you can answer these questions without looking anything up.

### 1

A user clicks their profile picture and a small menu appears.

What UI component would you search for?

```text
Dropdown Menu
```

### 2

A user clicks `Delete Project` and a confirmation box appears above the page.

What would you search for?

```text
Dialog
or
Alert Dialog
```

### 3

You need to display:

```text
Active
Paused
Failed
```

next to project names.

What UI component fits?

```text
Badge
```

### 4

You hover over an unfamiliar icon and explanatory text appears.

What is this?

```text
Tooltip
```

### 5

You need to display 100 rows of structured project data.

What UI pattern would you initially consider?

```text
Table
```

### 6

Users need to move between:

```text
/dashboard
/projects
/settings
```

What system handles this?

```text
Router
```

The exact library API is less important than recognizing the component category.

---

# 23. Bonus Tasks

These are optional.

Only attempt them after the required lab is complete.

## Bonus A — Command Palette

Implement:

```text
⌘ K
```

to open a command palette.

Possible commands:

```text
Go to Dashboard
Go to Projects
Go to Usage
Go to Settings
Create Project
```

Useful keyword:

```text
Command Palette
```

---

## Bonus B — Skeleton

Display placeholder UI while pretending that the dashboard is loading.

Useful component:

```text
Skeleton
```

---

## Bonus C — Empty State

On the Projects page, pretend that the user has no projects.

Create an empty state:

```text
No projects yet

Create your first project to get started.

[ Create Project ]
```

Recognize:

```text
Empty State
```

as a reusable UI pattern.

---

## Bonus D — Responsive Sidebar

On smaller screens:

```text
Sidebar
↓
Drawer / Sheet
```

Instead of permanently showing the sidebar.

---

# 24. What Not to Study Yet

Do not spend significant time studying:

```text
React Fiber
Virtual DOM internals
Webpack internals
Turbopack internals
React reconciliation algorithms
Browser rendering engine internals
Advanced SSR internals
Complex state management
Backend architecture
Databases
Authentication
```

Those topics may be useful later.

They are not the goal of this lab.

---

# 25. Component Vocabulary

The main output of this lab is this vocabulary:

| Requirement | Component / Pattern |
|---|---|
| clickable action | Button |
| grouped information | Card |
| compact status | Badge |
| structured rows | Table |
| modal interaction | Dialog |
| text entry | Input |
| choose one option | Select |
| user identity | Avatar |
| contextual menu | Dropdown Menu |
| hover explanation | Tooltip |
| divide sections | Separator |
| move between pages | Router |
| sidebar navigation | Sidebar |
| top navigation | Navbar |
| keyboard search/actions | Command Palette |
| loading placeholder | Skeleton |
| no-data screen | Empty State |
| operation feedback | Toast |

The goal is to start translating product requirements into component names.

---

# 26. Mental Model

Before this lab:

```text
"I need a little box that appears when someone clicks their avatar."

→ How do I build that?
→ div?
→ onClick?
→ CSS?
→ position absolute?
```

After this lab:

```text
"I need a menu attached to an avatar."

→ Dropdown Menu
→ Find existing component
→ Configure it
→ Compose it into the page
```

That change in thinking is the main purpose of the lab.

---

# 27. Definition of Done

The project does not need to look production-ready.

You are finished when you can:

1. navigate through the four pages,
2. identify every major UI component on the Dashboard,
3. use existing UI primitives instead of recreating common patterns,
4. create several reusable product-specific components,
5. explain the difference between a UI primitive and a product component,
6. look at another SaaS dashboard and begin naming its interface patterns.

---

# 28. Final Exercise

After completing the project, open any modern SaaS dashboard.

Do not write code.

Spend five minutes identifying components.

Try to label things such as:

```text
Sidebar
Navbar
Breadcrumb
Tabs
Card
Table
Dropdown Menu
Dialog
Tooltip
Toast
Command Palette
Skeleton
Empty State
Pagination
Search
Filter
Avatar
Badge
```

The goal is to develop the habit:

```text
See UI
↓
Identify Pattern
↓
Identify Component Category
↓
Find Existing Implementation
↓
Compose
```

rather than:

```text
See UI
↓
Start coding from scratch
```

---

# Lab Complete

When all required acceptance tests pass:

```text
Stage 1
Lab 1
SaaS Dashboard
✅ Complete
```

Next:

```text
Stage 1 — Lab 2

State + Forms
```

In Lab 2, the application will begin to have meaningful client-side behavior using:

```text
Application State
Form State
Validation
Zustand
React Hook Form
Zod
```