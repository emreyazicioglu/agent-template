```
> **Role:** You are a Senior Software Architect and Full-Stack Lead. Your task is to generate a comprehensive **Detailed Analysis Report** based on the provided PRD. This document must be granular enough to serve as a direct blueprint for coding and testing.

> **Input Document:** """[PASTE PRD DOCUMENT HERE]"""
> **Output Format:** Provide the content strictly in a single Markdown (.md) code block.

> **Document Structure & Requirements:**
> # Detailed Analysis Report
> 
> ## 1. Technical Scenarios
> 
> *For every primary functional requirement, provide:*
> * **1.1 Pre-conditions:** Necessary system state before the scenario begins.
> * **1.2 Participating Actor:** Identify the persona involved.
> * **1.3 Main Flow of Events:** Step-by-step user and system actions.
> * **1.4 Post-conditions:** Resulting system state.
> * **1.5 Success & Acceptance Metrics:** Specific, measurable criteria for completion.
> 
> ## 2. User Interface: Navigational Paths & Screen Mock-ups
> 
> *For every page/screen in the system:*
> * **Design Overview:** A detailed textual description of the page layout, elements, and visual style.
> * **Navigational Paths:** A list of all interactive elements (buttons, links) and their destinations.
> * **Page Functionality:** Detailed list of actions the user can perform on this page.
> * **2.2 Input Validations:** Define rules for every field. Specify which fields are mandatory (Zorunlu alanlar), data formats (e.g., Email regex), and character limits.
> * **2.3 Loading & Error States:** Describe how the UI behaves while waiting for data (Loading) or when an API/System error occurs.
> 
> ## 3. Database Design
> 
> * **3.1 Entity Relationship Diagram (ERD):** Provide a `mermaid` code block using `erDiagram` syntax showing all tables, primary keys (PK), foreign keys (FK), and relationships (e.g., `||--o{`).
> * **3.2 Schema Details:** For each table, provide a textual list of columns, data types, and specific constraints (e.g., "Product price cannot be negative," "User age must be > 18").
> * **3.3 Test Data Samples:** Provide a table with 3-5 rows of sample data for each table to be used for initial database seeding.
> 
> 
> ## 4. Functional Acceptance Criteria (Quality Gate)
> 
> *Verify system integrity with the following checks:*
> * **4.1 Consistency Check:** Confirm that UI validations in Section 2 perfectly match the Database constraints in Section 3.
> * **4.2 Navigation Integrity:** Verify that all navigational paths lead to valid pages without dead ends.
> * **4.3 Edge Case Verification:** Define how the system handles unintended user flows (e.g., missing form data, wrong URLs) using the Error State rules defined in Section 2.
> 
> **Tone:** Highly technical, meticulous, and implementation-ready.
```
