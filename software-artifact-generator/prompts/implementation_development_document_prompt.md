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
> * **Styling:** **NO TAILWIND.** Use CSS Modules (`.module.css`) located within the component folders.
> * **Logic Pattern:** All business logic must reside in `src/services/`.
> * **Data Fetching:** Fetch at the Server Component level where possible; use Context for client-side state sharing.

> **Output Format:** Provide the content strictly in a single Markdown (.md) code block.

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
> * **Unit Testing:** Define Jest/React Testing Library setup for Services and Contexts.
> * **Manual Testing:** Provide a standardized `CURL` command set for testing APIs and Actions.
> 
> ## 5. Repository Folder Structure
> 
> * Generate a visual directory tree, the following one is an example that you can get inspired from:
> ├── docs/                      # 💎 Sizin 5 Önemli Dokümanınız
> │   ├── 1-requirements.md      # Gereksinim analizi
> │   ├── 2-prd.md               # Ürün gereksinim belgesi
> │   ├── 3-detailed-analysis.md # Senaryolar, UI Akışı, DB Tasarımı
> │   ├── 4-implementation.md    # Teknik mimari ve kalite kapıları
> │   └── 5-roadmap.md           # Yol haritası ve subtaskler
> │
> ├── public/                    # Statik varlıklar (Resimler, SVG, Favicon)
> │
> ├── src/
> │   ├── app/                   # 🚀 NEXT.JS APP ROUTER (Routing & API)
> │   │   ├── (auth)/            # Gruplanmış rotalar (Login/Register)
> │   │   ├── (dashboard)/       # Gruplanmış rotalar (Admin paneli)
> │   │   ├── api/               # REST API Endpoints (Route Handlers)
> │   │   ├── ...
> │   │   ├── layout.tsx         # Global layout & Providers sarmalayıcı
> │   │   └── page.tsx           # Ana sayfa (Server Component)
> │   │
> │   ├── components/            # 🧱 UI BİLEŞENLERİ
> │   │   ├── common/            # Navbar, Footer, Sidebar gibi her yerde olanlar
> │   │   ├── ui/                # Button, Input, Modal (Atomik bileşenler)
> │   │   └── features/          # Sayfaya özel karmaşık bileşenler (Örn: UserList)
> │   │
> │   ├── services/              # 🧠 BUSINESS LOGIC & DB (Arka Ofis)
> │   │   ├── actions.ts         # Next.js Server Actions ("use server")
> │   │   ├── db.ts              # Database Client (Prisma/Drizzle)
> │   │   ├── userService.ts     # ÖRNEK: Kullanıcı işlemlerini yürüten saf fonksiyonlar
> │   │   └── authService.ts     # ÖRNEK: Yetkilendirme mantığı
> │   │
> │   ├── hooks/                 # 🎣 CUSTOM HOOKS (Client-side logic)
> │   │   ├── useAuth.ts         # ÖRNEK
> │   │   └── useFetch.ts.       # ÖRNEK
> │   │
> │   ├── providers/             # 📡 CONTEXT PROVIDERS (Broadcast layer)
> │   │   ├── AuthProvider.tsx   # ÖRNEK
> │   │
> │   ├── constants/             # 🏷️ "ANTI-MAGIC" STRINGS (Sabitler)
> │   │   ├── routes.ts          # ROUTES.DASHBOARD gibi tanımlar
> │   │   └── config.ts          # API_BASE_URL vb.
> │   │
> │   ├── utils/                 # 🛠️ HELPERS (Saf fonksiyonlar)
> │   │   ├── formatters.ts      # Tarih, para birimi formatlama
> │   │   └── validations.ts     # Zod/Joi şemaları
> │   │
> │   └── styles/                # 🎨 GLOBAL STYLING
> │       ├── globals.css        # Reset & CSS Variables
> │
> ├── .env.local                 # Hassas veriler (Git'e eklenmez)
> ├── .env.example               # Örnek olarak doldurulabilecek hassas veriler (Git'e eklenmez).
> ├── next.config.js             # Next.js konfigürasyonu
> ├── package.json               # Bağımlılıklar ve scriptler
> ├── .gitignore                 # NEXT JS Konfigürasyonunda gite gitmesini istemediğimiz şeyler
> └── tsconfig.json              # TypeScript ayarları
> 
> **Tone:** Highly technical, prescriptive, and optimized for professional Next.js development.
```
