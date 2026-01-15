# Developer Briefing
## TenantShield – Bakersfield Tenant Help
### Quick Start Guide (Paste to Your Dev)

---

## 🎯 Project Goal

Build a simple landing page where Bakersfield tenants can submit landlord disputes and receive AI-powered legal analysis via email within 2-5 minutes.

**No backend needed.** Everything runs on:
- Framer (frontend + forms)
- Zapier (automation + AI)
- Stripe (payments via links only)

---

## 🌐 Domain & Routes

**Domain:** `coaihq.online`

**Routes:**
- `/` – Minimal hub (can redirect to main page or be barebones)
- `/bakersfield-tenant-help` – **Main landing page (BUILD THIS FIRST)**

---

## 🛠️ Tech Stack

| Component | Tool | Purpose |
|-----------|------|---------|
| **Frontend** | Framer | Landing page + native form |
| **Forms** | Framer Form → Zapier Webhook | Capture submissions |
| **AI** | OpenAI/Claude (via Zapier) | Analyze tenant cases |
| **Email** | Gmail/SendGrid (via Zapier) | Send AI analysis to users |
| **Payments** | Stripe Payment Links | Upsell products (no backend) |

---

## 📋 What You Need to Build

### **1. Framer Landing Page** (`/bakersfield-tenant-help`)

**Full spec:** See `FRAMER-PAGE-SPEC.md` (detailed specs)

**Quick Version:**

#### **Sections (in order):**

