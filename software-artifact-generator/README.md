This folder facilitates the creation of software artifacts. Here is the intended use:

1. When starting a project from scratch you need LLMs and coding agents by your side.

   * These agents need context about your project. They need static files to guide them through coding as your project's personal assistant.
   * The artifacts that agents need include:
     * Requirements Elicitation/Analysis
     * Project Requirements Document (PRD)
     * Detailed Analysis Report
     * Implementation/Development Document
     * Detailed Roadmap (for execution)

2. These artifacts are generated sequentially in the order above. Start with creating the Requirements Elicitation document.

   * Feed the LLM with all the context you currently have: your goal, product description, customers, and any other relevant business and software information.

3. Feed all this data in the following placeholder for the first prompt:

   * Case Study Input: [PASTE CASE STUDY TEXT OR DATA HERE]

4. The first prompt is critical for output quality. Take your time, clearly explain what you're looking for in this software.

5. Execute the remaining prompts one by one, giving the previously generated `.md` files as context. Drag and drop those `.md` files and let the prompt execute.

6. All generated artifacts are saved to `docs/specs/` with the following naming convention:
   * `docs/specs/1-requirements.md`
   * `docs/specs/2-prd.md`
   * `docs/specs/3-detailed-analysis.md`
   * `docs/specs/4-implementation.md`
   * `docs/specs/5-roadmap.md`

7. Once all 5 artifacts are generated, copy the last prompt ("LAST EXECUTION PROMPT") and provide all the generated `.md` documents from `docs/specs/` as context. The agent will plan and build the application from scratch.

   * It's advised to use the most intelligent agent available while running the last execution prompt.

**Important Note 1:** The prompts are designed specifically for Next.js projects. If your current tech stack doesn't include Next.js, adjust the prompts accordingly (keeping the content same but tailored for another type of tech stack).

**Important Note 2:** The "design.md" file within this folder is for the BentoUI design, a minimal but modern design used in UIs such as Gemini's, ChatGPT's, etc. If you're planning to use another design, delete this document before executing this workflow or make sure it's not used in context.

**Important Note 3:** Review the content of the prompts and understand them deeply before running any. If you see any conflict of interest, adjust according to your needs.
