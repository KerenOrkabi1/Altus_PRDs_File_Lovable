# Project Overview Masterplan

## 30-Second Elevator Pitch

Project Overview provides Project Managers and PMO users with a calm, factual, high-level landing page within Altus PPM. This new default tab consolidates existing project data to offer a trustworthy decision-support experience, enabling users to quickly assess project health, detect emerging drift, and determine necessary actions. With an optional AI layer for enhanced interpretation and next-best action suggestions, Project Overview empowers users to efficiently manage projects while retaining full human control.

## Problem Statement + Why Now

Project Managers and PMO users struggle with fragmented understanding of project health, requiring them to synthesize information from various signals to confirm project status, identify early drift, and decide on next steps. This fragmentation leads to inefficiencies, delayed interventions, and increased risk. The current Altus PPM experience lacks a consolidated, high-level view that quickly conveys critical project status. There is a pressing need for a unified, decision-support experience that leverages existing data to provide clarity and guidance, particularly as demands for proactive project management and data-driven insights grow. The rise of AI capabilities also presents an opportunity to augment human decision-making without replacing it, making this the opportune moment to introduce such a feature that can evolve with technological advancements.

## Target Audience + Jobs-to-be-done

### 1. Project Manager
*   **Job-to-be-done:** Quickly check project health and confirm the project's direction. Identify areas needing attention and navigate directly to them for investigation, confirmation, or updates.

### 2. PMO User
*   **Job-to-be-done:** Review project health at a high level. Identify projects that may require early intervention. Understand potential drivers of drift and confidently support governance and decision-making for a portfolio of projects.

### 3. Executive Stakeholder (Indirect)
*   **Job-to-be-done:** Gain confidence that project health is being proactively managed and that risks are being monitored. Rely on the Project Manager/PMO for clear, data-backed updates on project status.

## Core Features

### 1. Unified Executive Summary
*   **Description:** A prominent section providing a concise, factual overview of the project's health, including forecast visibility, the last updated status, and a clear primary next action when intervention is required.
*   **Acceptance Criteria:**
    *   Displays current project status (e.g., On Track, At Risk, Critical).
    *   Includes a clear forecast (e.g., "Forecast Green" or "Forecast Red").
    *   Shows the exact ISO-8601 timestamp of the last data refresh.
    *   When action is needed, presents one unambiguous "Primary Next Action" with a navigable path.
    *   Remains factual and concise, acting as a quick digest.

### 2. Core Project Domains (Always Visible)
*   **Description:** Dedicated sections for Cost, Schedule, Scope, and Resources, providing key metrics, status indicators, and drill-down capabilities. These domains are always visible and serve as the foundation of project health assessment.
*   **Acceptance Criteria:**
    *   Each domain prominently displays its current health status (e.g., Green, Yellow, Red).
    *   Provides key summary metrics relevant to the domain (e.g., for Cost: variance, remaining budget; for Schedule: completion %;, due date, forecast).
    *   Offers a clear path to drill down into the respective detailed area of Altus PPM for further investigation.
    *   Visually consistent presentation across all core domains.

### 3. Conditional Project Domains (Reveal on Signal)
*   **Description:** Sections for Risks, Issues, Dependencies, and Changes that only appear when there is a relevant problem, issue, or drift signal detected within those areas, minimizing clutter when no action is needed.
*   **Acceptance Criteria:**
    *   Each conditional domain appears only when its status is not "Green" or "On Track" (e.g., when a "Red" risk is present or a "Yellow" issue is active).
    *   When visible, each domain displays its current health status and a summary of the most critical item.
    *   Provides a direct navigation link to the detailed section within Altus PPM for the specific domain.
    *   A "Show all domains" option is available to reveal all conditional domains regardless of their status.

### 4. Optional AI Insight Layer
*   **Description:** A distinct, opt-in section that leverages AI to provide deeper interpretation, anticipate likely drift, simulate outcomes, and suggest next-best actions. This layer is visually subordinate to factual content and emphasizes human oversight.
*   **Acceptance Criteria:**
    *   Clearly labeled as an "AI Insight" section.
    *   Includes clear trust signals: "based on latest available project data," "confidence level" (e.g., high, medium, low), "source signals used" (e.g., Schedule Slippage, Resource Overload), and "AI suggests, human decides."
    *   Provides descriptive insights (e.g., "Schedule likely to slip due to critical path delays").
    *   Offers agentic support (e.g., "Suggests drafting an email to resource manager," "Simulate impact of re-prioritizing tasks").
    *   All agentic suggestions require explicit human approval; no automatic actions are taken by AI.
    *   Visually distinguishable from factual content, adhering to prescribed design constraints.

