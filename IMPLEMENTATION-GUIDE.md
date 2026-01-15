# Complete Implementation Guide
## TenantShield Bakersfield - Build Instructions

**Estimated Time:** 2-3 hours total
**Goal:** Launch https://coaihq.online/bakersfield-tenant-help

---

## ⚡ Quick Setup Checklist

### 1. Domain & DNS (5 min)
- [ ] Log into your DNS provider (where you manage coaihq.online)
- [ ] Point domain to Framer per their instructions
- [ ] Verify domain connected in Framer settings

### 2. Build Framer Page (45 min)
- [ ] Create Framer project
- [ ] Set page route: `/bakersfield-tenant-help`
- [ ] Add SEO meta tags (title, description, OG tags)
- [ ] Build 8 sections: Nav, Hero, Form, Benefits, How It Works, Upsell, FAQ, Footer
- [ ] Configure form with 6 fields + checkbox
- [ ] Set form to submit to "Webhook" (paste Zapier URL after Step 3)
- [ ] Test responsive design
- [ ] Publish

### 3. Setup Zapier Workflow (60 min)
- [ ] Create Zapier account
- [ ] Create new Zap: "TenantShield - Form to AI Email"
- [ ] **Step 1:** Webhooks by Zapier → Catch Hook → Copy webhook URL
- [ ] Paste webhook URL into Framer form settings
- [ ] **Step 2:** (Optional) Formatter → Trim Whitespace on `situation`
- [ ] **Step 3:** OpenAI or Claude → AI Analysis (use prompt from AI-PROMPT-TEMPLATE.md)
- [ ] **Step 4:** Gmail/SendGrid → Send Email (use template from EMAIL-TEMPLATES.md)
- [ ] **Step 5:** (Optional) Google Sheets → Log submission
- [ ] Test with sample form submission
- [ ] Turn Zap ON

### 4. Create Stripe Payment Links (20 min)
- [ ] Create Stripe account
- [ ] Create Product 1: "Premium Letter Package" ($29)
- [ ] Create Payment Link for Product 1 → Copy URL
- [ ] Create Product 2: "15-Min Paralegal Call" ($15)
- [ ] Create Payment Link for Product 2 → Copy URL
- [ ] Paste both URLs into Zapier email template (Step 4)
- [ ] Update Zap

### 5. Add Analytics (10 min)
- [ ] Create Google Analytics 4 property
- [ ] Add GA4 tracking code to Framer site settings
- [ ] Track form submission event (custom event in Framer)

### 6. Testing (30 min)
- [ ] Submit 3 test forms with different scenarios
- [ ] Verify emails arrive within 2-5 minutes
- [ ] Check email formatting and AI analysis quality
- [ ] Test Stripe payment links (use test mode first)
- [ ] Mobile responsive check
- [ ] Desktop browser check (Chrome, Safari, Firefox)

---

## 📝 Detailed Instructions

### STEP 1: Domain & Routing

**In your DNS provider:**
1. Add CNAME record: `coaihq.online` → Framer's DNS target (they'll provide this)
2. Wait for DNS propagation (5-30 minutes)

**In Framer:**
1. Go to Site Settings → Custom Domain
2. Add `coaihq.online`
3. Create page route: `/bakersfield-tenant-help`
4. (Optional) Set `/` to redirect to `/bakersfield-tenant-help`

---

### STEP 2: Build Framer Page

#### SEO Settings (in Framer page settings):

```
Title: Bakersfield Tenant Help – AI Landlord Dispute Analysis | COAI HQ

Description: Stuck in a landlord fight in Bakersfield? Get AI-powered case analysis, a step-by-step plan, and connection to local tenant advocates in minutes. Not legal advice.

OG Title: Bakersfield Tenant Help – TenantShield by COAI HQ
OG URL: https://coaihq.online/bakersfield-tenant-help
OG Type: website
```

#### Page Structure:

