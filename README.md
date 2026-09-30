# ORION Discipline Wing — Frontend

> Internal administration and management portal for the ORION Discipline Wing / Committee.

## Overview

The ORION Discipline Wing frontend is an **admin-first React application** for managing the operational records of an ORION club committee.

The interface is intentionally designed to start with **empty records**. Committee members can add the real members, events, attendance, tasks, duties, contributions and other records through the UI.

This repository contains the **frontend only**. During development, records are stored in the browser with `localStorage`. The backend team can later replace the local data layer with authenticated API calls without redesigning the main screens.

## Core workflow

```text
Administrator login
   ↓
Dashboard
   ↓
Add/manage members
   ↓
Create an event
   ↓
Open attendance → Present / Late / Absent
   ↓
Assign tasks and duties
   ↓
Record and verify contributions
   ↓
Reports & analytics
   ↓
Notifications + Activity Log
```

## Pages



| Route            |            Purpose                   |
| ---------------- | ------------------------------------ |
| `/login`         | Administrator login                  |
| `/`              | Dashboard & operational overview     |
| `/members`       | Member directory & member management |
| `/attendance`    | Event-based attendance management    |
| `/events`        | Create & manage events               |
| `/tasks`         | Assign, track & review tasks         |
| `/contributions` | Record contribution history          |
| `/duties`        | Assign & verify event duties         |
| `/reports`       | Attendance/task reports & CSV export |
| `/notifications` | Operational notifications            |
| `/activity-log`  | Audit-style activity history         |
| `/settings`      | Administrator & local-data controls  |


## Attendance workflow

1. Create an event from **Events**.
2. Open **Attendance**.
3. Select the event.
4. Search members by name, member ID or wing.
5. Mark each member **Present**, **Late** or **Absent**.
6. Use **Mark all present/absent** when appropriate.
7. The event totals and attendance percentage update automatically.
8. Attendance actions are recorded in the local activity log.

## Contribution records

The contribution page deliberately does **not** use points, rankings or a `/100` score.

A contribution contains normal descriptive information such as:

- Member
- Date
- Contribution type
- Description of actual work
- Event/activity
- Verifier

## Empty-data design

The project does not ship with fake members or fake events. A fresh browser session starts with empty operational records.

This makes the portal suitable for demonstrating the actual committee workflow without presenting placeholder people as real ORION members.

## Technology

- React
- Vite
- React Router
- Recharts
- CSS-based responsive UI
- Browser `localStorage` during frontend-only development
- ORION black/gold extracted logo asset in `public/orion-logo.png`

## Requirements

- Node.js 18+
- npm 9+
- VS Code or another JavaScript editor

## Run locally

```bash
npm install
npm run dev
```

Then open the localhost URL shown by Vite.

### Windows PowerShell note

If Windows shows an error that `npm.ps1` cannot be loaded because script execution is disabled, open the VS Code terminal as **Command Prompt** and run the same commands there.

## Demo authentication

The current login is frontend-only. Any non-empty email/member ID and password can enter the portal.

This is intentional for the frontend handoff. **Do not use this authentication model in production.** The backend must implement real authentication, password/session handling and authorization.

## Data storage

The current frontend stores operational records in browser `localStorage` so that the UI can be demonstrated without a backend.

This is development storage only. It is not a substitute for a database or secure server-side authorization.

## Backend integration

The intended production architecture is:

```text
React UI
   ↓
API/service layer
   ↓
Backend REST API
   ↓
Database
```



## GitHub handoff

repository name:

`orion-discipline-wing`

After creating the repository:

```bash
git init
git add .
git commit -m "Initial ORION Discipline Wing frontend"
git branch -M main
git remote add origin <YOUR-GITHUB-REPOSITORY-URL>
git push -u origin main
```


## Project status

**Frontend:** ready for GitHub/backend handoff.

**Backend:** not included. Authentication, database persistence, authorization, server-side validation, real notifications and production audit/security controls still need to be implemented by the backend team.
