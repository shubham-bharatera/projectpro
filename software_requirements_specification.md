# Software Requirements Specification (SRS)
## AI-Powered Project Management & Reporting Web App

### 1. Introduction
**1.1 Purpose**
The purpose of this document is to define the software requirements for an AI-powered project management web application. The system enables rapid, chat-based progress updates and utilizes AI to automatically categorize tasks, flag blockers, and generate dynamic dashboards and aggregate reports.

**1.2 Scope**
The application will serve as a continuous data-entry tool and a visualization platform for project tracking. It features an interactive input engine, real-time Jira-style Kanban dashboards, and automated daily, weekly, and monthly reporting views utilizing AI logic. The core development will be orchestrated via Google Antigravity, with AI logic prototyped in Google Opal.

### 2. Overall Description
**2.1 User Workflow**
1. Users enter task metadata (Project, Assignee, Task, Due Date) into sticky fields.
2. Users continuously submit brief progress updates via a chat-style interface.
3. The system parses updates, automatically flagging items containing the keyword "BLOCKED".
4. Users can click "Show Dashboard" for a real-time Kanban view or "Generate Report" (Daily, Weekly, Monthly) for AI-aggregated tables and visualizations.

**2.2 Technology Stack Guidelines**
*   **Core Development / IDE:** Google Antigravity (Agent-driven scaffolding, Next.js framework, real-time UI generation).
*   **AI Logic Prototyping:** Google Opal (Visual node-based prompt chaining and NLP logic).
*   **Database:** Real-time database (e.g., Firebase) to support live sync.

### 3. System Features
**3.1 Interactive Input Engine**
*   **Description:** The primary interface for users to log progress.
*   **Requirements:**
    *   Input fields for: Assignee Name, Project Name, Task Name.
    *   Date range selector for Due Date.
    *   Chat-style text box for inputting progress updates.
    *   Data entered into sticky fields must persist between chat submissions to allow for rapid, continuous data entry.

**3.2 AI Natural Language Processing (NLP)**
*   **Description:** The background logic processing chat inputs.
*   **Requirements:**
    *   Parse the submitted text update.
    *   Detect the exact keyword "BLOCKED" (case-insensitive) within the text update.
    *   Update the task's database status to `blocked` if the keyword is detected.

**3.3 Real-Time Kanban Dashboard ("Show Dashboard")**
*   **Description:** A direct, non-aggregated view of current task statuses.
*   **Requirements:**
    *   Accessed via a top-level "Show Dashboard" button.
    *   Displays tasks as draggable cards in a Jira-style Kanban board (e.g., To Do, In Progress, Blocked, Done).
    *   Automatically routes and displays any task flagged as `blocked` in the Blocker column.
    *   Must reflect database changes in real-time without requiring a page reload.

**3.4 Report Generation Module**
*   **Description:** Aggregates and visualizes data based on timeframes.
*   **Requirements:**
    *   Accessed via a "Generate Report" dropdown button (Options: Daily, Weekly, Monthly).
    *   **Daily Report (Scrum View):** Renders the current day's active tasks and updates in the Kanban board format.
    *   **Weekly/Monthly Reports:** 
        *   Renders data in a tabular format (Columns: Project Name, Assigned To, Task Name, Due Date, Latest Progress Updates, Blockers).
        *   Generates visual elements (Bar charts, Pie charts) to represent task distribution, completion rates, and blocker frequency.

### 4. User Interface (UI) Layout Requirements
*   **Top Navigation/Action Bar:** Must contain the "Show Dashboard" button (left/primary) and the "Generate Report" dropdown (right/secondary).
*   **Main Content Area (Input State):** Split view or focused view with sticky metadata fields at the top and a chat feed/input box below.
*   **Main Content Area (Dashboard/Report State):** Dynamic rendering area that swaps between the Kanban component and the Chart/Table components based on user selection.

### 5. Non-Functional Requirements
*   **Performance:** The "Show Dashboard" button must load within 1 second using real-time database subscriptions.
*   **Usability:** The input engine must support rapid keyboard navigation to facilitate continuous logging for multiple team members.