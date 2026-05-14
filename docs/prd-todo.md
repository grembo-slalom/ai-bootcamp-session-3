# Product Requirements Document (PRD) - TODO App Upgrade MVP

## 1. Overview

We are upgrading the existing basic TODO app so users can better organize and act on tasks without increasing system complexity. The MVP focuses on adding optional due dates, simple task priorities, and date-based filters while keeping the solution local-only and avoiding backend changes. The goal is a lean, teachable enhancement that improves day-to-day usefulness without expanding into advanced workflow features.

---

## 2. MVP Scope

- Add an optional `dueDate` field to tasks using ISO `YYYY-MM-DD` format.
- Add a `priority` field with allowed values `P1`, `P2`, and `P3`.
- Default `priority` to `P3` when not provided.
- Add filter views for `All`, `Today`, and `Overdue`.
- Keep task storage local only with no backend or external storage changes.
- Require `title` for every task.
- Treat invalid `dueDate` values as absent rather than failing the task.
- In `All` view, show completed and incomplete tasks.
- In `Today` and `Overdue` views, show only incomplete tasks.

---

## 3. Post-MVP Scope

- Visually highlight overdue tasks so they stand out in the task list.
- Add sorting rules in this order: overdue first, then priority from `P1` to `P3`, then due date ascending, with tasks that have no due date shown last.
- Consider visual priority badges or color-coding for `P1`, `P2`, and `P3`.

---

## 4. Out of Scope

- Backend changes of any kind.
- External storage or integrations.
- Notifications.
- Recurring tasks.
- Multi-user features.
- Keyboard navigation improvements.
- Broader accessibility enhancements beyond the current baseline.