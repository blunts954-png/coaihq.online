# TENANTSHIELD BAKERSFIELD
AI-Powered Tenant Rights Platform - Complete Build Guide

## 🎯 PROJECT OVERVIEW

**What is TenantShield?**

TenantShield is a platform that helps Bakersfield tenants dealing with landlord disputes get instant AI-powered case analysis, actionable next steps, and connections to local tenant advocates—all for free.

**The Problem It Solves:**

Sierra, 34, renter in Southwest Bakersfield, is fighting a landlord over a withheld security deposit. She's working three jobs, has no time for lawyer consultations, and Googles "how to fight eviction" at 11 PM only to find contradictory Reddit threads. She needs immediate, trustworthy help.

**What We Provide:**

1. **Instant AI Analysis:** Upload your situation, get case strength rating (STRONG/MODERATE/WEAK) in 5 minutes
2. **Actionable Steps:** 3-5 specific actions to take THIS WEEK (not vague "talk to a lawyer")
3. **Draft Documents:** Copy-paste demand letters, emails, and templates ready to send TODAY
4. **Local Advocate Connections:** Free 15-min consultations with Bakersfield paralegals and tenant advocates

**Monetization:**

- **Free:** AI analysis + advocate intro (builds trust, generates leads)
- **$29:** Premium Letter Package (professionally formatted documents)
- **$15:** Extended paralegal consultation (10 minutes)
- **Provider Revenue Share:** 20% of fees when advocates close cases we refer

**Target Revenue:** $1,000-$2,500/month by Week 4

---

## 📁 PROJECT STRUCTURE

```
tenantshield-bakersfield/
├── ai-prompts/
│   ├── tenant-case-analyzer.txt       # Main AI system prompt (Claude/OpenAI)
│   ├── objection-handler.txt           # Handles user pushback
│   ├── upsell-trigger.txt              # Intelligent upsell logic
│   └── provider-handoff.txt            # Template for sending leads to paralegals
│
├── email-templates/
│   ├── user-response-email.txt         # Auto-reply after form submission
│   └── provider-pitch-email.txt        # Cold outreach to paralegals
│
├── landing-page-content/
│   └── homepage-copy.txt               # All copy for Framer landing page
│
├── setup-guides/
│   ├── framer-setup.md                 # Step-by-step Framer build
│   ├── zapier-workflow.md              # Zapier automation setup
│   └── stripe-setup.md                 # Payment link creation
│
├── provider-outreach/
│   ├── sample-cases.md                 # 5 sample cases for pitching
│   └── call-deck.md                    # Provider call script + slides
│
└── docs/
    ├── README.md                       # This file
    ├── deployment-checklist.md         # Pre-launch verification
    └── execution-timeline.md           # 24-hour sprint timeline
```

---

## 🚀 QUICK START (24-HOUR SPRINT)

### **Phase 1: Validation (Hours 0-2)**

**Goal:** Confirm niche demand before building

1. Post in 3 Bakersfield Facebook groups:
   > "Quick question: If you had a landlord dispute (security deposit, eviction, etc.), would you want an AI to instantly tell you if you have a real case + the exact next steps (free)?"

2. DM 5 Bakersfield paralegals on LinkedIn:
   > "Got 5 pre-screened tenant cases this week—want to try for free?"

**Success criteria:**
- ✅ 10+ engaged comments in FB groups
- ✅ 2+ paralegals respond with interest

**If you fail:** Pivot to Niche #2 (contractors) or iterate messaging.

---

### **Phase 2: Build Infrastructure (Hours 3-8)**

**Step 1: Framer Landing Page (90 min)**
- Follow: `setup-guides/framer-setup.md`
- Copy content from: `landing-page-content/homepage-copy.txt`
- Deliverable: Live landing page with form

**Step 2: Zapier Workflow (90 min)**
- Follow: `setup-guides/zapier-workflow.md`
- Use prompts from: `ai-prompts/tenant-case-analyzer.txt`
- Deliverable: Form submission triggers AI analysis + email

