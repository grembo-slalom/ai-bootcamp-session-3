# Cloud Architecture Overview

This monorepo contains a React frontend and a Node.js backend. The frontend provides the user interface for managing tasks, and the backend exposes task APIs backed by an in-memory SQLite database.

## System Context

```mermaid
flowchart LR
    User[User]
    Frontend[Frontend App\nReact UI\npackages/frontend]
    Backend[Backend API\nExpress.js\npackages/backend]
    Database[(Task Data Store\nIn-Memory SQLite)]

    User --> Frontend
    Frontend -->|HTTP /api/tasks| Backend
    Backend --> Database
```

## Create TODO Sequence

```mermaid
sequenceDiagram
    actor User
    participant Frontend as Frontend App
    participant Backend as Backend API
    participant Database as In-Memory SQLite

    User->>Frontend: Enter task details and submit form
    Frontend->>Frontend: Validate required title
    Frontend->>Backend: POST /api/tasks
    Backend->>Backend: Validate request body
    Backend->>Database: Insert task record
    Database-->>Backend: Return created task
    Backend-->>Frontend: 201 Created + task payload
    Frontend->>Frontend: Refresh task list
    Frontend-->>User: Show new TODO in list
```

## Monorepo Components

- `packages/frontend`: React application for creating, editing, filtering, and viewing tasks.
- `packages/backend`: Express API that handles task CRUD operations.
- Root workspace: Shared monorepo scripts for running frontend and backend together.

## Current Characteristics

- The frontend and backend are developed and run from the same monorepo.
- The backend currently stores data in an in-memory SQLite database, so task data does not persist across backend restarts.
- The frontend communicates with the backend through the `/api/tasks` endpoints.