**1. Navigation**
- Left: "COAI HQ" (text logo, links to `/`)
- Right: "How it works" (#how), "FAQ" (#faq), "Contact" (footer)

**2. Hero**
- Label: "TenantShield by COAI HQ"
- H1: "Stuck in a Landlord Fight in Bakersfield? Get a Clear Plan in 5 Minutes."
- Subhead: "AI-powered analysis plus a connection to Bakersfield tenant advocates. No lawyer fees, no guessing. Just clarity."
- Button: "Analyze My Case →" (scroll to form)

**3. Form Section** (ID: `form`)

**Fields:**
```
full_name - Text - Required - "Your Full Name"
email - Email - Required - "Email Address"
phone - Text - Optional - "Phone Number (optional)"
city - Text - Required - Default: "Bakersfield, CA"
situation - Textarea - Required - "Describe what's happening with your landlord or rental (dates, amounts, what they said, what you did)"
consent - Checkbox - Required - "I understand this is information only, not legal advice"
```

**Submit Button:** "Get My Plan →"

**Form Settings:**
- Submit to: Webhook
- Webhook URL: [Paste Zapier webhook URL from Step 3]

**Form Interactions:**
- On submit: Disable button, show text "Analyzing your case (30–60 seconds)..."
- On success: Show "Done. Check your email in the next few minutes for your analysis and next steps."
- Do NOT redirect

**4. Benefits Section**
- ✅ Instant situation breakdown in plain English
- ✅ Clear 3–5 step action plan for THIS week
- ✅ Copy-paste emails and letters ready to send today
- ✅ Optional connection to a Bakersfield tenant advocate
- ✅ Built for California tenant law (information only)

**5. How It Works** (ID: `how`)
- **Step 1:** Tell us what happened
- **Step 2:** AI analyzes your case
- **Step 3:** Get a plan + options

**6. Upsell Teaser**
- "Upgrade options are included in your email after analysis"

**7. FAQ** (ID: `faq`)
- **Q:** Is this legal advice? **A:** No, information only.
- **Q:** How fast? **A:** A few minutes by email.
- **Q:** Who will you connect me with? **A:** Tenant advocates/paralegals.
- **Q:** What does it cost? **A:** Basic AI analysis free; optional paid extras.

**8. Footer**
- "COAI HQ – Chaotically Organized AI"
- "TenantShield – Bakersfield Tenant Help"
- Contact: support@coaihq.online
- Disclaimer: "Not a law firm. Not legal advice. For information purposes only."

---

### STEP 3: Zapier Workflow Setup

#### Create Zap:

**Step 1: Webhook Trigger**
- App: Webhooks by Zapier
- Event: Catch Hook
- Copy webhook URL → Paste into Framer form settings
- Submit test form from Framer
- Click "Test trigger" in Zapier
- Verify all fields received: full_name, email, phone, city, situation, consent

**Step 2: (Optional) Format Text**
- App: Formatter by Zapier
- Transform: Trim Whitespace
- Input: `situation` field from Step 1

**Step 3: AI Analysis**

**Option A - OpenAI:**
- App: OpenAI
- Event: Send Prompt
- Model: `gpt-4-turbo` or `gpt-4o`
- Temperature: 0.7
- Max Tokens: 2000
- System Message: (Copy from AI-PROMPT-TEMPLATE.md)
- User Message:
  ```
  City: [1. City]
  Tenant Name: [1. Full Name]
  Issue Description: [2. Output]

  Analyze this tenant's situation and provide a detailed response.
  ```

**Option B - Claude (via Code by Zapier):**
- App: Code by Zapier
- Language: Python
- Code: (Copy from ZAPIER-SETUP.md, Step 5B.2)
- Input Data:
  - full_name: [1. Full Name]
  - situation: [2. Output]
  - city: [1. City]
  - api_key: [Your Claude API key]

**Step 4: Email to User**
- App: Gmail or SendGrid
- To: [1. Email]
- Subject: "Your Bakersfield Tenant Case – Analysis & Next Steps"
- Body:
  ```
  Hi [1. Full Name],

  Here's your AI-generated case analysis for your situation in Bakersfield (information only, not legal advice):

  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  [3. Analysis]
  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

  READY TO TAKE ACTION?

  1. Premium Letter Package ($29)
     [STRIPE_LINK_1]

  2. 15-Min Paralegal Call ($15)
     [STRIPE_LINK_2]

  Best,
  The TenantShield Team

  DISCLAIMER: This is information only, not legal advice.
  ```

**Step 5: (Optional) Log Submission**
- App: Google Sheets or Airtable
- Action: Create row
- Fields: Timestamp, Full Name, Email, Phone, City, Situation, AI Analysis

**Turn Zap ON**

---

### STEP 4: Stripe Payment Links

**In Stripe Dashboard:**

**Product 1:**
- Name: "Premium Letter Package – TenantShield"
- Price: $29 (one-time)
- Description: "Done-for-you demand letters and templates"
- Create Payment Link → Copy URL → Save as `STRIPE_LINK_1`

**Product 2:**
- Name: "15-Min Tenant Advocate Call – TenantShield"
- Price: $15 (one-time)
- Description: "Quick consultation with California paralegal"
- Create Payment Link → Copy URL → Save as `STRIPE_LINK_2`

**Update Zapier:**
- Go to Step 4 (Email to User)
- Replace `[STRIPE_LINK_1]` and `[STRIPE_LINK_2]` with actual URLs
- Save Zap

---

### STEP 5: Analytics

**In Google Analytics:**
1. Create GA4 property for coaihq.online
2. Copy Measurement ID (e.g., `G-XXXXXXXXXX`)

**In Framer:**
1. Go to Site Settings → Integrations → Google Analytics
2. Paste Measurement ID
3. (Optional) Add custom event for form submission

---

### STEP 6: Testing

**Test 1: End-to-End Flow**
1. Submit form with realistic data
2. Check email arrives within 2-5 minutes
3. Verify AI analysis is complete and formatted correctly
4. Click Stripe payment links → verify checkout loads

**Test 2: Edge Cases**
- Leave phone blank (should still work)
- Very long situation text (should process)
- Missing required fields (should show validation error)

**Test 3: Responsive**
- Mobile (iPhone, Android)
- Tablet
- Desktop (Chrome, Safari, Firefox)

**Test 4: AI Quality**
- Submit 3 different scenarios (security deposit, eviction, habitability)
- Manually review AI responses for accuracy

---

## 📊 Handover Checklist

When complete, provide:

- [ ] **Live URL:** https://coaihq.online/bakersfield-tenant-help
- [ ] **Screenshot:** Form submission + email received
- [ ] **Zapier Details:**
  - Zap name
  - Number of steps
  - AI model used (OpenAI/Claude)
  - Where AI prompt is stored
- [ ] **Stripe Payment Links:**
  - Premium Letter Package URL
  - Paralegal Call URL
- [ ] **Analytics:**
  - GA4 Measurement ID
  - Access shared to client email
- [ ] **Test Results:**
  - 3 test submissions completed
  - Email delivery confirmed
  - Stripe links tested

---

## ⚠️ Error Handling

**If AI API fails:**
- Configure fallback email in Zapier:
  "We're reviewing your case manually and will follow up within 24 hours."

**If email doesn't send:**
- Check Zapier Task History for errors
- Verify Gmail/SendGrid authorization

**If webhook times out:**
- Increase timeout in Zapier settings
- Reduce AI max tokens

---

## 💰 Cost Summary

| Service | Monthly Cost |
|---------|--------------|
| Framer | $5 |
| Zapier (Free tier) | $0 |
| OpenAI/Claude API | $10-30 |
| Stripe | 2.9% + $0.30/transaction |
| SendGrid | $0 |
| **Total** | **$15-35/mo** |

---

## 📞 Support

**Questions during build?**
- Email: support@coaihq.online
- Reference docs: ARCHITECTURE.md, FRAMER-PAGE-SPEC.md, ZAPIER-SETUP.md

---

**Version:** 1.0
**Last Updated:** 2026-01-15
