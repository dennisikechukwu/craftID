# CraftID — The Income Identity Engine for Nigeria's 15 Million Invisible Artisans 🇳🇬

## Live Demo 🚀

https://craft-id-ecru.vercel.app

## Problem Statement

Nigeria has over 15 million skilled artisans — tailors, welders, mechanics, carpenters, hairdressers — who generate hundreds of billions of naira annually but remain invisible to the formal financial system. They are paid in cash or ad-hoc transfers with no verifiable income trail. When they seek even a ₦50,000 tool loan from any digital lender, they are rejected because they have no payslip, no BVN-linked salary, and no credit history. In 2026, even with CBN’s new credit reporting frameworks, the infrastructure to generate alternative credit data for artisans still doesn’t exist.

## Solution Overview

CraftID is an **income identity engine** that turns everyday client payments into **verified, bank-grade proof of income**.

**Important MVP scope:** We do **not** disburse loans or issue virtual cards in this hackathon MVP. CraftID focuses on generating verifiable income history and a portable income claim document.

## How It Works 🧭

1. **Artisan signs up (under 3 minutes)** and creates a craft profile (skill, location, rate card).
2. **Creates an invoice** that includes a secure **Interswitch payment link** (shareable URL) and **QR code**.
3. **Client pays** directly via the link or by scanning the QR.
4. **Payments are automatically tracked** and saved as verified transaction history.
5. As payments accumulate (simulated in demo or via real test payments), CraftID generates a **CraftScore** using transaction data.
6. The artisan generates a **verifiable “Income Claim Document” (PDF)**.
7. A **QR code at the bottom** of the PDF can be scanned by any bank/financial institution to open our verification portal and confirm the artisan’s payment history and CraftScore.

## Key Features ✅

- 🧑🏾‍🔧 Artisan onboarding + craft profile (skill, location, rate card)
- 🧾 Invoice generator + shareable Interswitch payment link/QR
- 💳 Real-time payment tracking (confirmed payments recorded as history)
- 📄 Income Claim PDF generator with embedded QR code for instant verification
- 📊 Simple dashboard showing income history and score

## Interswitch API Integration 🔌

1. **Interswitch Payment (WebPAY Inline Checkout + Transaction Verification)** — used to collect payments via our shareable link/QR and confirm transaction success server-side before recording it as verified income history.
2. **Interswitch BVN Verification API** — used during onboarding to verify identity and boost trust in the resulting income claim.

## Tech Stack 🛠️

- **Frontend:** Next.js (React) + Tailwind CSS + TypeScript
- **Backend:** Next.js Route Handlers (Node.js runtime)
- **Database:** Supabase (PostgreSQL)
- **Payments:** Interswitch WebPAY Inline Checkout + server-side transaction verification
- **PDF generation:** `pdfmake`
- **QR code generation:** `qrcode.react`
- **Deployment:** Vercel (frontend + API routes)

## Team Contributions 👥

| Team Member       | Role                               | Contributions                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| ----------------- | ---------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Ikechukwu Dennis  | Team Lead / Full-stack Developer   | - Led overall MVP build and technical direction (scope control, delivery, demo readiness)<br>- Implemented core user flows across onboarding → dashboard → invoices/payments so artisans can start generating a verifiable income trail quickly<br>- Integrated Interswitch payment experience using WebPAY inline checkout and built the server-side verification flow to ensure only confirmed transactions are recorded as “verified income”<br>- Connected payment confirmation to invoice status updates and transaction history to power CraftScore and the income claim narrative end-to-end                    |
| Favour Olaleru    | Full-stack Developer / Database & Documentation | - Implemented supporting features and wiring needed for a complete income-history pipeline (API routes, data fetching, and UI integration for invoices/payments)<br>- Set up the Supabase database schema and payment statistics function used by the dashboard and scoring logic (artisans, invoices, payments, and aggregated payment stats)<br>- Worked on documentation and submission materials to clearly explain the problem, MVP scope, and demo flow for judges and reviewers<br>- Assisted with deployment readiness and environment configuration patterns for local + hosted setups |
| Folashade Adewara | UI/UX Designer / Research          | - Designed the CraftID user experience to keep onboarding under 3 minutes and make invoice creation + link sharing feel simple for non-technical artisans<br>- Conducted product research on artisan income invisibility and lender requirements to shape the “Income Identity Engine” positioning and verification-first approach<br>- Created screen layouts and UX copy for the dashboard and verification story (income history → CraftScore → downloadable claim document)<br>|

## Installation & Local Setup 💻

### Prerequisites

- Node.js 18+ (recommended: 20+)
- An Interswitch sandbox (or test) credential set
- A Supabase project (PostgreSQL)

### 1) Install dependencies

```bash
npm install
```

### 2) Configure environment variables

Create `.env.local` in the project root:

```bash
# --- App ---
NEXT_PUBLIC_APP_URL=http://localhost:3000

# --- Supabase (server writes happen via service role key) ---
NEXT_PUBLIC_SUPABASE_URL=your_supabase_project_url
SUPABASE_SERVICE_ROLE_KEY=your_supabase_service_role_key

# --- Interswitch (OAuth) ---
INTERSWITCH_AUTH_URL=your_interswitch_oauth_url
INTERSWITCH_CLIENT_ID=your_interswitch_client_id
INTERSWITCH_SECRET_KEY=your_interswitch_secret_key
INTERSWITCH_BASE_URL=your_interswitch_base_url

# --- Interswitch WebPAY inline checkout (client-side) ---
NEXT_PUBLIC_ISW_MERCHANT_CODE=your_merchant_code
NEXT_PUBLIC_ISW_PAY_ITEM_ID=your_pay_item_id
NEXT_PUBLIC_ISW_MODE=TEST

# --- Interswitch BVN Verification ---
INTERSWITCH_BVN_URL=your_bvn_verification_endpoint

```

### 3) Set up the database

Run the SQL migration in your Supabase project:

- `supabase/migrations/001_init.sql`

This creates the minimal tables used in the MVP: `artisans`, `invoices`, and `payments`.

### 4) Start the dev server

```bash
npm run dev
```

Open http://localhost:3000

## Hackathon Impact & Why We Win 🏆

- **Creates the missing alternative credit data layer**: every payment becomes verified, portable income proof.
- **Bank-trustable verification**: the Income Claim PDF is easy to share, easy to validate, and backed by real transaction history.
- **Designed for the informal reality**: no payslip needed, no salary account needed—just verified customer payments.
- **Massive addressable market**: Nigeria’s 15M+ artisans can finally build measurable financial identity.

## Future Roadmap 🔭

- Full QR-backed verification page showing the artisan’s verified ledger and CraftScore in real time
- Deeper scoring signals (seasonality, client diversity, invoice fulfillment rate)
- Multi-merchant support and improved invoice lifecycle (reminders, partial payments)
- Bank/FI partner dashboard for bulk verification workflows

## License

MIT

---

CraftID exists to make financial inclusion real: **if an artisan can earn, they should be able to prove it — and access opportunity.**