**Step 3: Stripe Payment Links (30 min)**
- Follow: `setup-guides/stripe-setup.md`
- Create: $29 Premium Letters + $15 Paid Consult
- Deliverable: Payment links ready to embed

**Step 4: Test End-to-End (30 min)**
- Submit test form
- Verify AI response emails
- Test payment links
- Fix any bugs

---

### **Phase 3: Provider Outreach (Hours 9-12)**

**Step 1: Find Providers (30 min)**

Search on:
- Google: "Bakersfield tenant rights attorney"
- LinkedIn: "paralegal Bakersfield"
- Yelp: "tenant advocate Bakersfield"
- Legal aid: "Kern County legal aid"

**Target:** 5-10 potential providers

**Step 2: Send Pitch Emails (30 min)**

Use template: `email-templates/provider-pitch-email.txt`

Customize:
- Use their name (not "Hi there")
- Reference their practice area (if known)
- Attach 2 sample cases from `provider-outreach/sample-cases.md`

**Step 3: Schedule Calls (60 min)**

For providers who respond:
- Offer Calendly link for 15-min call
- Use call deck: `provider-outreach/call-deck.md`
- Goal: Lock in 2-3 for test batch (5 free leads)

---

### **Phase 4: Launch Marketing (Hours 13-16)**

**Step 1: Organic Social (30 min)**

Post landing page link in:
- Bakersfield Facebook groups (3-5 groups)
- Nextdoor (Bakersfield area)
- Reddit: r/Bakersfield, r/legaladvice (carefully—no spam)

**Sample post:**
> "Dealing with a landlord issue in Bakersfield? I built a free tool that analyzes your case using California law and tells you if you have a claim. Check it out: [LINK]"

**Step 2: Google Ads (Optional, $5/day)**

- Target keywords: "landlord tenant dispute Bakersfield", "security deposit not returned Bakersfield"
- Ad copy: "Stuck in a Landlord Fight? Free Case Analysis in 5 Minutes"
- Landing page: Your Framer site

**Step 3: Monitor First Leads (60 min)**

- Watch Zapier task history
- Respond to form submissions within 10 minutes
- Forward first lead to provider ASAP (builds credibility)

---

### **Phase 5: Iterate & Scale (Hours 17-24)**

**Step 1: Review Metrics**

Check:
- Form submissions (goal: 3-5 in first 24 hours)
- Provider responses (goal: 2-3 interested)
- Email open rates (goal: >40%)
- Payment conversions (goal: 1-2 by Day 3)

**Step 2: Fix Bottlenecks**

Common issues:
- Low traffic → Increase ad spend or post in more groups
- Low form completion → Simplify form (fewer fields)
- Low email opens → Test subject lines
- No provider interest → Refine pitch or find new providers

**Step 3: Plan Week 2**

- Double down on what's working (ads, organic, providers)
- Cut what's not (bad providers, low-converting channels)
- Add features only if validated (e.g., Premium Letters package if people ask for it)

---

## 📊 SUCCESS METRICS

### **Week 1 Goals (Validation)**

- ✅ 20+ form submissions
- ✅ 2-3 providers onboarded (test batch)
- ✅ 1 provider converts a lead to paid case
- ✅ $50-$200 revenue (upsells + provider payments)

### **Week 4 Goals (Scale)**

- 100+ form submissions
- 5+ providers active
- 10-15 provider conversions
- $1,000-$2,500 revenue

### **Month 3 Goals (Optimize)**

- 300+ form submissions/month
- 10+ providers (with exclusive deals)
- 30-50 provider conversions
- $3,000-$5,000 revenue/month

---

## 🛠️ TECH STACK

| **Component** | **Tool** | **Cost** | **Why** |
|---------------|----------|----------|---------|
| Landing page | Framer | Free (or $5/mo for custom domain) | Fast, no-code, responsive |
| Form submission | Framer native | Included | Built-in form handling |
| AI analysis | Claude API | ~$0.10 per analysis | Best for legal reasoning |
| Email delivery | Zapier + Gmail | Free (or $20/mo Zapier Starter) | Reliable, easy to set up |
| Payment processing | Stripe | 2.9% + $0.30 per transaction | Industry standard, trusted |
| Scheduling | Calendly | Free | Simple booking for consults |
| Analytics | Google Analytics 4 | Free | Track conversions |
| **Total monthly cost** | | **$0-$30/mo** | Scales as you grow |

