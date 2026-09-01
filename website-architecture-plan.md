# AI Automation & Software Services Portfolio — Complete Plan

## 1. Purpose & positioning

Portfolio + lead-gen machine, do audiences ke liye:
- Recruiters/clients jo skill dekhna chahte hain
- Businesses jo AI automation service hire karna chahte hain

Har case study ke sath clear "Hire me for this" CTA.

## 2. Public-facing sitemap

- **Home** — hero, elevator pitch, featured 3 projects, services summary, CTA
- **Services** — AI agents, workflow automation, OCR/document processing, chatbots, custom APIs
- **Case studies / Projects**:
  - RentFlow + Autonomous Dev tool (multi-agent code generation)
  - Schema-PDF AI (multi-provider extraction pipeline)
  - AITS Opportunity Discovery (7-stage FastAPI + Gemini pipeline)
  - Pakistani document OCR system (PaddleOCR + Gemini + Claude vision)
  - Website chatbot SaaS
- **About** — background, teaching role, skills stack
- **Blog/Insights** (optional, SEO)
- **Contact / Hire** — form + calendar booking link
- **Live demos** — chatbot widget demo, OCR/PDF extraction demo (rate-limited, sample data only)

## 3. Admin panel (private, only for you)

Ek separate route (e.g. `/admin`) jo public site se completely alag rahe, JWT-auth protected. Isme aap bina code chuye sab manage kar sakte ho:

**Dashboard (overview)**
- Total visitors (basic analytics summary)
- New contact/lead submissions count
- Live demo usage count (kitni baar OCR/chatbot demo try hui — cost tracking ke liye zaroori)
- API cost/usage estimate (agar provider dashboard se pull kar sakein)

**Content management**
- Projects/case studies — add/edit/delete, reorder, publish/draft toggle
- Services — edit descriptions, pricing (agar dikhana ho)
- Blog posts (agar blog rakha)

**Leads/CRM mini-view**
- Saare contact form submissions — name, email, message, source page, timestamp
- Status tags: new / contacted / converted / archived
- Export to CSV

**Demo monitoring**
- Log of demo runs — timestamp, which demo, IP (rate-limit tracking), success/fail
- Ability to pause a demo endpoint instantly (agar abuse ho rahi ho ya cost spike ho)

**Settings**
- API keys management (masked, backend `.env`-linked, sirf status dikhana — "connected/not connected")
- Rate-limit thresholds adjust karna

**Tech approach for admin panel**
- Same Next.js app ke andar `/admin` route (protected middleware) — separate app maintain karne ki zaroorat nahi
- FastAPI backend pe alag `/admin/*` endpoints, JWT + role check
- Simple email/password login (aap akele user ho, complex auth system ki zaroorat nahi)

## 4. Frontend

- **Framework**: Next.js (React) — SSR/SSG for SEO
- **Styling**: Tailwind CSS
- **Hosting**: Vercel (free tier, GitHub CI/CD)
- Case studies MDX ya CMS-driven (ya admin panel se hi manage — better, kyunke code-push ki zaroorat nahi)

## 5. Backend

- **Framework**: FastAPI
- Responsibilities: contact form → DB + email, admin CRUD APIs, live AI demo endpoints
- **Auth**: JWT-based, sirf admin ke liye

## 6. Database & storage

- **PostgreSQL** (Supabase free tier)
- Tables: `projects`, `leads`, `blog_posts` (optional), `demo_logs`, `admin_users`
- **File storage**: S3-compatible / Cloudinary — demo uploads ke liye

## 7. Live demo section (standout feature)

- Chatbot widget demo (website-chatbot-saas se)
- PDF → structured JSON demo (schema-pdf-ai se, rate-limited)
- OCR demo with sample CNIC image only (privacy safe)

Provider routing: primary (Groq/Gemini) + fallback, backend-proxied (API keys kabhi frontend mein expose nahi honge), IP-based rate limiting, sample-data-only for sensitive demos.

## 8. Deployment

- Frontend → Vercel
- Backend → Railway/Render (VPS agar Ollama chalana ho)
- DB → Supabase managed Postgres
- Domain + SSL → Vercel/Railway auto

## 9. Build order

1. Content plan + wireframe
2. Static frontend with case studies — deploy jaldi
3. Contact form backend + basic admin panel (leads view + CRUD)
4. Live demo endpoints
5. Demo monitoring + rate-limit controls in admin
6. Polish, SEO, analytics
