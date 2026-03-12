# App Flow / User Journey

## Sitemap

- Projects (List View)
- Project Overview (New Tab and Default Landing)
  - Executive Summary
  - Optional AI Insight Layer
  - Unified Diagnostic + Drill-down Section
    - Core Domains (Cost, Schedule, Scope, Resources)
    - Conditional Domains (Risks, Issues, Dependencies, Changes)
    - All Domains (Secondary reveal)
- Other Project Tabs (Existing)
  - Details
  - Tasks
  - Issues
  - etc.

## Page Purposes and Primary Actions

### Project Overview

**Purpose:** Provide a calm, factual, high-level landing page for each project to quickly assess health and identify needs.
**Primary Actions:**
- Assess project health status.
- Identify areas needing attention.
- Navigate to relevant sections for investigation or action.
- Toggle AI insights on/off.

### Executive Summary

**Purpose:** Offer an immediate snapshot of project status and critical next steps.
**Primary Actions:**
- Read a factual summary of project health.
- Determine forecast visibility.
- View last updated status.
- Understand the primary next action required.

### Optional AI Insight Layer

**Purpose:** Provide data interpretation, anticipate drift, and suggest next-best actions.
**Primary Actions:**
- Review AI-generated interpretations and insights.
- Consider AI-suggested next actions.
- Evaluate simulated outcomes.
- Approve or dismiss AI suggestions.

### Unified Diagnostic + Drill-down Section

**Purpose:** Present core and conditional project domains to diagnose issues and guide users to solutions.
**Primary Actions:**
- Scan domain-specific health indicators.
- Identify trends and issues within domains.
- Drill down into specific domain details (navigation to existing tabs).
- Access conditionally displayed domains.
- Reveal all domains.

## User Roles and Permissions

### Project Manager (PM)
- **Permissions:** Full read/write access to all project data, including the Overview page. Can toggle AI features.
- **Primary Use:** Daily/weekly project health checks, identifying actions, navigating to other parts of the project for updates.

### PMO User
- **Permissions:** Read-only access to most project data, including the Overview page. Can toggle AI features for insight but cannot directly modify project data.
- **Primary Use:** High-level project portfolio review, identifying projects needing intervention, supporting governance decisions.

## Primary User Journeys

### Journey 1: Weekly Project Health Check (Project Manager)
1. Project Manager opens an individual project in Altus.
2. Lands on the Project Overview tab (default).
3. Reviews the Executive Summary to quickly assess overall health and next action.
4. Scans Core and Conditional Domains for any anomalies.
5. If no immediate action is needed, moves to another project or closes the current project.

### Journey 2: Investigating a Drift Signal (PMO User)
1. PMO User opens a project flagged as potentially "at risk".
2. Lands on the Project Overview tab.
3. Activates the Optional AI Insight Layer.
4. Reviews AI insights for likely future drift and recommended actions.
5. Navigates to a specific domain (e.g., Schedule or Resources) to understand the underlying data, potentially suggesting further investigation to the Project Manager.

### Journey 3: Proposing a Corrective Action (Project Manager)
1. Project Manager lands on the Project Overview tab and identifies an issue in a Core Domain (e.g., Cost).
2. Activates the Optional AI Insight Layer.
3. Reviews AI suggestions for corrective actions, including simulations of potential outcomes.
4. Approves an AI-suggested action, which may involve drafting a follow-up or updating project data by navigating to the relevant existing tab, remaining fully in control of the actual change.
5. Navigates to the relevant Altus module (e.g., Budget/Finance) to implement the approved action.

## State Management / Data Flow Overview

- The Project Overview page acts as an aggregation layer for existing project data.
- Data is pulled from various Altus project modules (tasks, issues, resources, financials, etc.) upon page load.
- Executive Summary is generated dynamically based on real-time project metrics.
- Core and Conditional Domains display summarized data from their respective underlying systems.
- AI Insight Layer consumes the same project data, processes it, and generates its insights/recommendations. AI insights are generated on demand when enabled by the user.
- User interactions (e.g., toggling AI) trigger updates only to the display layer, not underlying project data.
- Drill-down actions navigate the user to existing Altus project tabs, passing the context of the current project.

## Error/Edge Cases

### Missing Data
- **Scenario:** A project lacks data in a specific domain (e.g., no budget information entered).
- **Handling:** The system will display "No data available" or similar message for that specific domain or metric. It will not prevent the rest of the page from loading.

### Permission Denied
- **Scenario:** A user attempts to view a project or specific data they do not have permissions for.
- **Handling:** Access denied messages will be displayed at the appropriate scope (e.g., "You do not have permission to view this project" or "Access denied to cost data"). The Overview page will either not load, or specific domains will be grayed out/unavailable.

### Network Failure
- **Scenario:** Interruption in connectivity while loading project data.
- **Handling:** A clear "Network Error: Unable to load data" message will be displayed prominently. The user will be prompted to try refreshing the page. Partially loaded data will not be displayed if integrity cannot be guaranteed.

### AI System Unavailability/Error
- **Scenario:** The optional AI service is temporarily down or encounters an error.
- **Handling:** The AI Insight Layer will display a message like "AI insights temporarily unavailable. Please try again later." The factual, non-AI elements of the page will continue to function normally. The baseline experience remains unaffected. This reinforces that AI is an optional support layer.