# COAI HQ - TenantShield Architecture

**Domain:** coaihq.online
**Product:** TenantShield – Bakersfield Tenant Help
**Primary URL:** https://coaihq.online/bakersfield-tenant-help

---

## 1. High-Level Architecture

### Stack Overview

| Component | Technology | Purpose |
|-----------|-----------|---------|
| **Frontend** | Framer | Single-page landing site with native forms |
| **Forms → Automation** | Framer Form + Zapier Webhook | Capture user submissions and trigger workflows |
| **AI Analysis** | OpenAI/Claude via Zapier | Generate case analysis and action plans |
| **Email Delivery** | Gmail/SendGrid via Zapier | Send AI analysis and follow-ups to users |
| **Payments** | Stripe Payment Links | Handle upsell purchases (no backend needed) |
| **Analytics** | Google Analytics (optional) | Track conversions and user behavior |

### Concept

- **Parent Brand:** COAI HQ (Chaotically Organized AI)
- **Product:** TenantShield – Bakersfield Tenant Help
- **Value Prop:** AI-powered landlord dispute analysis + connection to local tenant advocates
- **Target:** Bakersfield, CA renters facing landlord issues

---

## 2. Site Structure

### Routes

| Route | Purpose | Priority |
|-------|---------|----------|
| `/` | COAI HQ hub (minimal, can redirect) | Low |
| `/bakersfield-tenant-help` | Main TenantShield landing page | **HIGH** |

**Dev Note:** Build `/bakersfield-tenant-help` first. The root `/` can be a simple redirect or barebones hub page.

---

## 3. Page: `/bakersfield-tenant-help`

### 3.1 SEO & Meta Tags

```html
<title>Bakersfield Tenant Help – AI Landlord Dispute Analysis | COAI HQ</title>

<meta name="description" content="Stuck in a landlord fight in Bakersfield? Get AI-powered case analysis, a step-by-step plan, and connection to local tenant advocates in minutes. Not legal advice.">

<!-- Open Graph -->
<meta property="og:title" content="Bakersfield Tenant Help – TenantShield by COAI HQ">
<meta property="og:description" content="Stuck in a landlord fight in Bakersfield? Get AI-powered case analysis, a step-by-step plan, and connection to local tenant advocates in minutes. Not legal advice.">
<meta property="og:url" content="https://coaihq.online/bakersfield-tenant-help">
<meta property="og:type" content="website">
```

### 3.2 Page Layout (Sections in Order)

#### **Navigation**
- **Left:** "COAI HQ" (text logo, links to `/`)
- **Right Links:**
  - "How it Works" → `#how`
  - "FAQ" → `#faq`
  - "Contact" → footer

---

#### **Hero Section**

```
[Small Label]
TenantShield by COAI HQ

[H1]
Stuck in a Landlord Fight in Bakersfield?
Get a Clear Plan in 5 Minutes.

[Subhead]
AI-powered analysis plus a connection to Bakersfield tenant advocates.
No lawyer fees, no guessing. Just clarity.

[Primary CTA Button]
Analyze My Case →
(scroll to form)

[Secondary Link]
How this works
(anchor to #how)
```

---

#### **Form Section** (ID: `#form`)

**Placement:** Just below hero, full-width bordered card

**Form Fields:**

| Field Name | Type | Required | Label/Placeholder |
|------------|------|----------|-------------------|
| `full_name` | text | ✅ Yes | Your full name |
| `email` | email | ✅ Yes | Email address |
| `phone` | text | ⚠️ Optional | Phone number (optional but encouraged) |
| `situation` | textarea | ✅ Yes | Describe what's happening with your landlord or rental (dates, amounts, what they said, what you did) |
| `city` | text/select | ✅ Yes | City (pre-filled: "Bakersfield, CA") |
| `consent` | checkbox | ✅ Yes | I understand this is information only, not legal advice. |

**Submit Button:** "Get My Plan →"