### 5. Unified Diagnostic + Drill-down Section
*   **Description:** A consolidated area that allows users to quickly understand the drivers of project issues across both core and conditional domains and navigate to the precise location for resolution or further detail.
*   **Acceptance Criteria:**
    *   Highlights trends or critical issues within each visible domain.
    *   For each issue, provides a direct "drill-down" link to the relevant page in Altus PPM (e.g., to the Task list, Risk register, Resource planner).
    *   The user experience guides the Project Manager to the exact context needed for follow-up.

## Data Model Overview

### Entities:
*   **Project:**
    *   `ProjectID (PK)`
    *   `ProjectName`
    *   `ProjectDescription`
    *   `ProjectStatus (e.g., On Track, At Risk, Critical)`
    *   `LastUpdated (ISO-8601 Timestamp)`
    *   `OverallForecast (e.g., Green, Yellow, Red)`
    *   `PrimaryNextActionDescription`
    *   `PrimaryNextActionNavigationLink`

*   **CostData:**
    *   `CostID (PK)`
    *   `ProjectID (FK)`
    *   `Budget`
    *   `ActualSpend`
    *   `Variance`
    *   `CostStatus (e.g., Green, Yellow, Red)`
    *   `CostForecast`
    *   `DrillDownLink`

*   **ScheduleData:**
    *   `ScheduleID (PK)`
    *   `ProjectID (FK)`
    *   `PlannedEndDate`
    *   `ForecastEndDate`
    *   `CompletionPercentage`
    *   `ScheduleStatus (e.g., Green, Yellow, Red)`
    *   `ScheduleForecast`
    *   `DrillDownLink`

*   **ScopeData:**
    *   `ScopeID (PK)`
    *   `ProjectID (FK)`
    *   `BaselineScope`
    *   `CurrentScope`
    *   `ScopeChangeCount`
    *   `ScopeStatus (e.g., Green, Yellow, Red)`
    *   `DrillDownLink`

*   **ResourceData:**
    *   `ResourceID (PK)`
    *   `ProjectID (FK)`
    *   `AllocatedResources`
    *   `UtilizedResources`
    *   `ResourceConflictsDetected`
    *   `ResourceStatus (e.g., Green, Yellow, Red)`
    *   `DrillDownLink`

*   **RiskData:**
    *   `RiskID (PK)`
    *   `ProjectID (FK)`
    *   `RiskCount`
    *   `CriticalRiskCount`
    *   `RiskStatus (e.g., Green, Yellow, Red)`
    *   `DrillDownLink`

*   **IssueData:**
    *   `IssueID (PK)`
    *   `ProjectID (FK)`
    *   `IssueCount`
    *   `OpenIssueCount`
    *   `IssueStatus (e.g., Green, Yellow, Red)`
    *   `DrillDownLink`

*   **DependencyData:**
    *   `DependencyID (PK)`
    *   `ProjectID (FK)`
    *   `DependencyCount`
    *   `BrokenDependencyCount`
    *   `DependencyStatus (e.g., Green, Yellow, Red)`
    *   `DrillDownLink`

*   **ChangeData:**
    *   `ChangeID (PK)`
    *   `ProjectID (FK)`
    *   `ChangeRequestCount`
    *   `PendingApprovalCount`
    *   `ChangeStatus (e.g., Green, Yellow, Red)`
    *   `DrillDownLink`

*   **AIInsightData:**
    *   `AIInsightID (PK)`
    *   `ProjectID (FK)`
    *   `InsightText`
    *   `ConfidenceLevel`
    *   `SourceSignalsUsed`
    *   `SuggestedAction`
    *   `SimulationOutcome`
    *   `ApprovalStatus`

### Relationships:
*   One `Project` has many `CostData`, `ScheduleData`, `ScopeData`, `ResourceData`, `RiskData`, `IssueData`, `DependencyData`, `ChangeData`, and `AIInsightData` records.

## Permissions/Roles Overview

*   **Project Manager:**
    *   **View:** All project data and AI insights for projects they manage or have been granted access to.
    *   **Interact:** Approve/decline AI-suggested actions; navigate to drill-down links to update project data.

*   **PMO User:**
    *   **View:** All project data and AI insights for all projects within their purview.
    *   **Interact:** Approve/decline AI-suggested actions (with appropriate permissions); navigate to drill-down links for review and governance.

*   **Read-Only User:**
    *   **View:** All project data and AI insights for projects they have been granted access to.
    *   **Interact:** Navigate to drill-down links for read-only understanding; cannot approve/decline AI-suggested actions or modify project data.

