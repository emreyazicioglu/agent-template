This folder is created in to f**acilitate the creation of software artifacts**, here is the intended use:

1. When you're starting a project from scratch you need LLMs and coding agents by your side.

   * These agents have to know about the context and the project you are working with. Therefore they need static files that will guide them through coding by yourside as your project's personal assistant.
   * In order for agents to work better and fully understand the project that you're working on, they need artifacts related to your project. There artifacts include:
     * Requirements Elicitation/Analysis
     * Project Requirements Document (PRD)
     * Detailed Analysis Report
     * Implementation/Development Document
     * Detailed Roadmap (for execution)
2. These artifacts are meant to be generated in a sequence given above. Therefore we should start with creating Requirements Elicitation document.

   * In order to start with this document you have to feed the LLM with all the context that you currently have.
   * If you're planning to start working on a project, you probably have a goal, a description of the product, your customers... and so on. Literally we have to feed all the information that we have about the business and the software that we're planning to build.
3. You'll feed all this data in the following placeholder for the first prompt:

   * Case Study Input: [PASTE CASE STUDY TEXT OR DATA HERE]
4. That's all you need for this workflow to start, however for the quality of your software to be great. The first prompt is very important. So take your time, clearly explain what you're looking for in this software, what you have written as data and paste it in the placeholder part.
5. Then all you need is to execute the rest of the prompts one by one while giving the previous generated .md files (artifacts) as the context, just drag and drop those .md files created and then let the prompt execute.
6. If all goes well, you'll have 5 decent artifacts before you even begin to start coding, but you'll have a perfectly designed context for agent to execute with. Which will cut of all the halucinations that would possible occur along the way.
7. All you have to do at the end is to copy and paste the last prompt called: "LAST EXECUTION PROMPT" while giving all the generated .md documents as the context. Then the agent will plan according to the artifacts and start building the application from scratch.

   * It's advised to use opus 4.6 or the most intelligent agent that the world currently has while running the last execution prompt.

**Important Note 1:** Keep in mind that the prompts are designed specificly for next.js projects, therefore if your current tech stack doesn't include Next.js, you have to adjust the prompts accordingly (keeping the content same but tailored for another type of tech stack)

**Important Note 2:** The "design.md" file within this folder is for the design choice called BentoUI, which is a minimal but a very good looking design that is currently used in modern UIs such as gemini's, chatgpt's etc. It's one of the best designs out there, but in case you're planning to use another type of design, simply delete this document before you execute this workflow or make sure it's not used in context.

**Important Note 3:** You are advised to take a good look at the content of the prompts and understand them deeply before running any. If you see any conflict of interest in those prompts, simply delete or adjust according to your needs. DON'T JUST BLINDLY EXECUTE THEM.

ENJOY!
