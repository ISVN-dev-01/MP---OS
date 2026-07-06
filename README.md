# 🏛️ MP OS — Member of Parliament Operating System

### *An agentic-AI platform that turns a months-long wait for a hearing into a trackable, transparent, minutes-long interaction.*

![React](https://img.shields.io/badge/Frontend-React_18-61DAFB?style=for-the-badge&logo=react&logoColor=white)
![React Native](https://img.shields.io/badge/Mobile-React_Native-61DAFB?style=for-the-badge&logo=react&logoColor=white)
![FastAPI](https://img.shields.io/badge/Backend-FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white)
![Python](https://img.shields.io/badge/Python-3.11+-3776AB?style=for-the-badge&logo=python&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/Database-PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)
![Redis](https://img.shields.io/badge/Cache-Redis-DC382D?style=for-the-badge&logo=redis&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

> **Note on source material:** This README was written from the detailed feature brief provided for the hackathon submission. The linked Figma "Make" prototype is a client-rendered, access-gated file and couldn't be scraped by an automated fetch — if you want the UI screens reflected here too, export the frames as PNGs or share the file in "view" mode and I'll fold them in.

---

## 📌 Table of Contents

1. [Problem Statement](#-problem-statement)
2. [Solution Overview](#-solution-overview)
3. [What Makes This Different](#-what-makes-this-different)
4. [Key Features by Role](#-key-features-by-role)
5. [System Architecture](#-system-architecture)
6. [The Agentic AI Layer](#-the-agentic-ai-layer)
7. [Tech Stack](#-tech-stack)
8. [Project Structure](#-project-structure)
9. [Data Model](#-data-model)
10. [API Overview](#-api-overview)
11. [Slot-Based Appointment Booking](#-slot-based-appointment-booking)
12. [Tokenized Influence System](#-tokenized-influence-system)
13. [Happiness Performance Index (HPI)](#-happiness-performance-index-hpi)
14. [Multilingual Support](#-multilingual-support)
15. [Security & Data Privacy](#-security--data-privacy)
16. [Compliance, Governance & Ethical Considerations](#-compliance-governance--ethical-considerations)
17. [Getting Started](#-getting-started)
18. [Environment Variables](#-environment-variables)
19. [Roadmap](#-roadmap)
20. [Contributing](#-contributing)
21. [Team](#-team)
22. [License](#-license)
23. [Acknowledgements & Prior Art](#-acknowledgements--prior-art)

---

## 🎯 Problem Statement

A citizen with a genuine civic issue — a broken streetlight, a stalled pension, a school with no toilets — has almost no low-friction way to reach their Member of Parliament. In practice they either:

- wait weeks for an in-person appointment slot that's allocated informally and opaquely,
- file a grievance into a system that gives them a ticket number but no real sense of who is acting on it or when, or
- give up, because the round trip of travel, waiting rooms, and follow-up costs more than the problem itself.

On top of this, most citizens are far more comfortable describing a problem in Telugu, Hindi, Tamil, or another regional language than in the English/Hindi-first forms that most e-governance portals default to, and very few people know **which** government body actually owns their issue — Municipal Corporation? PWD? The MP's office? A state department?

At the institutional level, there's also no simple, comparable signal for whether an MP's office is actually *resolving* what citizens raise — versus just receiving and filing it.

**MP OS is built to close all three gaps at once: intake, routing, and accountability — in the citizen's own language, on their own phone.**

---

## 💡 Solution Overview

MP OS is a role-based, multilingual, agentic-AI-powered web and mobile platform. A citizen describes a problem in free text (or voice) in their own language; the platform's agent pipeline classifies it, drafts a properly formatted grievance document, assigns a trackable **Problem ID**, and routes it to the right authority — no queue, no waiting room required for the *filing* step.

The same platform lets citizens book a direct meeting slot with their MP the way they'd book a movie ticket (pick a date, see open slots, confirm), ask a multilingual chatbot which government scheme applies to their situation, and take part in civic engagement — referrals, verified donations, cleanliness/infrastructure reporting — that builds visible on-platform recognition through a transparent **Tokenized Influence** system.

On the other side, MPs get a live dashboard of constituency sentiment, and the CM/party leadership gets a comparable, auditable **Happiness Performance Index (HPI)** across every MP — an objective signal for whether representatives are actually solving people's problems, not just logging them.

---

## 🌟 What Makes This Different

| Existing system | What it does well | What it doesn't do |
|---|---|---|
| **CPGRAMS** (Centralized Public Grievance Redress and Monitoring System, DARPG) | Nationwide grievance intake, unique registration IDs, role-based routing across ministries, and — as of its newer versions — an AI module that auto-flags spam and clusters repeat complaints | No direct link to *your* MP, no appointment booking, no citizen-facing multilingual chatbot, no representative-level accountability score |
| **Local MP office appointment desks** | Personal, high-touch when you get through | Manual, opaque queueing; no tracking; doesn't scale past a few dozen meetings a week |
| **MP OS** | Combines natural-language intake → auto-classification → document generation → routing → direct slot booking → multilingual scheme guidance → a public accountability index, in one citizen-facing app | — |

MP OS isn't trying to replace CPGRAMS; it's the missing citizen-to-representative layer that a system like CPGRAMS doesn't provide, purpose-built around a single MP's constituency and schedule.

---

## ✨ Key Features by Role

### 👤 Citizen (Public User)
- **Problem submission with auto-generated Problem ID** — describe an issue in free text or voice; the agentic AI layer classifies it, drafts a formal grievance document, and routes it to the correct authority.
- **Multilingual agentic chatbot** — "Which scheme covers my situation?" / "Which office handles road repairs?" answered in the citizen's own language.
- **Movie-ticket-style slot booking** — view the MP's live calendar and reserve a meeting slot the way you'd book a cinema seat.
- **Cleanliness & infrastructure reporting** — geo-tagged civic issue reporting, separate from formal grievances.
- **Special requests** — invite the PM to a local event, request facilitation for a corporate meeting, or refer the MP's work to your network.
- **Tokenized Influence** — earn Influence Tokens through verified donations, referrals, and civic participation.
- **Branding & engagement** — selfies, donation showcases, referral leaderboards.

### 🧑‍💼 MP (Admin)
- **Constituency dashboard** — live view of open, in-progress, escalated, and resolved grievances.
- **Happiness Performance Index (HPI)** — a composite, auditable score of constituent satisfaction and responsiveness.
- **Schedule & slot management** — publish available meeting windows for citizen booking.
- **Branding tools** — public profile, achievement highlights, event announcements.

### 🏛️ CM / Party Oversight *(recommended addition — see note below)*
- **Cross-constituency HPI leaderboard** — compare MP performance across the state or party.
- **Aggregate analytics** — resolution rates, sentiment trends, and a public donation-to-token transparency ledger.

> **Design note:** The brief specifies MP (admin) and Citizen roles, and separately says "the CM will measure … by Happiness Index." For that to work as a real RBAC system, the CM/party leadership needs its own role and dashboard, distinct from any single MP's — otherwise there's no cross-MP comparison surface. I've added it as a third role above; treat it as an assumption to confirm, not a locked-in requirement. A fourth role, **Department Officer** (to receive routed grievances and push status updates), is listed under [Roadmap](#-roadmap) since the brief doesn't ask for it directly, but the loop from "routed" to "resolved" needs *someone* on the receiving end eventually.

---

## 🏗️ System Architecture

```mermaid
flowchart TB
    subgraph Clients [Client Layer]
        WEB[React Web App]
        MOB[React Native Mobile App]
    end

    subgraph API [API Layer - FastAPI]
        GATEWAY[REST API Gateway<br/>Auth - Rate Limiting - RBAC]
    end

    subgraph Agentic [Agentic AI Layer]
        INTAKE[Intake Agent]
        CLASSIFY[Classification Agent]
        DOCGEN[Document Generation Agent]
        ROUTE[Routing Agent]
        CHAT[Multilingual Chatbot Agent]
        SCHEME[Scheme Advisor - RAG]
    end

    subgraph Data [Data Layer]
        PG[(PostgreSQL)]
        REDIS[(Redis Cache and Slot Locks)]
        VEC[(Vector Store)]
        S3[(Object Storage)]
    end

    subgraph External [External Services]
        PAY[Payment Gateway]
        NOTIFY[SMS / Email / Push]
        TRANSLATE[Translation Engine - Bhashini]
    end

    WEB --> GATEWAY
    MOB --> GATEWAY
    GATEWAY --> INTAKE
    INTAKE --> CLASSIFY
    CLASSIFY --> DOCGEN
    DOCGEN --> ROUTE
    GATEWAY --> CHAT
    CHAT --> SCHEME
    SCHEME --> VEC
    ROUTE --> PG
    GATEWAY --> PG
    GATEWAY --> REDIS
    GATEWAY --> S3
    GATEWAY --> PAY
    GATEWAY --> NOTIFY
    CHAT --> TRANSLATE
```

**Layer responsibilities**

| Layer | Responsibility |
|---|---|
| Client | React (web) + React Native (mobile) — one shared design system, role-aware routing |
| API Gateway | AuthN/AuthZ, RBAC enforcement, request validation, rate limiting |
| Agentic AI | Classification, document generation, routing, multilingual chat, scheme RAG |
| Data | Transactional data (Postgres), ephemeral locks/cache (Redis), embeddings (vector store), files (object storage) |
| External | Payments, notifications, translation — all pluggable, none hard-coded to a single vendor |

---

## 🤖 The Agentic AI Layer

A single chatbot can answer questions; it can't independently classify a grievance, draft a properly formatted document, *and* route it to the correct authority. MP OS uses a short pipeline of narrow, single-purpose agents with a clear handoff between each step, orchestrated as a state machine (e.g. LangGraph) so a failure at one stage doesn't fail silently:

1. **Intake Agent** — normalizes raw input (typed text, voice-to-text transcript, image captions) and detects the input language.
2. **Classification Agent** — tags the grievance category (infrastructure, sanitation, education, law & order, pension/welfare, etc.) and an urgency level.
3. **Document Generation Agent** — fills a structured grievance template from the classified data, in the format the receiving department expects.
4. **Routing Agent** — matches the document to the correct department/jurisdiction using a rules engine backed by a small RAG lookup over department mandates.
5. **Scheme Advisor Agent** — a separate RAG pipeline over a vector store of government scheme data, used by the chatbot to answer "am I eligible for X" or "which scheme covers Y."
6. **Notification Agent** — pushes status updates back to the citizen (SMS/push) as the Problem ID moves through each stage.

**Submission flow:**

```mermaid
sequenceDiagram
    actor U as Citizen
    participant FE as React Frontend
    participant BE as FastAPI Backend
    participant AI as Agentic AI Pipeline
    participant DB as Database

    U->>FE: Describe problem in own language
    FE->>BE: POST /api/v1/problems
    BE->>AI: Forward raw input
    AI->>AI: Classify category and urgency
    AI->>AI: Generate formal grievance document
    AI->>AI: Determine routing department
    AI->>DB: Persist problem and routing
    DB-->>BE: Problem ID
    BE-->>FE: Problem ID and status
    FE-->>U: Tracking confirmation
    BE-->>U: Status updates via SMS or push
```

**Sample endpoint (FastAPI):**

```python
# app/api/v1/problems.py
from fastapi import APIRouter, Depends
from app.schemas.problem import ProblemCreate, ProblemResponse
from app.services.agent_pipeline import run_intake_pipeline
from app.core.security import get_current_user

router = APIRouter(prefix="/problems", tags=["problems"])

@router.post("/", response_model=ProblemResponse, status_code=201)
async def submit_problem(
    payload: ProblemCreate,
    current_user=Depends(get_current_user),
):
    """
    Accepts a raw citizen complaint, runs it through the agentic pipeline
    (classify -> generate document -> route), and returns a trackable
    Problem ID immediately. Heavy AI steps run as a background task so the
    citizen isn't left waiting on an LLM call.
    """
    result = await run_intake_pipeline(payload, user=current_user)
    return result
```

> Note the last line in the docstring: classification/document-generation can take a few seconds. Return the Problem ID as soon as the record is created, and run the AI steps as a Celery background task that updates status asynchronously — don't block the citizen's confirmation screen on an LLM round-trip.

---

## 🧰 Tech Stack

| Layer | Technology |
|---|---|
| **Frontend (Web)** | React 18, TypeScript, TailwindCSS, React Query, Zustand |
| **Frontend (Mobile)** | React Native (Expo) |
| **Backend** | FastAPI, Python 3.11+, Pydantic v2, SQLAlchemy 2.0 / SQLModel |
| **Async task queue** | Celery + Redis (AI pipeline jobs, notifications, nightly HPI computation) |
| **Agent orchestration** | LangGraph / LangChain |
| **LLM** | Pluggable — Claude API, GPT, or a self-hosted open-source model behind one interface |
| **Multilingual / translation** | [Bhashini](https://bhashini.gov.in) (Digital India's language AI mission) or AI4Bharat IndicTrans2 |
| **RAG / vector store** | pgvector (Postgres extension) or a managed vector DB (Pinecone/Weaviate) |
| **Primary database** | PostgreSQL 15+ |
| **Cache / slot locking** | Redis |
| **Object storage** | AWS S3 or Cloudinary (grievance documents, selfies) |
| **Payments** | Razorpay (UPI, cards, net banking) |
| **Auth** | JWT + OAuth2, optional Aadhaar-based eKYC for identity verification |
| **DevOps** | Docker, Docker Compose, GitHub Actions, Nginx |
| **Monitoring** | Prometheus + Grafana, Sentry |

---

## 📂 Project Structure

```
mp-os/
├── frontend/                      # React web app
│   └── src/
│       ├── components/
│       ├── pages/
│       ├── roles/
│       │   ├── citizen/
│       │   ├── mp-admin/
│       │   └── oversight/
│       ├── hooks/
│       ├── services/               # API clients
│       └── i18n/                   # multilingual translation bundles
├── mobile/                         # React Native (Expo) app, shares services/ logic
├── backend/                        # FastAPI app
│   └── app/
│       ├── api/v1/                 # routers: problems, auth, appointments, tokens, hpi, chatbot
│       ├── agents/                 # intake, classification, document_gen, routing, chatbot, scheme_advisor
│       ├── models/                 # SQLAlchemy models
│       ├── schemas/                # Pydantic schemas
│       ├── services/               # business logic (booking, tokens, hpi calculation)
│       ├── core/                   # config, security, RBAC
│       └── db/                     # session, Alembic migrations
├── docker-compose.yml
├── .env.example
└── README.md
```

---

## 🗄️ Data Model

```mermaid
erDiagram
    USER ||--o{ PROBLEM : submits
    USER ||--o{ APPOINTMENT : books
    USER ||--o{ DONATION : makes
    USER ||--o{ REFERRAL : initiates
    USER ||--o{ TOKEN_LEDGER : owns
    MP ||--o{ APPOINTMENT : hosts
    MP ||--o{ PROBLEM : receives
    MP ||--o{ HPI_SCORE : measured_by

    USER {
        uuid id PK
        string name
        string phone
        string role
        string preferred_language
    }
    PROBLEM {
        string problem_id PK
        uuid user_id FK
        string category
        string status
        string routed_department
        timestamp created_at
    }
    MP {
        uuid id PK
        string constituency
        string party
    }
    APPOINTMENT {
        uuid id PK
        uuid mp_id FK
        uuid user_id FK
        datetime slot_time
        string status
    }
    DONATION {
        uuid id PK
        uuid user_id FK
        decimal amount
        int tokens_earned
    }
    TOKEN_LEDGER {
        uuid id PK
        uuid user_id FK
        int balance
    }
    HPI_SCORE {
        uuid id PK
        uuid mp_id FK
        float resolution_rate
        float satisfaction_score
        float composite_score
        date period
    }
```

---

## 🔌 API Overview

| Method | Endpoint | Description | Role |
|---|---|---|---|
| POST | `/api/v1/auth/login` | OTP-based login, returns JWT | All |
| POST | `/api/v1/problems` | Submit a new problem, returns Problem ID | Citizen |
| GET | `/api/v1/problems/{problem_id}` | Track status of a submitted problem | Citizen |
| GET | `/api/v1/mp/dashboard` | Constituency dashboard data | MP |
| GET | `/api/v1/mp/schedule` | View an MP's available slots | Citizen, MP |
| POST | `/api/v1/appointments/book` | Book a meeting slot | Citizen |
| POST | `/api/v1/chatbot/query` | Ask a scheme / department-routing question | Citizen |
| POST | `/api/v1/donations` | Record a donation and mint tokens | Citizen |
| GET | `/api/v1/tokens/wallet` | View Influence Token balance | Citizen |
| POST | `/api/v1/referrals` | Generate a referral code/link | Citizen |
| GET | `/api/v1/hpi/{mp_id}` | Get an MP's Happiness Performance Index | MP, CM/Oversight |
| GET | `/api/v1/hpi/leaderboard` | Cross-MP HPI leaderboard | CM/Oversight |

Full interactive documentation is auto-generated by FastAPI at `/docs` (Swagger) and `/redoc`.

---

## 🎟️ Slot-Based Appointment Booking

The MP publishes available meeting windows (e.g. 15-minute slots across a working day) exactly like a theatre publishes showtimes. Citizens see a live grid of open/booked slots and reserve one instantly.

**Concurrency safety:** when a citizen selects a slot, the backend places a short-lived Redis lock (e.g. 5 minutes) on that slot ID, so two citizens can't both grab the same window while one is completing confirmation — the same pattern ticketing platforms use to hold a seat during checkout. On confirmation, the lock converts into a permanent row in the `appointments` table; if the hold expires unconfirmed, the slot returns to the available pool.

---

## 🪙 Tokenized Influence System

Citizens earn **Influence Tokens** for:
- ✅ Verified donations to the party welfare/development fund
- ✅ Successful referrals (bringing a new verified citizen onto the platform)
- ✅ Verified civic participation (cleanliness/infra reports that are confirmed and resolved)

Tokens unlock:
- 🏅 Profile badges and leaderboard visibility
- 🎉 Invitations to public events, meet-and-greets, or PM/corporate-meeting facilitation requests
- 📣 Branding features (highlighted selfies, a donor-recognition wall)

> ⚠️ **Design principle:** grievance intake, routing, and resolution SLAs are **never** influenced by token balance. Tokens govern *engagement and recognition* features only, never queue priority for core civic services. This is enforced at the business-logic layer (a separate service from booking/grievance logic reads token balance), not just stated as policy — see [Compliance, Governance & Ethical Considerations](#-compliance-governance--ethical-considerations) for why this separation matters.

---

## 📊 Happiness Performance Index (HPI)

HPI is a composite, periodically recalculated score (0–100) that the CM/party leadership can use to gauge whether an MP's office is actually resolving citizen problems, not just receiving them:

```
HPI = (w1 × Resolution Rate)
    + (w2 × (1 − Normalized Avg. Resolution Time))
    + (w3 × Citizen Satisfaction Score)
    + (w4 × Appointment Responsiveness Rate)
    − (w5 × Repeat-Complaint Rate)
```

| Weight | Component | Data source |
|---|---|---|
| w1 | % of grievances resolved within SLA | `problems` table |
| w2 | Speed of resolution vs. category benchmark | `problems` table |
| w3 | Post-resolution citizen feedback (1–5 rating) | Feedback survey |
| w4 | % of booked appointments honored on time | `appointments` table |
| w5 | % of resolved issues re-reported within 30 days | `problems` table |

Default weights (`w1..w5 = 0.3, 0.2, 0.25, 0.15, 0.1`, summing to 1) are configurable per state/party so the metric can be tuned to local priorities without changing code. HPI is computed on a schedule (e.g. nightly, via a Celery task) and surfaced on both the MP's own dashboard (self-view, for course-correction) and the CM/oversight leaderboard (comparative view, for accountability).

---

## 🌐 Multilingual Support

- Auto-detects the citizen's input language, text or voice.
- Powered by **[Bhashini](https://bhashini.gov.in)**, the Government of India's National Language Translation Mission (MeitY / Digital India Bhashini Division). Bhashini already provides open APIs for translation, ASR, TTS, and OCR across India's scheduled languages, and reportedly already underpins other public grievance-redressal and welfare platforms — making it a natural, government-aligned choice here rather than a third-party dependency.
- AI4Bharat's IndicTrans2 is a solid open-source fallback/complement if a fully offline or self-hosted translation path is needed.
- Target languages at launch: Hindi, Telugu, Tamil, Bengali, Marathi, Kannada, Malayalam, Gujarati, Punjabi, Odia, plus English.
- The chatbot, scheme advisor, and status notifications all respond in the citizen's chosen language — not just the intake form.

---

## 🔐 Security & Data Privacy

- JWT-based session auth with OAuth2 password flow and refresh-token rotation.
- Role-Based Access Control (RBAC) enforced at the API layer on every endpoint, not just hidden in the UI.
- Encryption in transit (TLS) and at rest (AES-256 for PII fields).
- Aadhaar-based eKYC is optional; where used, store only a hashed reference, never the raw Aadhaar number, and follow minimal-data-retention principles.
- Designed to align with India's **Digital Personal Data Protection Act, 2023 (DPDP Act)** and the DPDP Rules, 2025: explicit, purpose-limited consent capture presented in plain language, a citizen-facing data access/correction/erasure flow, breach notification procedures, and — since MP OS would likely be a **Significant Data Fiduciary** given its scale and the sensitivity of grievance data — governance measures like a designated Data Protection Officer and periodic Data Protection Impact Assessments are worth planning for even at MVP stage, ahead of the Act's phased compliance deadline.
- Full audit trail for every administrative action (who viewed, edited, or routed a grievance, and when).

---

## ⚖️ Compliance, Governance & Ethical Considerations

Because MP OS links financial contributions to a visibility/recognition system, this is the section most worth a judge's — and your own — scrutiny. A few safeguards are worth building in from day one rather than retrofitting later:

1. **Hard separation of concerns.** Token balance must never affect grievance priority, routing speed, or resolution SLA. This has to be enforced at the query/business-logic layer (see [Tokenized Influence System](#-tokenized-influence-system)), not just documented as a policy.
2. **Transparency ledger.** Every donation-to-token conversion is logged to an append-only ledger, with aggregate figures displayed publicly (individual donor identity shown only if the donor opts in). The goal is that the "value" of engagement is auditable, not opaque.
3. **Regulatory alignment.** Any donation flow should be reviewed against the **Representation of the People Act, 1951** and current **Election Commission of India (ECI)** guidelines on political contributions. It's worth being deliberate here: India's Supreme Court struck down the Electoral Bonds scheme in February 2024, specifically because its anonymity undermined voters' right to information under Article 19(1)(a) and created a real risk of quid-pro-quo arrangements between donors and parties. MP OS doesn't have to repeat that mistake — an auditable, non-anonymous, non-access-linked ledger is a very different design, and this section is a big part of why it's structured that way.
4. **Independent oversight.** An audit committee outside the MP's own office should periodically review the tokenization ledger and the HPI computation methodology, so neither can be quietly gamed by the office it's meant to hold accountable.

> This section is a design recommendation based on general public information, not legal advice. Any real deployment that combines political donations with a citizen-facing platform should have its donation and tokenization flow reviewed by legal counsel familiar with Indian election and campaign-finance law before launch.

---

## 🚀 Getting Started

### Prerequisites
- Node.js 18+
- Python 3.11+
- PostgreSQL 15+
- Redis 7+
- Docker & Docker Compose (recommended)

### Quick start (Docker)

```bash
git clone https://github.com/<your-org>/mp-os.git
cd mp-os
cp .env.example .env      # fill in secrets
docker-compose up --build
```

### Manual setup

**Backend**
```bash
cd backend
python -m venv venv && source venv/bin/activate
pip install -r requirements.txt
alembic upgrade head
uvicorn app.main:app --reload --port 8000
```

**Frontend**
```bash
cd frontend
npm install
npm run dev
```

Visit `http://localhost:5173` for the app and `http://localhost:8000/docs` for the FastAPI Swagger UI.

---

## 🔑 Environment Variables

```env
# Backend
DATABASE_URL=postgresql://user:password@localhost:5432/mpos
REDIS_URL=redis://localhost:6379/0
JWT_SECRET_KEY=
JWT_ALGORITHM=HS256
LLM_API_KEY=
TRANSLATION_API_KEY=
VECTOR_DB_URL=
PAYMENT_GATEWAY_KEY=
PAYMENT_GATEWAY_SECRET=
S3_BUCKET_NAME=
S3_ACCESS_KEY=
S3_SECRET_KEY=

# Frontend
VITE_API_BASE_URL=http://localhost:8000/api/v1
```

---

## 🗺️ Roadmap

- [x] Core problem submission + AI document generation
- [x] Multilingual chatbot & scheme advisor
- [x] Slot-based appointment booking
- [x] Happiness Performance Index v1
- [ ] Tokenized influence ledger with public transparency dashboard
- [ ] Department Officer role — closes the loop from "routed" to "resolved"
- [ ] Blockchain-anchored audit trail for donations (stretch goal, for extra tamper-evidence beyond an append-only Postgres ledger)
- [ ] Aadhaar-based eKYC integration
- [ ] Voice-first accessibility mode for low-literacy users
- [ ] Interoperability with CPGRAMS for cross-filing
- [ ] Multi-state / multi-party rollout

---

## 🤝 Contributing

Contributions are welcome. Please open an issue to discuss significant changes before submitting a pull request, and follow the existing code style (Black/Ruff for Python, ESLint/Prettier for TypeScript).

## 👥 Team

*Add your team name, member names, and roles here before submission.*

## 📄 License

Distributed under the MIT License — see `LICENSE` for details. *(Swap this out if your hackathon's rules require a different license.)*

## 🙏 Acknowledgements & Prior Art

- **[CPGRAMS](https://pgportal.gov.in)** (Centralized Public Grievance Redress and Monitoring System, DARPG) — the existing benchmark for nationwide grievance intake and routing.
- **[Bhashini](https://bhashini.gov.in)** (Digital India, MeitY) — for making multilingual AI a public digital good rather than something every app has to rebuild.
- India's **Digital Personal Data Protection Act, 2023** — the compliance backdrop for how citizen data is handled here.

*(Add screenshots or a demo GIF of the actual UI here before submission — judges skim, and a visual above the fold goes a long way.)*