---

## 💰 MONETIZATION BREAKDOWN

### **Revenue Streams:**

1. **Premium Letter Package ($29)**
   - Target conversion: 10-15% of STRONG cases
   - Week 1: 0-1 sales ($0-$29)
   - Week 4: 5-10 sales ($145-$290)

2. **Paid Paralegal Consult ($15)**
   - Target conversion: 5-10% of MODERATE cases
   - Week 1: 0-1 sales ($0-$15)
   - Week 4: 3-5 sales ($45-$75)

3. **Provider Revenue Share (20% of fees)**
   - Average paralegal case value: $250-$500
   - Your cut: $50-$100 per conversion
   - Week 1: 1 conversion ($50-$100)
   - Week 4: 5-10 conversions ($250-$1,000)

**Total Week 1 Revenue:** $50-$144
**Total Week 4 Revenue:** $440-$1,365

---

## 🎓 LEGAL DISCLAIMERS (CRITICAL)

**IMPORTANT:** You are NOT providing legal advice. TenantShield is educational only.

**Include on every page:**

> TenantShield provides educational information about California tenant rights. This is NOT legal advice and does not create an attorney-client relationship. For legal advice specific to your situation, consult a licensed California attorney.

**Add to every email:**

> IMPORTANT DISCLAIMER: This is educational analysis, not legal advice. Consult a licensed attorney before taking legal action.

**Never say:**
- ❌ "You should sue"
- ❌ "You will win"
- ❌ "I recommend you..."

**Always say:**
- ✅ "Based on California law, your position appears..."
- ✅ "Consult an attorney to confirm..."
- ✅ "This is educational analysis, not legal advice"

---

## 🚨 COMMON PITFALLS (AVOID THESE)

1. **Over-engineering:** Don't add features no one asked for. Start simple.
2. **No provider validation:** Confirm 2+ providers BEFORE building.
3. **Weak traffic strategy:** Don't rely on "build it and they will come." Post in 5+ groups Day 1.
4. **Bad provider relationships:** If a provider ghosts users or gives bad service, cut them immediately.
5. **Legal liability:** Never give legal advice. Stay educational. Get insurance if you scale.
6. **Chasing weak leads:** Only send STRONG + MODERATE cases to providers. Filter aggressively.

---

## 📞 SUPPORT & RESOURCES

**Documentation:**
- Framer: https://framer.com/docs
- Zapier: https://zapier.com/help
- Stripe: https://stripe.com/docs
- Claude API: https://docs.anthropic.com

**Community:**
- Indie Hackers: https://indiehackers.com (share progress, get feedback)
- Bakersfield Local Groups: Facebook, Nextdoor (recruit users + providers)

**Legal Resources:**
- California Tenant Law: https://leginfo.legislature.ca.gov (source of truth)
- Nolo: https://nolo.com (great for legal research)

---

## 🎯 NEXT STEPS

1. **Read this README fully** (you are here)
2. **Review deployment checklist:** `docs/deployment-checklist.md`
3. **Follow 24-hour timeline:** `docs/execution-timeline.md`
4. **Build Framer site:** `setup-guides/framer-setup.md`
5. **Set up Zapier:** `setup-guides/zapier-workflow.md`
6. **Launch!**

---

## 📝 FINAL NOTES

**This is a sprint, not a marathon.**

The goal is to validate demand in 24-48 hours, not build a perfect SaaS. You'll iterate based on real user feedback.

**Execution beats perfection.**

A live, imperfect site beats a perfect site you never launch.

**You've got this. Now go build.** 🚀

---

**Last updated:** 2026-01-14
**Version:** 1.0
**Contact:** hello@tenantshield.com
