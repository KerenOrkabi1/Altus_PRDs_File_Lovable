# Altus Project Overview — Implementation Tasks

## Legend
- [ ] To do
- [ ] Done

---

## Phase 0: Foundation & Design System

- [ ] **0.1** Install Fluent UI 9 (`@fluentui/react-components`, `@fluentui/react-icons`)
- [ ] **0.2** Set up FluentProvider with custom Altus theme (map design spec colors, typography, spacing, shadows to Fluent tokens)
- [ ] **0.3** Update Tailwind config and `index.css` with complementary Altus design tokens (status colors: green/yellow/red, AI layer tint, spacing scale)
- [ ] **0.4** Create shared TypeScript interfaces for all data entities (Project, CostData, ScheduleData, ScopeData, ResourceData, RiskData, IssueData, DependencyData, ChangeData, AIInsightData)
- [ ] **0.5** Create mock data files with realistic project data (2-3 projects with varying health states)
- [ ] **0.6** Set up routing structure: `/projects` (list), `/projects/:id` (overview with tabs)

---

## Phase 1: MVP — Factual Overview

### 1A: Projects List Page
- [ ] **1A.1** Build `ProjectsListPage` — table/card view of all projects with status badges, last updated, and forecast indicators
- [ ] **1A.2** Add sorting/filtering by status (On Track, At Risk, Critical)
- [ ] **1A.3** Navigate to individual project overview on row/card click

### 1B: Project Overview Shell
- [ ] **1B.1** Build `ProjectOverviewPage` with tab navigation (Overview as default, plus placeholder tabs: Details, Tasks, Issues, etc.)
- [ ] **1B.2** Build project header with project name, status badge, and breadcrumb navigation back to project list

### 1C: Executive Summary
- [ ] **1C.1** Build `ExecutiveSummary` component — project status, forecast indicator, last updated timestamp (ISO-8601), primary next action with navigable link
- [ ] **1C.2** Style status/forecast as color-coded badges (green/yellow/red)
- [ ] **1C.3** Implement "attention needed" callout when project is not on track

### 1D: Core Domains (Always Visible)
- [ ] **1D.1** Build `DomainCard` reusable component — status indicator, key metrics, trend hint, drill-down link
- [ ] **1D.2** Build `CostDomain` — budget, actual spend, variance, cost status, forecast
- [ ] **1D.3** Build `ScheduleDomain` — planned vs forecast end date, completion %, schedule status
- [ ] **1D.4** Build `ScopeDomain` — baseline vs current scope, change count, scope status
- [ ] **1D.5** Build `ResourceDomain` — allocated vs utilized, conflicts detected, resource status

### 1E: Conditional Domains (Reveal on Signal)
- [ ] **1E.1** Build `ConditionalDomainCard` — same base as DomainCard but with conditional visibility logic (show only when status ≠ Green)
- [ ] **1E.2** Build `RisksDomain` — risk count, critical risk count, risk status
- [ ] **1E.3** Build `IssuesDomain` — issue count, open issues, issue status
- [ ] **1E.4** Build `DependenciesDomain` — dependency count, broken dependencies, status
- [ ] **1E.5** Build `ChangesDomain` — change request count, pending approvals, status

### 1F: Unified Diagnostic + Drill-down
- [ ] **1F.1** Implement "Show all domains" toggle to reveal all conditional domains regardless of status
- [ ] **1F.2** Ensure all drill-down links navigate to respective placeholder tabs within the project

### 1G: Error/Edge Cases
- [ ] **1G.1** Build empty states for missing data per domain ("No data available")
- [ ] **1G.2** Build network error state with retry prompt
- [ ] **1G.3** Build permission denied state (simulated)

---

## Phase 2: AI Insight Layer

- [ ] **2.1** Build `AIInsightLayer` component — clearly labeled, visually subordinate, with toggle on/off
- [ ] **2.2** Create mock AI service returning simulated insights with confidence levels and source signals
- [ ] **2.3** Build `AIInsightCard` — displays insight text, confidence badge (high/medium/low), source signals list, "AI suggests, human decides" disclaimer
- [ ] **2.4** Build descriptive insights display (interpretations of factual data)
- [ ] **2.5** Build anticipatory drift section (predicted schedule/cost deviations)
- [ ] **2.6** Implement AI toggle persistence (per-user preference simulation via localStorage)

---

## Phase 3: Agentic AI + Polish

### 3A: Agentic Features
- [ ] **3A.1** Build `AgenticSuggestion` component — suggested action with "Approve" / "Dismiss" buttons
- [ ] **3A.2** Build "Simulate outcomes" interaction (mock simulation with before/after comparison)
- [ ] **3A.3** Build "Draft follow-up" action (simulated email/message draft generation)
- [ ] **3A.4** Implement approval audit log (simulated, displayed in a collapsible panel)

### 3B: Polish & Refinement
- [ ] **3B.1** Add motion/transitions — section reveals (200-300ms), hover states (100-150ms), page transitions (300-400ms)
- [ ] **3B.2** Accessibility pass — ARIA labels, keyboard navigation, focus management, contrast checks
- [ ] **3B.3** Responsive layout refinements (desktop-first, but functional on tablet)
- [ ] **3B.4** Role simulation toggle (PM / PMO / Read-Only) to demonstrate permission differences

---

## Implementation Order

Build sequentially: **0 → 1A → 1B → 1C → 1D → 1E → 1F → 1G → 2 → 3A → 3B**

Each task should be committed and verified before moving to the next group.
