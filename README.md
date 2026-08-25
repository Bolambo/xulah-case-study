# Xulah

## Content Intelligence Platform

**Live product:** https://xulah.com  
**Product builder:** Chigozie Nwokoro  
**Production source:** Private

Xulah is a Content Intelligence Platform built for creators, businesses, entrepreneurs, marketers, coaches, consultants, e-commerce brands, and other content-driven professionals.

Rather than treating content generation as a simple prompt-and-output exercise, Xulah considers the context behind what the user is trying to achieve. It combines **objective, audience, niche, region, platform, tone, content pack, and selected template** to determine an appropriate content direction and produce strategy-driven content.

## What I Built

I designed and built Xulah, developed its product implementation roadmap, and took the product from concept and MVP through a continuously evolving live application.

My work covered product planning, frontend and backend development, database design, authentication, AI integration, subscription architecture, payment processing, security and abuse-prevention mechanisms, API integrations, deployment, testing, debugging, and ongoing product refinement.

Xulah includes authenticated workspaces, subscription entitlements, regional payment flows, AI-powered content generation, a 30-day content calendar, media integrations, usage controls, account/device security, and an administrative Intelligence Circle environment.

## Technology Stack

| Area | Technologies |
|---|---|
| Application | Next.js 16, React 19, TypeScript |
| Styling | Tailwind CSS 4, PostCSS |
| Backend | Next.js Route Handlers, Node.js, TypeScript |
| Database & Auth | Supabase, PostgreSQL, Supabase Auth, Row Level Security |
| AI | OpenAI API |
| Payments | Stripe, Paystack |
| Media | Unsplash, Pexels |
| Email | Resend, Brevo integration |
| Source Control | GitHub |
| Deployment | Vercel |
| Domain / DNS | Cloudflare, Namecheap |
| Package Workflow | pnpm |

## Architecture

Xulah uses a **Next.js App Router** architecture with React and TypeScript on the application layer, server-side route handlers for backend operations, and Supabase for authentication and persistent application data.

![Xulah high-level architecture](architecture/xulah-architecture.svg)

Reusable server-side libraries handle content templates and rules, prompt layers, calendar generation and validation, entitlement resolution, device security, Supabase clients, Stripe and Paystack billing, media providers, and Intelligence Circle services.

## Content Intelligence Engine

Xulah builds generation instructions through multiple intelligence layers:

- template rules
- subscription-plan depth
- niche-specific guidance
- regional language and market calibration
- tone and call-to-action guidance
- intelligence and voice reasoning
- transformation/action rules
- commercial intent and output formatting

Generation considers platform, content type, niche, template, region, plan, and requested transformation. Generated content is persisted with its associated user and contextual information.

## AI Infrastructure

Xulah integrates the OpenAI API through the official OpenAI Node package.

Current subscription-aware model allocation:

- **Silver:** `gpt-4o-mini`
- **Gold:** `gpt-4o-mini`
- **Platinum:** `gpt-5.4-mini`

The 30-day calendar agent also uses `gpt-4o-mini` with a versioned prompt identifier.

Selected transient OpenAI network failures are handled with bounded retries, exponential backoff, and jitter.

## Authentication & Authorization

Supabase Auth provides email/password registration, login, email confirmation, password recovery/reset, session validation, and protected application routes.

Role-aware authorization includes `user`, `admin`, and `developer` roles, with privileged role data kept server-controlled.

## Subscription & Payments

Xulah supports **Free, Silver, Gold, and Platinum** plan states through a central entitlement system that determines effective plan, usage allowance, paid status, trial status, and regional onboarding.

### Stripe

Checkout, billing portal, subscription synchronization/resynchronization, plan-price mappings, signed webhook processing, and subscription lifecycle handling are implemented.

### Paystack

Paystack provides the local payment path for Nigerian users and includes local checkout, subscription lifecycle processing, signed webhook verification, and customer/subscription lookup with fallback matching.

Regional logic directs Nigerian users toward the local payment path while directing non-Nigerian users toward international checkout.

## 30-Day Content Calendar