*   **System Integrator/Admin:**
    *   **View:** All project data and AI insights.
    *   **Interact:** Configure data sources, AI models, and overall system settings. Manage user roles and permissions.

## Non-functional Requirements

### Performance:
*   **Page Load Time:** Initial page load for the Overview tab must complete within 2 seconds for projects with up to 10,000 underlying data points (e.g., tasks, risks, issues).
*   **Data Refresh:** Automated data refresh for "Last Updated Status" must complete within 1 second of the source system update.
*   **AI Insight Generation:** AI insights must be generated and displayed within 3 seconds of the user opting-in or opening the page (if opt-in is already active).

### Reliability:
*   **Data Consistency:** Project data displayed on the Overview page must be consistent with the underlying Altus PPM data sources with a negligible delay.
*   **System Uptime:** The Overview page, as part of Altus PPM, must adhere to the existing Altus uptime SLA of 99.9%.
*   **Error Handling:** Robust error handling mechanisms must be in place to gracefully manage data source unavailability or AI service errors, displaying informative messages to the user without crashing the application.

## Security & Privacy Considerations

*   **Data Access Control:** All data displayed on the Overview page must respect existing Altus PPM role-based access control (RBAC) and permissions. Users must only see data they are authorized to view.
*   **Data Encryption:** All data, both in transit and at rest, must be encrypted according to Altus PPM's security standards.
*   **AI Data Usage:** User data used by the AI layer must be clearly communicated to users. No personally identifiable information (PII) or sensitive project details will be used by the AI model without explicit consent and anonymization where appropriate. AI model training will adhere to strict data governance policies.
*   **Audit Trails:** All AI-suggested actions, especially agentic ones, and user responses (approve/decline) must be logged for audit purposes.
*   **Compliance:** Adherence to relevant industry standards and regulations (e.g., GDPR, CCPA) for data privacy and security.

## Risks + Mitigations

### 1. Data Latency and Consistency
*   **Risk:** The Overview page relies on multiple existing Altus PPM data sources. Inconsistent or delayed data updates from these sources could lead to the Overview page displaying stale or inaccurate information, eroding user trust.
*   **Mitigation:** Implement a robust data ingestion and synchronization pipeline with clear SLAs for data freshness. Develop real-time monitoring and alerting for data discrepancies. Design the "Last Updated" timestamp prominently to manage user expectations and provide transparency. Explore event-driven architecture for immediate data updates.

### 2. AI Trust and Adoption
*   **Risk:** Users may be hesitant to trust or adopt AI-generated insights, especially if they are perceived as inaccurate, unhelpful, or lacking transparency. This could lead to low feature utilization.
*   **Mitigation:** Prioritize transparency by clearly displaying confidence levels, source signals, and the explicit "AI suggests, human decides" disclaimer. Offer a clear opt-in/opt-out mechanism. Conduct extensive user testing with target audiences to refine AI output and ensure its value. Start with descriptive AI and gradually introduce agentic features as trust builds. Provide clear in-product education on AI capabilities and limitations.

### 3. Performance Scalability with Large Projects/Portfolios
*   **Risk:** As projects grow in complexity or as PMO users view overviews for large portfolios, the performance of data aggregation and rendering could degrade, leading to slow load times or unresponsive UI.
*   **Mitigation:** Implement efficient data indexing and caching strategies. Optimize database queries for summary data. Utilize incremental data loading and virtualization for large data sets where applicable. Conduct rigorous performance testing with simulated large projects and portfolios. Design the UI to prioritize essential information and defer less critical data loading.

## Future Expansion Ideas

*   **Customizable Dashboards:** Allow users to personalize the layout and content of their Overview page, selecting different metrics or conditional domains to display.
*   **Portfolio Overview:** Extend the concept to a higher-level portfolio view, summarizing health across multiple projects for PMO and executive users.
*   **Predictive Analytics Module:** Enhance AI capabilities beyond anticipated drift to include more advanced predictive modeling for various project outcomes.
*   **"What If" Scenarios:** Integrate more sophisticated simulation capabilities, allowing users to model the impact of different decisions on project health.
*   **Integration with Collaboration Tools:** Provide AI-suggested actions that can directly integrate with tools like Microsoft Teams for drafting communications or scheduling meetings, pending explicit user approval.
*   **Quality Domain:** Introduce a dedicated "Quality" domain, if user feedback indicates a strong need, to track quality metrics and potential issues.
*   **Historical Trends and Benchmarking:** Add features to view historical project performance and benchmark against similar projects or industry standards.