**Form Behavior:**

1. **On Submit:**
   - Disable button
   - Show inline status: "Analyzing your case (30–60 seconds)..."

2. **After Successful Webhook:**
   - Show thank-you message:
     ```
     Done. Check your email in the next few minutes
     for your analysis and next steps.
     ```
   - **Do NOT redirect away**

**Technical Requirements for Dev:**

- Use Framer native form component
- Set "Submit to: Webhook/Zapier"
- Paste Zapier webhook URL (provided separately)
- Ensure proper error handling and loading states

---

#### **Benefits Section**

**Location:** Near the form (above or below)

**Benefits (5 bullet points):**

- ✅ Instant situation breakdown in plain English
- ✅ Clear 3–5 step action plan for THIS week
- ✅ Copy-paste emails and letters ready to send today
- ✅ Optional connection to a Bakersfield tenant advocate
- ✅ Built for California tenant law (not generic advice)

---

#### **How It Works** (ID: `#how`)

**Layout:** 3 columns or vertical steps

**Step 1 – Tell us what happened**
> You describe your landlord issue in a few sentences. Dates, amounts, what they said.

**Step 2 – AI analyzes your case**
> Our AI looks at your situation through the lens of California tenant law and scores how strong your position is.

**Step 3 – Get a plan + options**
> You get an email with a summary, a step-by-step plan, draft emails, and options to talk to a local advocate.

---

#### **Upsell Teaser Section**

**Headline:** Want done-for-you documents?

**Copy:**
> For some cases, you can upgrade to get your letters formatted, ready for certified mail, or get a short paid consult with a tenant-focused paralegal.

**Two Buttons (placeholder links):**

1. "See letter package options →"
   _(Mention: "link will be in your email")_

2. "Talk to a paralegal →"
   _(Placeholder for Stripe/Calendly)_

---

#### **FAQ** (ID: `#faq`)

**Q: Is this legal advice?**
**A:** No. This is information to help you understand your situation. Always speak to a licensed attorney for legal advice.

**Q: How fast do I get my analysis?**
**A:** Usually within a few minutes, delivered to your email.

**Q: Who will you connect me with?**
**A:** Tenant-focused paralegals or advocates in the Bakersfield/Kern County area. No obligation.

**Q: What does it cost?**
**A:** The basic AI analysis is free. Optional document packages or consults may have a fee, clearly shown before you pay.

---

#### **Footer**

**Brand:** COAI HQ – Chaotically Organized AI
**Product:** TenantShield – Bakersfield Tenant Help
**Contact Email:** support@coaihq.online

**Small Print:**
> Not a law firm. Not legal advice. For information purposes only.

---

## 4. Zapier + AI Workflow

See: [ZAPIER-SETUP.md](./ZAPIER-SETUP.md)

**High-Level Flow:**

1. **Trigger:** Webhooks by Zapier → Catch Hook (Framer form submission)
2. **Formatter:** Clean up text (optional)
3. **AI Call:** OpenAI/Claude API with TenantShield analysis prompt
4. **Email User:** Send AI analysis + upsell options
5. **Log Submission:** (Optional) Store in Airtable/Google Sheets

---

## 5. Stripe Payment Links

See: [STRIPE-SETUP.md](./STRIPE-SETUP.md)

**Products:**

1. **Premium Letter Package** – Custom pricing (suggested: $29-$49)
2. **Paralegal 15-min Call** – Custom pricing (suggested: $15-$25)

**Implementation:**
- Create products in Stripe Dashboard
- Generate Payment Links
- Embed links in email template and upsell section

**No backend integration needed** – Stripe handles checkout.

---

## 6. Key Files & Assets

### Files to Provide to Dev:

| Asset | Content |
|-------|---------|
| **Domain** | `https://coaihq.online/bakersfield-tenant-help` |
| **Logo** | "COAI HQ" (text only, no logo file needed for v1) |
| **Product Label** | "TenantShield – Bakersfield Tenant Help" |
| **Copy** | All headlines, subheads, bullets from this doc |
| **Disclaimer** | "Not a law firm. Not legal advice." |
| **Form Fields** | See section 3.2 Form Section above |
| **Zapier Webhook URL** | (Provided after Zapier setup) |

### Dev Instruction Summary:

> **Goal:** User fills out the form → within 2–5 minutes they receive an email with AI-generated case analysis and a 3–5 step plan.
>
> **Design Guidance:** Don't over-design. Focus on speed and robustness. You are allowed to use Framer defaults.
>
> **Priority:** Build `/bakersfield-tenant-help` first. Root `/` can be minimal or redirect.

---

## 7. Tech Stack Details

| Layer | Tool | Notes |
|-------|------|-------|
| **Frontend** | Framer | No-code website builder with native forms |
| **Hosting** | Framer (built-in) | Custom domain: coaihq.online |
| **Form Handling** | Framer → Zapier Webhook | Native form component |
| **Automation** | Zapier | Free tier: 100 tasks/month (≈25 leads) |
| **AI** | OpenAI GPT-4 or Claude 3.5 | Via Zapier integration or custom webhook |
| **Email** | Gmail or SendGrid | Via Zapier (Gmail for testing, SendGrid for scale) |
| **Payments** | Stripe Payment Links | No backend, just links |
| **Analytics** | Google Analytics 4 (optional) | Track form submissions and conversions |

---

## 8. Success Metrics (Week 1)

- **Form Submissions:** 15-25 submissions
- **Email Delivery Rate:** >95%
- **AI Analysis Quality:** Manual review of first 10 outputs
- **Upsell Conversion:** 2-5% of submissions purchase upsell
- **Revenue Target:** $50-$200 (proof of concept)

---

## 9. Legal & Compliance

**Disclaimer (prominently displayed):**
> Not a law firm. Not legal advice. For information purposes only.

**User Consent:** Required checkbox acknowledging info is educational, not legal advice.

**Data Privacy:**
- Zapier: SOC 2 Type II compliant
- Stripe: PCI DSS compliant
- Framer: GDPR compliant
- **Recommendation:** Add simple privacy policy page (v2)

---

## 10. Next Steps for Implementation

### Phase 1: Setup (Day 1)
1. ✅ Set up Framer project
2. ✅ Build landing page (`/bakersfield-tenant-help`)
3. ✅ Create Zapier workflow with AI integration
4. ✅ Set up Stripe payment links

### Phase 2: Testing (Day 1-2)
1. ✅ Test form → Zapier → AI → Email flow
2. ✅ Verify email delivery and formatting
3. ✅ Test Stripe payment links
4. ✅ Manual QA on mobile and desktop

### Phase 3: Launch (Day 2)
1. ✅ Point custom domain (coaihq.online) to Framer
2. ✅ Enable Google Analytics
3. ✅ Launch and monitor first 5 submissions
4. ✅ Iterate based on feedback

---

## 11. Cost Breakdown (Month 1)

| Service | Plan | Monthly Cost |
|---------|------|--------------|
| Framer | Free or Mini ($5/mo) | $0-$5 |
| Zapier | Free (100 tasks) | $0 |
| OpenAI/Claude API | Pay-per-use | $10-$30 (est.) |
| Stripe | 2.9% + $0.30/transaction | Variable |
| SendGrid (optional) | Free (100 emails/day) | $0 |
| **Total** | | **$10-$35/mo** |

**Scaling:** At 100+ submissions/month, upgrade Zapier to Starter plan ($19.99/mo).

---

## 12. Support & Maintenance

**Contact Email:** support@coaihq.online
**Documentation:** This repo (`/docs` folder)
**Issue Tracking:** (Optional) GitHub Issues or Notion board

---

**Last Updated:** 2026-01-15
**Version:** 1.0 – Initial Architecture