The 30-Day Content Calendar helps users maintain a strategic stream of content over an entire month rather than repeatedly generating isolated posts.

It supports **Instagram, Facebook, LinkedIn, X, and TikTok**, with formats including captions, carousels, short-video scripts, stories, threads, and LinkedIn posts.

The generation workflow is staged:

1. Generate a strategy structure.
2. Validate the strategy.
3. Generate the calendar plan.
4. Parse and validate the returned plan.
5. Recover missing days when necessary.
6. Repair invalid individual items where possible.
7. Fall back to broader plan repair when required.
8. Persist model, prompt version, snapshots, validation results, errors, and completion information.

## Security & Abuse Prevention

Implemented controls include one-active-device account binding, server-side device hashing, device mismatch detection, device transfer challenges, six-digit OTP transfer verification, OTP expiry and attempt limits, email-confirmation enforcement for relevant trial flows, server-side entitlement checks, Row Level Security for calendar data, signed Stripe and Paystack webhook verification, and security-event recording.

Content-generation rules also guard against fabricating statistics, testimonials, discounts, scarcity, stock information, or unsupported business facts during transformations.

Security and abuse testing is an ongoing part of product development.

## External Integrations

- **OpenAI** — content intelligence and generation
- **Supabase** — authentication and data
- **Stripe** — international billing
- **Paystack** — Nigerian billing
- **Unsplash** — image suggestions
- **Pexels** — image and video suggestions
- **Resend** — server-side email functionality
- **Brevo** — Intelligence Circle helper configuration

## Engineering Challenges & Solutions

### Reliable structured AI output
Calendar generation uses parsing, validation, missing-day recovery, targeted item repair, broader fallback repair, bounded attempts, and persisted diagnostics.

### Transient AI API failures
Selected transient OpenAI network failures are handled with bounded retries, exponential backoff, and jitter.

### Payment lifecycle synchronization
Stripe and Paystack use multiple identifiers and signed lifecycle webhooks to improve account matching and subscription-state synchronization.

### Regional payment differences
Regional payment and trial rules are enforced server-side rather than relying only on frontend selection.

### Account sharing and abuse
Device binding, transfer challenges, OTP verification, mismatch handling, entitlement checks, and security-event logging make uncontrolled account sharing and trial abuse more difficult.

### Content quality
Layered intelligence rules preserve template structure while incorporating niche, region, plan, transformation, commercial intent, and output-format requirements.

## Development & Iteration

Xulah has been developed through continuous implementation, testing, debugging, and refinement. The implementation history includes work on calendar validation and repair, generation limits, commercial content intent, Paystack synchronization, Stripe billing and webhook mapping, device-transfer edge cases, trial entitlement alignment, production build issues, responsive/mobile refinement, PWA work, branding, and routing.

## Development Philosophy

Xulah was built through **AI-assisted software development**, while the product direction, roadmap, implementation decisions, integrations, testing, debugging, and deployment were owned and driven by me.

The project represents hands-on learning through building: identifying a product problem, translating it into systems and features, implementing those systems, testing them against real-world behaviour, finding weaknesses, and iterating toward a usable product.

## What This Project Demonstrates

- product ideation and roadmap development
- full-stack web application development
- TypeScript and Next.js
- backend API design
- database design
- authentication and authorization
- AI/API integration
- prompt and intelligence architecture
- SaaS subscription design
- payment-provider integration
- regional payment logic
- security and abuse prevention
- structured AI workflows
- deployment and infrastructure configuration
- debugging and iterative product development

## Current Status

Xulah is a live, actively developed product.

**Visit:** https://xulah.com

The production source repository is intentionally private. This public repository is a **portfolio and technical case study**, not an open-source copy of Xulah's production codebase.

## About the Builder

**Chigozie Nwokoro** is a Computer Science professional and independent product builder currently pursuing a Post-Graduate Diploma in Computer Science at Enugu State University of Science and Technology (ESUT).

**LinkedIn:** https://www.linkedin.com/in/chigozie-nwokoro-4a075a43/  
**GitHub:** https://github.com/Bolambo  
**Live Product:** https://xulah.com
