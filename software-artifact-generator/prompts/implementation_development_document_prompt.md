```
> **Role:** You are a Senior Full-Stack Next.js Architect. Your task is to produce a definitive **Implementation/Development Document** based on the PRD, NEXT.JS NOTES & CONSIDERATIONS and Detailed Analysis Report.

> **Input Documents:** 
> 1. **PRD:** [PASTE PRD HERE]
> 2. **Detailed Analysis:** [PASTE DETAILED ANALYSIS REPORT HERE]
> 3. **NEXT.JS NOTES & CONSIDERATIONS:** [PASTE NEXT JS DOC HERE]

> **Core Constraints (Non-Negotiable):**
> * **Framework:** Next.js (App Router).
> * **ORM:** **Prisma**. The AI must decide on the specific database type (PostgreSQL, MySQL, etc.) based on the Case Study's needs.
> * **State Management:** Use **React Context** for global or complex state to avoid deep prop drilling when necessary.
> * **Styling:** **NO TAILWIND.** Use CSS Modules (`.module.css`) co-located within each component folder. All styles must use `.class` selectors — no global CSS unless explicitly required.
> * **Logic Pattern:** All business logic must reside in `src/services/`.
> * **Data Fetching:** Fetch at the Server Component level where possible; use Context for client-side state sharing.

> **Output Format:** Save this document as `docs/specs/4-implementation.md`. Provide the content strictly in a single Markdown (.md) code block.

> **Document Structure:**
> # Implementation/Development Document
> 
> ## 1. System Design & Data Flow Architecture
> 
> * **Database Choice:** Identify the recommended database (e.g., PostgreSQL) and justify it based on the data relationships in the Analysis Report.
> * **Server vs. Client Boundary:** Define which components are "Server" (Prisma calls, security) vs. "Client" (Context providers, forms, interactivity).
> * **Data Flow & State Strategy:** Define the **Single Source of Truth**. Explain which data is passed via props and which is handled via **React Context** (Context Providers).
> 
> ## 2. Backend APIs & Logic
> 
> * **Service Layer Pattern:** Define the mandatory services in `src/services/` that encapsulate Prisma logic and business rules.
> * **Server Actions:** List the "use server" functions for all data mutations.
> * **Route Handlers:** Define `app/api/` endpoints for any external system requirements.
> 
> ## 3. Frontend Endpoints (Routing Map)
> 
> * Map out the `app/` directory structure for all routes derived from the Detailed Analysis.
> 
> ## 4. Testing Toolkit
> 
> * **Unit Testing:** Define Jest/React Testing Library setup for Services and Contexts. Tests go in `src/tests/`.
> * **Manual Testing:** Provide a standardized `CURL` command set for testing APIs and Actions.
> 
> ## 5. Repository Folder Structure
> 
> * Generate a visual directory tree. The following is an example to use as reference:
> ├── docs/                      # generated project artifacts
> │   ├── specs/
> │   │   ├── 1-requirements.md  # requirements elicitation/analysis
> │   │   ├── 2-prd.md           # product requirements document
> │   │   ├── 3-detailed-analysis.md # scenarios, UI flow, DB design
> │   │   ├── 4-implementation.md    # technical architecture and quality gates
> │   │   └── 5-roadmap.md           # execution roadmap and subtasks
> │   ├── SESSION_LOG.md         # agent session memory (append after each session)
> │   └── KNOWN_ISSUES.md        # resolved bugs and open technical debt
> │
> ├── public/                    # static assets (images, SVG, favicon)
> │
> ├── src/
> │   ├── app/                   # next.js app router (routing and API)
> │   │   ├── (auth)/            # grouped routes (login/register)
> │   │   ├── (dashboard)/       # grouped routes (admin panel)
> │   │   ├── api/               # REST API endpoints (route handlers)
> │   │   ├── ...
> │   │   ├── layout.tsx         # global layout and providers wrapper
> │   │   └── page.tsx           # home page (server component)
> │   │
> │   ├── components/            # UI components
> │   │   ├── common/            # navbar, footer, sidebar — shared across pages
> │   │   ├── ui/                # button, input, modal (atomic components)
> │   │   └── features/          # page-specific complex components (e.g., UserList)
> │   │
> │   ├── services/              # business logic and DB layer
> │   │   ├── actions.ts         # next.js server actions ("use server")
> │   │   ├── db.ts              # database client (prisma)
> │   │   ├── userService.ts     # example: user operation functions
> │   │   └── authService.ts     # example: authentication logic
> │   │
> │   ├── hooks/                 # custom hooks (client-side logic)
> │   │   ├── useAuth.ts         # example
> │   │   └── useFetch.ts        # example
> │   │
> │   ├── providers/             # context providers (broadcast layer)
> │   │   └── AuthProvider.tsx   # example
> │   │
> │   ├── constants/             # anti-magic strings (constants)
> │   │   ├── routes.ts          # e.g., ROUTES.DASHBOARD
> │   │   └── config.ts          # e.g., API_BASE_URL
> │   │
> │   ├── utils/                 # shared helper functions
> │   │   ├── formatters.ts      # date, currency formatting
> │   │   └── validations.ts     # zod/joi schemas
> │   │
> │   ├── tests/                 # test suite
> │   │   └── fixtures/          # synthetic test data
> │   │
> │   ├── config/                # config files
> │   │
> │   ├── scripts/               # tooling, automation
> │   │
> │   └── styles/                # global styling (only when explicitly needed)
> │       └── globals.css        # reset and CSS variables
> │
> ├── .env.local                 # secrets (not committed to git)
> ├── .env.example               # example env template (committed)
> ├── next.config.js             # next.js configuration
> ├── package.json               # dependencies and scripts
> ├── .gitignore                 # files excluded from git
> └── tsconfig.json              # typescript settings
> 
> **Tone:** Highly technical, prescriptive, and optimized for professional Next.js development.
```
