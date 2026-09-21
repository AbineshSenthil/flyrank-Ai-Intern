# FlyRank AI Internship Portfolio

Backend engineering assignments and capstone work completed by **Abinesh S** during the
FlyRank AI internship.

This repository contains two independent areas of work:

| Project | Scope | Technologies |
| --- | --- | --- |
| [Backend Engineering Assignments](assignments/) | Nine progressive assignments covering APIs, persistence, authentication, containers, ethical scraping, background jobs, AI integration, PDF reporting, and durable workflows | Python, FastAPI, SQLite, PostgreSQL, Docker, Supabase, Gemini, ReportLab, Next.js, Inngest |
| [CampaignHub Studio Capstone](capstone-social-studio/) | A multi-platform social campaign engine that turns one article into tailored captions and images, then schedules and publishes them through safe fake-platform adapters | TypeScript, React, TanStack Start, Supabase, OpenAI, Redis, Vitest, MCP |

## Backend Engineering Assignments

Each assignment is self-contained and includes its own setup instructions, dependencies,
implementation, and automated tests where applicable.

| Assignment | Topic | Key outcome |
| --- | --- | --- |
| [BE-01](assignments/be-01/) | First API endpoint | FastAPI endpoints and JSON response contracts |
| [BE-02](assignments/be-02/) | Database-backed CRUD | Persistent SQLite task API with SQL operations |
| [BE-03](assignments/be-03/) | Authentication | Supabase JWT authentication and protected routes |
| [BE-04](assignments/be-04/) | Containerized stack | FastAPI and PostgreSQL with Docker Compose |
| [BE-05](assignments/be-05/) | Polite web scraping | Robots-aware, rate-limited catalogue scraper |
| [BE-06](assignments/be-06/) | Background jobs | Persistent and queryable asynchronous job lifecycle |
| [BE-07](assignments/be-07/) | AI API integration | Validated Gemini responses, timeouts, and bounded retries |
| [BE-08](assignments/be-08/) | PDF reporting | Asynchronous SQL aggregation and ReportLab PDF generation |
| [BE-09](assignments/be-09/) | AI decision workflow | Editable YES/NO graph with durable Inngest execution |

See the [assignment index](assignments/README.md) for a compact overview.

## CampaignHub Studio Capstone

[CampaignHub Studio](capstone-social-studio/) transforms a blog article into an Instagram,
X, and LinkedIn campaign. It generates platform-specific captions and exact-size image
variants, supports immediate or scheduled publishing, and exposes the same application use
cases through a standalone Model Context Protocol interface.

The capstone includes:

- Clean Architecture boundaries between domain, application, infrastructure, and interfaces.
- Deterministic idempotency keys and persisted publish-attempt history.
- `429 Retry-After` handling with bounded retries.
- Crash-safe scheduling with expiring worker leases.
- HMAC-verified delivery webhooks.
- AES-256-GCM encryption for stored OAuth tokens.
- Multi-tenant Supabase authentication and row-level security.
- Optional OpenAI caption and image generation with deterministic fallbacks.
- AI usage metering and a configurable spending guard.
- 131 deterministic Vitest tests that require no live database or API credentials.

For architecture, screenshots, environment variables, Docker setup, and the full reviewer
walkthrough, read the [capstone documentation](capstone-social-studio/README.md).

## Repository Structure

```text
flyrank-Ai-Intern/
├── assignments/                 Backend engineering assignments BE-01 to BE-09
├── capstone-social-studio/      CampaignHub Studio capstone application
├── .gitattributes               Cross-platform text and binary file handling
├── .gitignore                   Local dependency, secret, cache, and build exclusions
├── LICENSE                      Repository license
└── README.md                    Portfolio overview
```

## Running an Assignment

Open the assignment's README before running it because dependencies and environment variables
vary by project. A typical Python assignment uses:

```bash
cd assignments/be-02
python -m venv .venv

# Windows PowerShell
.venv\Scripts\Activate.ps1

python -m pip install -r requirements.txt
python -m pytest -q
```

BE-09 is a Node.js project:

```bash
cd assignments/be-09
npm install
npm test
npm run dev
```

## Running the Capstone

CampaignHub Studio recommends Node.js 22 or newer. All paid AI features are optional; the
application has deterministic local fallbacks.

```bash
cd capstone-social-studio
npm install
cp .env.example .env
npm test
npm run dev
```

The application starts at `http://localhost:8080`. Configure your own Supabase project before
using authenticated database features. Never commit the resulting `.env` file.

## Verification

The imported projects were verified before publication:

- 36 Python assignment tests passed across BE-02, BE-03, BE-05, BE-06, BE-07, and BE-08.
- 4 BE-09 workflow tests passed.
- 131 CampaignHub Studio tests passed.
- The CampaignHub Studio production build completed successfully.
- No production credentials or private datasets are committed.

## Author

**Abinesh S**

[GitHub profile](https://github.com/AbineshSenthil)

## License

This repository is available under the [MIT License](LICENSE). The capstone also contains its
own [MIT license](capstone-social-studio/LICENSE).
