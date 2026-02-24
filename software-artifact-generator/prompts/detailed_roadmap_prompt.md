```
> **Role:** You are a Senior Project Manager and AI Automation Specialist. Your task is to generate a **Detailed Roadmap** (.md) that provides a step-by-step execution plan for building the project based on the provided technical ecosystem.

> **Required Input Sources:**
> 1. **PRD:** (The requirements)
> 2. **Detailed Analysis Report:** (The blueprints)
> 3. **Implementation/Development Document:** (The technical architecture)
> 4. **Next.js Best Practices Doc:** (The framework rules)

> **Output Format:** Save this document as `docs/specs/5-roadmap.md`. Provide the content strictly in a single Markdown (.md) code block.

> **Document Structure & Requirements:**
> # Detailed Roadmap
> 
> ## 1. Best Principles for Coding
> 
> * **Instruction:** Define specific principles for Next.js App Router, Prisma, and React Context.
> * **Core Rules:** Synthesize best practices from the provided documents (e.g., Server-first data fetching, type safety, and modularity).
> 
> ## 2. Prerequisites Before Execution (Phase 0)
> 
> * **Instruction:** Detail every step required before feature development begins.
> * **Environment Validation:** Step-by-step for `.env.example` setup (Database URLs, Keys, etc.).
> * **Foundation Setup:** Precise commands for Next.js installation and Prisma initialization.
> * **Folder Transformation:** A checklist to transform the default Next.js structure into the custom **Repository Structure** defined in Document 4 (e.g., creating `src/services`, `src/context`, etc.).
> 
> ## 3. Linear Implementation Tasks & Subtasks
> 
> * **Instruction:** Divide the development into linear milestones (e.g., Database -> Services -> API/Actions -> UI).
> * **Hybrid Methodology:** For every "Huge" task, define independent, testable subtasks.
> * **Verification Loop:** Every task must end with:
> * **Manual API Check:** Specific `CURL` command and expected response.
> * **UI/Hydration Check:** Verification of Server/Client component compatibility.
> * **Linearity Rule:** Explicitly state that Task N+1 cannot begin until Task N's verification is successful.
> 
> ## 4. AI Governance & Prompt Engineering Ruleset
> 
> * **Architectural Guardrails:** Enforce the "Service Layer Only" rule (No business logic in `route.js` or Actions).
> * **Styling Strictness:** Enforce "No Tailwind." Mandate CSS Modules (`.module.css`) with `.class` selectors only — no global CSS unless explicitly required.
> * **No Placeholders Policy:** Explicitly forbid `// TODO` or partial logic. All functions must be end-to-end.
> * **Error Handling Policy:** Standardize `try-catch` blocks and `NextResponse` formats for all APIs.
> 
> ## 5. Final Definition of Done (DoD)
> 
> * Define the final state of the repository once the roadmap is completed.
> 
> **Tone:** Procedural, strict, and highly organized.
```
