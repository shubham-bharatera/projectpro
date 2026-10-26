# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview
AI-Powered Project Management & Reporting Web App designed to eliminate friction in daily scrum updates and reporting. It features a chat-driven input engine, real-time Kanban dashboards, and AI-aggregated reports.

## Architecture & Structure
- **Frontend Framework:** Next.js (scaffolded via Google Antigravity).
- **UI Components:** shadcn/ui for Kanban boards, tables, and layout.
- **Visualizations:** Recharts for report charts (Bar/Pie).
- **Database:** Real-time database (e.g., Firebase) for live sync of task statuses.
- **AI Logic:** Prototyped in Google Opal; focuses on NLP parsing of chat updates and case-insensitive "BLOCKED" keyword detection to automatically update task status.

### Key Modules
- **Interactive Input Engine:** Sticky metadata fields (Assignee, Project, Task, Due Date) and a chat interface for progress updates.
- **Real-Time Kanban Dashboard:** Live view of tasks categorized by status (To Do, In Progress, Blocked, Done).
- **Report Generation Module:** Time-based aggregation (Daily, Weekly, Monthly) providing both tabular and visual (Chart) summaries.

## Common Development Tasks
*Note: As the project is in the initial specification phase, specific build/test commands are not yet defined in the codebase. Standard Next.js commands are expected once implementation begins.*

- **Build:** `npm run build` (expected)
- **Develop:** `npm run dev` (expected)
- **Lint:** `npm run lint` (expected)
