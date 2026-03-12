# Design Specification: Altus Project Overview

## Emotional Thesis Statement
Users should feel calm, informed, and in control. The experience should convey trustworthiness and efficiency, empowering users to make confident decisions quickly and intuitively. When action is needed, the page should guide them with clarity and precision, fostering a sense of capability rather than urgency or panic.

## Typography System

Given the use of Fluent UI 9, we will primarily leverage its typography scale and semantic assignments. Customizations will be minimal to maintain consistency.

*   **H1 (Page Title):** Fluent UI "Display" - 48px, Semibold
*   **H2 (Section Header):** Fluent UI "Large Title" - 28px, Semibold
*   **H3 (Card Title / Sub-section Header):** Fluent UI "Title" - 20px, Semibold
*   **H4 (Domain Header / Important Label):** Fluent UI "Subtitle" - 16px, Semibold
*   **Body (Paragraphs, main content):** Fluent UI "Body" - 14px, Regular
*   **Caption (Small text, metadata, AI trust signals):** Fluent UI "Caption" - 12px, Regular

## Color System

We will utilize Fluent UI's semantic color tokens to ensure consistency and maintain accessibility. The focus is on clarity and visual hierarchy, aligning with the existing Altus product look and feel.

*   **Primary Accent:** Fluent UI `colorBrandBackground` (e.g., for active tabs, primary buttons) - conveys primary actions and highlights key information.
*   **Secondary Accent:** Fluent UI `colorNeutralStroke1` (e.g., for secondary buttons, borders) - provides visual separation without overpowering.
*   **Backgrounds:** 
    *   **Page Background:** Fluent UI `colorNeutralBackground1` - provides a clean, neutral canvas.
    *   **Card Background:** Fluent UI `colorNeutralBackground2` - subtly distinguishes content blocks.
*   **Text:** 
    *   **Primary Text:** Fluent UI `colorNeutralForeground1` - for all main body text and labels.
    *   **Secondary Text/Subtle:** Fluent UI `colorNeutralForeground2` - for less critical information, captions, and secondary labels.
    *   **Success:** Fluent UI `colorPaletteGreenForeground1` - for positive status indicators (e.g., "On Track").
    *   **Warning:** Fluent UI `colorPaletteYellowForeground1` - for caution or emerging issues (e.g., "At Risk").
    *   **Critical:** Fluent UI `colorPaletteRedForeground1` - for urgent problems or critical drift (e.g., "Off Track", "Critical Issue").
*   **Borders/Dividers:** Fluent UI `colorNeutralStroke1`, `colorNeutralStroke2` - for separation and structure.
*   **AI Layer:** Subtle background tint using Fluent UI `colorNeutralBackground4`, with AI-specific text using a slightly muted `colorNeutralForeground3` to visually subordinate it.

## Spacing, Radius, and Shadow System Guidelines

Adhere to Fluent UI 9's spacing, radius, and shadow tokens for consistency.

*   **Spacing Hierarchy:** Utilize a consistent 4px grid system derived from Fluent UI spacing tokens (e.g., `spacingHorizontalM`, `spacingVerticalS`).
    *   **Large Gaps:** Between major sections (e.g., Executive Summary, Diagnostic section).
    *   **Medium Gaps:** Between content cards, between domain areas.
    *   **Small Gaps:** Between text elements, icons, and within components.
*   **Border Radius:** Use Fluent UI `borderRadiusMedium` for most interactive elements and cards to maintain a soft, approachable aesthetic. No sharp corners.
*   **Shadows:** Employ Fluent UI `shadow2` or `shadow4` for lifted elements like cards or modals, providing subtle depth and hierarchy without being distracting. Shadows should be minimal and used purposefully to indicate interactive states or elevation.

## Component Guidelines

All components will primarily leverage available Fluent UI 9 components, ensuring a unified experience.

