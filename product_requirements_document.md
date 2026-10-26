# Product Requirements Document (PRD)
**Product Name:** AI-Powered Agile Tracker & Reporting App
**Document Version:** 1.0
**Status:** Draft

## 1. Product Overview
**1.1 Vision**
To eliminate the friction of daily scrum updates and manual project reporting by creating a seamless, chat-driven interface that uses AI to automatically categorize tasks, update Kanban boards in real-time, and generate comprehensive weekly/monthly leadership reports.

**1.2 Problem Statement**
Project managers and team members spend too much time manually moving Jira tickets, compiling weekly progress reports, and aggregating blocker data. Data entry is tedious, and deriving insights across multiple team members' updates requires manual compilation.

**1.3 Target Audience**
* **Project Managers / Scrum Masters:** Need a bird's-eye view of team progress, blockers, and automated reports for stakeholders.
* **Team Members (Engineers, Designers):** Need a frictionless, rapid way to log daily updates without navigating complex ticket hierarchies.

## 2. Objectives & Success Metrics
**2.1 Objectives**
* Reduce the time taken to log daily updates to under 30 seconds per team member.
* Automate 100% of the weekly and monthly progress report generation.
* Instantly surface blockers to reduce task cycle time.

**2.2 Key Results (KPIs)**
* **User Adoption:** 90% of team members logging updates daily.
* **Time Saved:** Reduce weekly report generation time from hours to one click.
* **System Latency:** "Show Dashboard" loads real-time data in < 1 second.

## 3. User Stories
* **As a user**, I want to fill in my project metadata once (sticky fields) and rapidly fire off multiple task updates via a chat box so I can save time.
* **As a user**, I want to type "BLOCKED" in my update so the system automatically flags it and moves it to the Blocker column.
* **As a Scrum Master**, I want to click "Show Dashboard" to instantly see a live Kanban board of today's statuses before standup.
* **As a Project Manager**, I want to click "Generate Report > Weekly" to get a clean table and pie/bar charts of what was accomplished, to share with stakeholders.

## 4. Feature Requirements

### Feature 1: Rapid Input Engine
* **Sticky Header:** Input fields for Assignee Name, Project Name, Task Name, and a Date Range selector (Due Date). These fields retain their values after submitting an update to allow for continuous entry.
* **Chat Interface:** A text input box where users type their natural language progress update. Submitting clears the chat input but keeps the sticky header.

### Feature 2: AI Logic Pipeline (Opal Prototyped)
* **Intent Parsing:** Evaluates the chat input. 
* **Blocker Detection:** If the string "BLOCKED" (case-insensitive) is present, the backend automatically flags the associated task's status as `Blocked`.

### Feature 3: Real-Time Kanban Dashboard ("Show Dashboard")
* **Trigger:** A prominent "Show Dashboard" button in the top navigation.
* **View:** A Jira-style Kanban board (e.g., To Do, In Progress, Blocked, Done).
* **Behavior:** Skips AI generation and fetches live database state. Updates submitted via the Input Engine appear instantaneously here without page reloads.

### Feature 4: Automated Reporting ("Generate Report")
* **Trigger:** A dropdown menu offering Daily, Weekly, and Monthly intervals.
* **Daily (Scrum):** Generates a Kanban board view filtered strictly to the current day's active tasks and updates.
* **Weekly/Monthly (Analytics):** 
    * **Table View:** Columns include Project Name, Assigned To, Task Name, Due Date, Latest Progress Updates, Blockers.
    * **Visualizations:** Generates Bar Charts (e.g., tasks completed per project) and Pie Charts (e.g., blocker distribution across teams).

## 5. User Interface & Flow
* **Top Navigation:** Contains "Show Dashboard" (Button) and "Generate Report" (Dropdown). 
* **Default State:** The Rapid Input Engine.
* **Transitions:** Clicking dashboard or reports replaces the Input Engine view with the respective data visualization component. Users can easily navigate back to the Input Engine.

## 6. Technical Architecture & Google Stack Strategy
* **App Generation & IDE:** **Google Antigravity**. Used to scaffold the Next.js frontend, wire up shadcn/ui components (for the Kanban board and tables), and integrate Recharts (for data visualization).
* **AI Prototyping:** **Google Opal**. Used to visually design and test the prompt chain that parses the chat updates and detects blockers before translating that logic to the application backend.
* **Database:** Real-time NoSQL or PostgreSQL (e.g., Firebase) to support live sync for the Kanban dashboard.

## 7. Out of Scope (Future Iterations)
* Integration with external ticketing tools (Jira, Linear, Asana).
* Emailing reports directly from the application.
* Complex user authentication and role-based access control (RBAC) (Keep simple for v1).