1. **Navigation**
   - Logo: "COAI HQ" (text, links to `/`)
   - Links: "How it Works" (#how), "FAQ" (#faq), "Contact" (footer)

2. **Hero**
   - Label: "TenantShield by COAI HQ"
   - H1: "Stuck in a Landlord Fight in Bakersfield? Get a Clear Plan in 5 Minutes."
   - Subhead: "AI-powered analysis plus a connection to Bakersfield tenant advocates. No lawyer fees, no guessing. Just clarity."
   - CTA Button: "Analyze My Case →" (scroll to form)

3. **Form Section** (ID: `#form`)
   - **Use Framer native form component**
   - **Fields:**
     | Field | Type | Required |
     |-------|------|----------|
     | `full_name` | Text | Yes |
     | `email` | Email | Yes |
     | `phone` | Text | No |
     | `situation` | Textarea | Yes |
     | `city` | Text (pre-filled: "Bakersfield, CA") | Yes |
     | `consent` | Checkbox | Yes |

   - **Submit Button:** "Get My Plan →"
   - **Form Action:** "Submit to: Webhook/Zapier"
   - **Webhook URL:** `[Paste Zapier webhook URL after setup]`

   - **Form Behavior:**
     - On submit: Disable button, show "Analyzing your case (30–60 seconds)..."
     - On success: Show "Done. Check your email in the next few minutes..."
     - **Do NOT redirect**

4. **Benefits Section** (5 bullets near form)
   - ✅ Instant situation breakdown in plain English
   - ✅ Clear 3–5 step action plan for THIS week
   - ✅ Copy-paste emails and letters ready to send today
   - ✅ Optional connection to a Bakersfield tenant advocate
   - ✅ Built for California tenant law (not generic advice)

5. **How It Works** (ID: `#how`) – 3 steps/columns
   - Step 1: Tell us what happened
   - Step 2: AI analyzes your case
   - Step 3: Get a plan + options

6. **Upsell Teaser**
   - Headline: "Want Done-For-You Documents?"
   - 2 placeholder buttons (links TBD after Stripe setup)

7. **FAQ** (ID: `#faq`) – 4 questions
   - Is this legal advice?
   - How fast do I get my analysis?
   - Who will you connect me with?
   - What does it cost?

8. **Footer**
   - Brand: "COAI HQ – Chaotically Organized AI"
   - Product: "TenantShield – Bakersfield Tenant Help"
   - Contact: `support@coaihq.online`
   - Disclaimer: "Not a law firm. Not legal advice."

#### **SEO Meta Tags:**

```html
<title>Bakersfield Tenant Help – AI Landlord Dispute Analysis | COAI HQ</title>
<meta name="description" content="Stuck in a landlord fight in Bakersfield? Get AI-powered case analysis, a step-by-step plan, and connection to local tenant advocates in minutes. Not legal advice.">
<meta property="og:title" content="Bakersfield Tenant Help – TenantShield by COAI HQ">
<meta property="og:url" content="https://coaihq.online/bakersfield-tenant-help">
<meta property="og:type" content="website">
```

---

### **2. Zapier Workflow** (Backend Automation)

**Full guide:** See `ZAPIER-SETUP.md` (step-by-step instructions)

**Quick Version:**

#### **Zap Flow:**

```
[Framer Form]
    → [Zapier Webhook Trigger]
    → [Optional: Text Formatter]
    → [AI Analysis (OpenAI/Claude)]
    → [Email to User (Gmail/SendGrid)]
    → [Optional: Log to Google Sheets]
```

#### **Steps:**

1. **Trigger:** Webhooks by Zapier → Catch Hook
   - Generates webhook URL → paste into Framer form settings

2. **Formatter (optional):** Formatter by Zapier → Trim Whitespace
   - Clean up `situation` text

3. **AI Analysis:** OpenAI or Code by Zapier (Claude)
   - **Prompt:** See `AI-PROMPT-TEMPLATE.md`
   - **Input:** User's situation, name, city
   - **Output:** AI-generated case analysis

4. **Email User:** Gmail or SendGrid
   - **Template:** See `EMAIL-TEMPLATES.md` (Template 1)
   - **Body includes:** AI analysis + 3 upsell options (Stripe links)

5. **Log (optional):** Google Sheets or Airtable
   - Track all submissions for analytics

#### **What You Provide After Setup:**

- Zapier webhook URL (for Framer form)
- Zapier is LIVE and tested (submit test form → receive email)

---

### **3. Stripe Payment Links** (Upsells)

**Full guide:** See `STRIPE-SETUP.md`

**Quick Version:**

#### **Products to Create:**

1. **Premium Letter Package** – $29
   - Done-for-you demand letters and templates

2. **Paralegal 15-min Call** – $15
   - Quick consultation with California paralegal

#### **Steps:**

1. Create products in Stripe Dashboard
2. Generate Payment Links for each product
3. **Provide links to paste into:**
   - Zapier email template (Template 1 in `EMAIL-TEMPLATES.md`)
   - Framer upsell section (optional)

**No backend integration needed.** Stripe handles checkout.

---

## 📂 Files to Reference

| File | Purpose |
|------|---------|
| `ARCHITECTURE.md` | High-level overview |
| `FRAMER-PAGE-SPEC.md` | **Full landing page spec (copy, layout, SEO)** |
| `ZAPIER-SETUP.md` | **Step-by-step Zapier workflow setup** |
| `STRIPE-SETUP.md` | **Stripe payment links setup** |
| `AI-PROMPT-TEMPLATE.md` | AI system prompt for case analysis |
| `EMAIL-TEMPLATES.md` | Email copy for Zapier workflow |
| `DEV-BRIEFING.md` | This document (quick reference) |

---

## ✅ Development Checklist

### **Phase 1: Framer Landing Page (30-45 min)**

- [ ] Create Framer project
- [ ] Build page sections (Nav, Hero, Form, How It Works, FAQ, Footer)
- [ ] Add form with 6 fields (full_name, email, phone, situation, city, consent)
- [ ] Set form to "Submit to: Webhook/Zapier" (paste webhook URL later)
- [ ] Add SEO meta tags
- [ ] Test responsive design (mobile + desktop)
- [ ] Publish to `https://coaihq.online/bakersfield-tenant-help`

---

### **Phase 2: Zapier Workflow (45-60 min)**

- [ ] Create Zapier account (free tier: 100 tasks/month)
- [ ] Set up Zap:
  - [ ] Step 1: Webhooks by Zapier → Catch Hook
  - [ ] Step 2 (optional): Formatter → Trim Whitespace
  - [ ] Step 3: OpenAI/Claude → AI Analysis (use prompt from `AI-PROMPT-TEMPLATE.md`)
  - [ ] Step 4: Gmail/SendGrid → Send Email (use template from `EMAIL-TEMPLATES.md`)
  - [ ] Step 5 (optional): Google Sheets → Log Submission
- [ ] Copy webhook URL from Step 1
- [ ] Paste webhook URL into Framer form settings
- [ ] Test workflow (submit form → check email arrives in 2-5 min)
- [ ] Turn Zap ON (publish)

---

### **Phase 3: Stripe Payment Links (15-20 min)**

- [ ] Create Stripe account (free)
- [ ] Create Product 1: Premium Letter Package ($29)
- [ ] Create Payment Link for Product 1 → copy URL
- [ ] Create Product 2: Paralegal Consultation ($15)
- [ ] Create Payment Link for Product 2 → copy URL
- [ ] Paste both Stripe links into:
  - [ ] Zapier email template (update Step 4)
  - [ ] Framer upsell section (optional)

---

### **Phase 4: Testing & Launch (30 min)**

- [ ] Submit 3 test forms with different scenarios
- [ ] Verify email delivery (check spam folder)
- [ ] Test Stripe payment links (use Stripe test mode first)
- [ ] Mobile responsive check (iPhone, Android)
- [ ] Desktop check (Chrome, Safari, Firefox)
- [ ] SEO meta tags visible in page source
- [ ] Custom domain pointing correctly (`coaihq.online`)

---

## 🚀 Design Guidance

**Keep it simple.**

- Use Framer defaults for speed
- Don't over-design
- Focus on: **clarity, speed, and trust**
- Colors: Primary blue (#2563EB), secondary green (#10B981), light gray (#F9FAFB)
- Font: Inter or system font

**Goal:** User fills out form → receives AI analysis via email within 2-5 minutes. That's it.

---

## 📧 Contact & Support

**Email:** `support@coaihq.online`

**Assets Provided:**

- Logo: "COAI HQ" (text only, no image)
- Product name: "TenantShield – Bakersfield Tenant Help"
- Disclaimer: "Not a law firm. Not legal advice. For information purposes only."

---

## 💰 Cost Estimate (Month 1)

| Service | Cost |
|---------|------|
| Framer | $0-$5/mo |
| Zapier (Free tier) | $0 |
| OpenAI/Claude API | $10-$30 (pay-per-use) |
| Stripe | 2.9% + $0.30 per transaction |
| SendGrid (optional) | $0 (free tier) |
| **Total** | **$10-$35/mo** |

**Scaling:** At 100+ form submissions/month, upgrade Zapier to Starter plan ($19.99/mo).

---

## 🧩 Key Integration Points

### **Framer → Zapier:**

- In Framer form settings:
  - Set "Submit to: Webhook/Zapier"
  - Paste Zapier webhook URL (from Zapier Step 1)

---

### **Zapier → AI:**

- In Zapier Step 3 (OpenAI or Code by Zapier):
  - **System Prompt:** Copy from `AI-PROMPT-TEMPLATE.md`
  - **User Message:** Dynamic fields from form (name, email, situation, city)

---

### **Zapier → Email:**

- In Zapier Step 4 (Gmail/SendGrid):
  - **To:** `1. Email` (from webhook)
  - **Subject:** "Your Bakersfield Tenant Case – Analysis & Next Steps"
  - **Body:** Template 1 from `EMAIL-TEMPLATES.md`
  - **Dynamic field:** `[AI Analysis]` = output from Step 3

---

### **Email → Stripe:**

- Paste Stripe payment links in email body:
  - Premium Letter Package: `https://buy.stripe.com/XXXXXXXXXXXX`
  - Paralegal Consultation: `https://buy.stripe.com/YYYYYYYYYYYY`

---

## ❓ FAQs for Dev

### Q: Do I need to set up a backend server?
**A:** No. Everything runs on Framer (frontend), Zapier (automation), and Stripe (payments via links).

---

### Q: How does the form submission trigger the AI?
**A:** Framer form submits to Zapier webhook → Zapier calls OpenAI/Claude API → Zapier sends email with AI response.

---

### Q: Do I need to handle Stripe checkout on the site?
**A:** No. Use Stripe Payment Links (just URLs). Users click → redirected to Stripe checkout → Stripe handles payment.

---

### Q: What if Zapier fails or times out?
**A:** Check Zapier Task History for errors. Common issues:
- AI timeout: reduce max tokens or use faster model (GPT-3.5)
- Email not sending: check Gmail/SendGrid authorization

---

### Q: How do I test without using real API credits?
**A:**
- **Zapier:** Use Test Mode (free test data)
- **Stripe:** Use Test Mode + test card (4242 4242 4242 4242)
- **OpenAI/Claude:** Use small test prompts (cost ~$0.01 each)

---

## 📌 Priority Summary

**Build in this order:**

1. ✅ **Framer landing page** (`/bakersfield-tenant-help`) – **Priority 1**
   - Full spec: `FRAMER-PAGE-SPEC.md`

2. ✅ **Zapier workflow** (form → AI → email) – **Priority 1**
   - Setup guide: `ZAPIER-SETUP.md`

3. ✅ **Stripe payment links** – **Priority 2**
   - Setup guide: `STRIPE-SETUP.md`

4. ⏸️ **Root page** (`/`) – **Priority 3** (can be minimal or redirect)

---

## 🎯 Success Criteria (Week 1)

- [ ] Landing page live at `https://coaihq.online/bakersfield-tenant-help`
- [ ] Form submissions working (webhook triggers Zapier)
- [ ] Email delivery working (users receive AI analysis in 2-5 min)
- [ ] Stripe payment links working (test purchase completes)
- [ ] Mobile responsive (no broken layouts)
- [ ] SEO meta tags present (check page source)

**Goal:** 15-25 form submissions in Week 1, 2-5% conversion to paid products.

---

## 📞 Questions?

If anything is unclear, refer to the detailed setup guides:

- `FRAMER-PAGE-SPEC.md` – Full page layout and copy
- `ZAPIER-SETUP.md` – Step-by-step automation setup
- `STRIPE-SETUP.md` – Payment link creation
- `AI-PROMPT-TEMPLATE.md` – AI prompt and examples
- `EMAIL-TEMPLATES.md` – Email copy for all scenarios

**Or contact:** `support@coaihq.online`

---

**Last Updated:** 2026-01-15
**Version:** 1.0

---

## 📋 Copy-Paste Summary for Dev

**To send to your developer in one message:**

```
──────────────────────────────────────────────────────────────
TENANTSHIELD – BAKERSFIELD LANDING PAGE (Quick Briefing)
──────────────────────────────────────────────────────────────

GOAL:
Build a landing page where Bakersfield tenants submit landlord disputes
and receive AI-powered legal analysis via email within 2-5 minutes.

TECH STACK:
• Frontend: Framer (landing page + form)
• Automation: Zapier (form → AI → email)
• AI: OpenAI/Claude (via Zapier)
• Email: Gmail/SendGrid (via Zapier)
• Payments: Stripe Payment Links (no backend)

URL:
https://coaihq.online/bakersfield-tenant-help

WHAT YOU BUILD:
1. Framer landing page with:
   - Hero section ("Stuck in a Landlord Fight?")
   - Form (6 fields: name, email, phone, situation, city, consent)
   - Form submits to Zapier webhook (URL provided after setup)
   - How It Works, FAQ, Footer sections

2. Zapier workflow:
   - Trigger: Webhook (catches form submission)
   - AI Analysis: OpenAI/Claude (analyzes tenant case)
   - Send Email: Gmail/SendGrid (sends AI analysis to user)

3. Stripe Payment Links:
   - Create 2 products: Premium Letter Package ($29), Paralegal Call ($15)
   - Paste links in email template

DETAILED SPECS:
See files in this repo:
• FRAMER-PAGE-SPEC.md (full page layout)
• ZAPIER-SETUP.md (automation setup)
• STRIPE-SETUP.md (payment links)
• AI-PROMPT-TEMPLATE.md (AI prompt)
• EMAIL-TEMPLATES.md (email copy)

DESIGN GUIDANCE:
Don't over-design. Use Framer defaults. Focus on speed and clarity.

TIMELINE:
Total setup: 2-3 hours
• Framer: 30-45 min
• Zapier: 45-60 min
• Stripe: 15-20 min
• Testing: 30 min

QUESTIONS?
support@coaihq.online

──────────────────────────────────────────────────────────────
```

---

**END OF DEV BRIEFING**