*   **Buttons:**
    *   **Primary Buttons:** Fluent UI `PrimaryButton` styled with `colorBrandBackground` for the most important actions (e.g., "View Details").
    *   **Secondary Buttons:** Fluent UI `DefaultButton` for less critical actions (e.g., "Show all domains").
    *   **Tertiary/Subtle Buttons:** Fluent UI `SubtleButton` for contextual actions or within tables/lists.
    *   All buttons will have clear hover/focus states consistent with Fluent UI.
*   **Cards:** Use Fluent UI `Card` component for content areas like Executive Summary, Domain views, and AI Insight Layer. Cards should have `borderRadiusMedium` and a subtle shadow (`shadow2`) to distinguish them as content blocks. They will enclose related information and support clear internal hierarchy.
*   **Inputs:** Utilize standard Fluent UI `Input` and `Dropdown` components for any filtering or input needs (though not a primary focus for V1). Ensure clear labels and validation states.
*   **Tables:** Leverage Fluent UI `Table` component for any structured data presentation within a domain. Ensure readability with clear headers, adequate row height, and visual distinction between rows. Sorting/filtering capabilities should be available where appropriate.
*   **Empty States:** Design clear and helpful empty states for conditional domains when no issues or relevant data are present. These should explain why the domain is not visible and offer guidance if appropriate (e.g., "No risks detected. Well done!").

## Motion Specifications

Motion should be subtle, functional, and aligned with Fluent UI principles to enhance usability without distraction.

*   **Easing:** Primarily Fluent UI's default easing curves (e.g., `curveEasyEase`).
*   **Duration Ranges:**
    *   **Micro-interactions (Hover, focus states):** 100ms - 150ms
    *   **Component Transitions (e.g., opening/closing a panel, revealing hidden sections):** 200ms - 300ms
    *   **Page Transitions (if applicable to navigation):** 300ms - 400ms

## Voice & Tone Examples (Microcopy)

The voice should be professional, factual, direct, and supportive. Avoid jargon or overly technical language where simpler alternatives exist.

*   **Executive Summary:** "Forecast: On Track. Last Updated: [Date/Time]. Next Action: [Clear, concise action]."
*   **Domain Headers:** "Schedule Status", "Cost Health", "Risks ([Number] Critical)"
*   **AI Insight Layer Label:** "AI Insights (Optional)"
*   **AI Trust Signals:**
    *   "Based on the latest available project data."
    *   "Confidence: High (92%)"
    *   "Source signals: Financials, Schedule, Issues Log."
    *   "AI suggests, human decides."
*   **Decision Support:** "AI recommends [Action]. Simulate outcomes?", "Consider [Action] to mitigate [Issue]."
*   **Empty State (Risks):** "No critical risks detected. All looks good here!"
*   **Action Needed Callout:** "Attention needed: Schedule is drifting. Investigate now."
*   **Guidance on next steps:** "Go to [Specific Destination] to update [Information]."

## Accessibility Requirements

Accessibility is paramount and will adhere to WCAG 2.1 AA standards as a minimum.

*   **Color Contrast:** All text and interactive elements will meet minimum contrast ratios (4.5:1 for normal text, 3:1 for large text and UI components) as defined by WCAG. Use Fluent UI's semantic color tokens that are designed for accessibility.
*   **Focus Management:** Clear and visible focus indicators for all interactive elements (buttons, links, form fields, tab stops). Focus order will be logical and intuitive, following the visual flow of the page.
*   **Keyboard Navigation:** The entire page must be fully operable via keyboard alone. All interactive elements must be reachable and actionable using standard keyboard commands (Tab, Shift+Tab, Enter, Spacebar, Arrow keys).
*   **Screen Reader Support:** Provide appropriate ARIA attributes and semantic HTML to ensure screen readers accurately convey the page structure, content, and interactive elements. Each section, heading, and interactive component will have meaningful labels and roles.
*   **Responsive Design:** The page will be designed to be responsive and usable across various screen sizes and orientations, though the primary focus for V1 is a desktop experience within the Altus shell.
*   **Text Scaling:** Ensure text scales gracefully with OS/browser settings without clipping or loss of functionality."