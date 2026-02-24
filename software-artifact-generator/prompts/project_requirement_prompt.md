```
**Role:** You are a Lead Product Manager and Systems Architect. Your task is to generate a professional **PRD (Product Requirements Document)** by building upon the "Requirements Elicitation/Analysis Document" and the raw case study.
**Output Format:** Save this document as `docs/specs/2-prd.md`. Provide the content strictly within a single Markdown (.md) code block.

**Requirements Elicitation/Analysis Document Content:** """[PASTE MD FILE HERE]"""
**Case Study Context:** """[PASTE MD FILE / CASE STUDY HERE]"""

**Document Structure & Instructions:**

# PRD Document

## 1. Functional Requirements
  * **Template:** "The system should [action] when [condition/trigger] user [interaction/role]."
  * **Instruction:** Derive these strictly from the Elicitation document and case study. Focus on the core mechanics required to satisfy the business goals.
## 2. Non-functional Requirements (The "Right Fit")
  * **Instruction:** Calibrate these to match the specific needs of the case—neither over-engineering nor under-delivering.
  * **Usability:** (UI/UX standards based on the target users)
  * **Reliability:** (Uptime, error handling, and data integrity)
  * **Performance:** (Response times, latency, and throughput)
  * **Scalability:** (Capacity for growth and resource management)
## 3. User Stories
  * **Instruction:** First, identify the key **Personas** (e.g., Admin, Customer, Guest) from the text.
  * **Format:** "As a [Persona], I want to [Action], so that [Value/Benefit]."
  * Generate enough stories to cover all Functional Requirements.
## 4. Implementation Constraints
  * **Instruction:** List only specific technical/implementation constraints explicitly mentioned in the input. **If no constraints are explicitly stated, leave this section empty.**
## 5. Scope: High-Level System Architecture
  * **Instruction:** Describe the system’s primary components and their relationships.
  * **Format:** Use a text-based hierarchy or flow (e.g., Frontend -> API Gateway -> Backend Services -> Database) followed by a brief bulleted description of each core module.

**Tone:** Precise, logical, and engineering-focused.
```
