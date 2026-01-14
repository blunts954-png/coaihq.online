# EXECUTION TIMELINE
24-Hour Sprint to Launch TenantShield

## OVERVIEW

**Start time:** Wednesday, 1:00 PM
**Launch time:** Thursday, 1:00 PM (24 hours later)
**Goal:** Live website + 1 provider onboarded + first lead

**Prerequisites:**
- You've read `docs/README.md`
- You have Framer, Zapier, Stripe accounts created
- You have Claude API key or OpenAI API key
- You're mentally prepared to move fast

---

## 📅 TIMELINE AT-A-GLANCE

| **Time Block** | **Duration** | **Focus** | **Deliverable** |
|----------------|--------------|-----------|-----------------|
| 1:00-2:30 PM | 90 min | Validation | 10+ FB comments, 2+ provider interest |
| 2:30-4:00 PM | 90 min | Tech Setup | Framer site live with form |
| 4:00-5:30 PM | 90 min | AI Wiring | Zapier → Claude → Email working |
| 5:30-7:00 PM | 90 min | Provider Outreach | 5 pitches sent, Stripe ready |
| 7:00-8:30 PM | 90 min | Polish & Deploy | End-to-end test passed |
| 8:30-10:00 PM | 90 min | Social Push | Posted in 5+ groups, ads live |
| **OVERNIGHT** | - | Sleep (or iterate) | - |
| 8:00-11:00 AM | 3 hours | Provider Calls | 1-2 providers committed |
| 11:00 AM-1:00 PM | 2 hours | First Lead Handling | Lead sent to provider |

---

## BLOCK 1: VALIDATION BLITZ (1:00-2:30 PM)

**Objective:** Confirm demand before building

### **Tasks:**

**1. Social Validation (60 min)**

Post in Bakersfield Facebook groups:

> "Quick question for Bakersfield renters: If you had a landlord dispute (security deposit, eviction, etc.), would you want an AI to instantly tell you if you have a real case + the exact next steps (free)? Curious what problems you'd trust AI help with."

**Where to post:**
- Facebook: "Bakersfield Residents" group
- Facebook: "Bakersfield Community" group
- Facebook: "Bakersfield Buy/Sell/Trade" (if allowed)
- Nextdoor: Bakersfield area
- Reddit: r/Bakersfield (carefully—add value, don't spam)

**Success metric:** 10+ engaged comments (questions, upvotes, interest)

**If <10 comments after 1 hour:** Post in 3 more groups or pivot messaging.

---

**2. Provider Validation (30 min)**

DM 5 Bakersfield paralegals on LinkedIn:

> "Hi [Name], I'm launching a service that pre-screens tenant cases using AI and sends qualified leads to Bakersfield advocates. Would you be interested in receiving 5 free leads this week to test it out? No obligation."

**How to find them:**
- LinkedIn search: "paralegal Bakersfield"
- Google search: "Bakersfield tenant rights attorney"
- Yelp: "tenant advocate Bakersfield"

**Success metric:** 2+ respond with "tell me more" or "yes"

**If 0 responses after 2 hours:** Follow up with 5 more, or pivot to different provider type (legal aid orgs).

---

**Checkpoint at 2:30 PM:**
- ✅ 10+ social comments = GREEN LIGHT, continue
- ❌ <5 comments + 0 provider interest = YELLOW LIGHT, re-evaluate niche or messaging
- ❌ Total crickets = RED LIGHT, pivot to different niche (contractors, small business)

**DECISION:** Only continue if you see green or yellow. If red, stop and reassess.

---

## BLOCK 2: TECH SETUP (2:30-4:00 PM)

**Objective:** Get infrastructure live (skeleton only, not polished)

### **Tasks:**

**1. Create Framer Project (30 min)**

Follow: `setup-guides/framer-setup.md`

- Create new Framer project
- Set up basic layout (hero + form + 3 sections)
- DON'T obsess over design—clarity over beauty
- Use placeholder copy for now (you'll refine later)

**Deliverable:** Framer project created, layout roughed in

---

**2. Build Form (30 min)**

Add form to Framer:

Fields (copy from `landing-page-content/homepage-copy.txt`):
- First Name
- Last Name
- Email
- Phone
- Issue Type (dropdown)
- Situation (textarea)
- Timeline (dropdown)
- Previous Legal Help (radio)
- Consent (checkbox)

**Deliverable:** Form visible on page, all fields added

---

**3. Connect Zapier Webhook (20 min)**

1. Create Zapier Zap: Webhooks → Catch Hook
2. Copy webhook URL
3. Paste into Framer form settings (action URL)
4. Test: Submit form, verify Zapier catches it

**Deliverable:** Form submission triggers Zapier

---

**4. Add Placeholder Copy (10 min)**

Paste content from `landing-page-content/homepage-copy.txt`:
- Hero headline + subheadline
- Benefit bullets
- CTA button text

**Deliverable:** Site has basic copy (not perfect, just readable)

---

**Checkpoint at 4:00 PM:**
- ✅ Framer site exists
- ✅ Form is functional
- ✅ Zapier webhook catches form data

---

## BLOCK 3: AI WIRING (4:00-5:30 PM)

**Objective:** Hook form to Claude API, send AI analysis via email

### **Tasks:**

**1. Set Up Zapier → Claude Integration (30 min)**

Follow: `setup-guides/zapier-workflow.md`

- Add Zapier step: Code by Zapier (Python) OR OpenAI app
- Load system prompt from `ai-prompts/tenant-case-analyzer.txt`
- Map form fields to AI input
- Test: Submit form, verify AI analysis returns

**Deliverable:** AI analysis working

---

**2. Create Email Template (20 min)**

Add Zapier step: Gmail → Send Email

Copy email template from `email-templates/user-response-email.txt`:
- Subject: "Your Case Analysis is Ready - TenantShield"
- Body: Include AI analysis + next steps
- Add placeholders: {{firstName}}, {{analysis}}

**Deliverable:** Email template created

---

**3. Test End-to-End (20 min)**

1. Submit test form (use your own email)
2. Wait 30-60 seconds
3. Check inbox: Did you receive email with AI analysis?
4. If YES: ✅ Move on
5. If NO: Debug (check Zapier task history for errors)

**Deliverable:** End-to-end flow working (form → AI → email)

---

**4. Add Lead Notification Email (20 min)**

Add Zapier step: Gmail → Send Email (to yourself)

- Subject: "🚨 New Lead: {{firstName}} {{lastName}}"
- Body: Include user info + AI analysis (use template from `ai-prompts/provider-handoff.txt`)

**Deliverable:** You get notified when leads come in

---

**Checkpoint at 5:30 PM:**
- ✅ Form → AI → Email flow works
- ✅ You receive lead notifications
- ✅ Zapier is live and turned ON

---

## BLOCK 4: PROVIDER OUTREACH & PAYMENT (5:30-7:00 PM)

**Objective:** Lock in 1 provider, set up payment links

### **Tasks:**

**1. Send Provider Emails (30 min)**

Use template from `email-templates/provider-pitch-email.txt`

Send to 5 paralegals/advocates:
- Personalize (use their name, reference their practice)
- Include 2 sample cases from `provider-outreach/sample-cases.md`
- End with: "Can we hop on a quick call tomorrow at 10 AM?"

**Deliverable:** 5 emails sent

---

**2. Set Up Stripe (30 min)**

Follow: `setup-guides/stripe-setup.md`

Create products:
- Premium Letter Package ($29)
- Paid Paralegal Consult ($15)

Generate payment links for both.

**Deliverable:** 2 Stripe payment links ready

---

**3. Add Payment Links to Email Template (20 min)**

Go back to Zapier email step, add Stripe links:
- Option 2: [Get Premium Letters - $29] → Stripe link
- Option 3: [Paid Consult - $15] → Stripe link

Save and test.

**Deliverable:** Payment links embedded in user email

---

**4. Set Up Calendly (10 min)**

1. Create Calendly account (free)
2. Set up event: "15-Minute Tenant Rights Consultation"
3. Copy Calendly link
4. Add to email template (Option 1: Free Consult)

**Deliverable:** Calendly link embedded in user email

---

**Checkpoint at 7:00 PM:**
- ✅ 5 provider pitches sent
- ✅ Stripe payment links live
- ✅ Calendly link added to emails
- ✅ End-to-end test passed (with payment links)

---

## BLOCK 5: POLISH & DEPLOY (7:00-8:30 PM)

**Objective:** Refine copy, test everything, deploy live

### **Tasks:**

**1. Refine Landing Page Copy (30 min)**

Copy all content from `landing-page-content/homepage-copy.txt`:
- Hero section
- How It Works (4 steps)
- Benefits (5 benefits)
- FAQ (10 questions)
- Footer (disclaimer, contact, links)

Paste into Framer. Don't obsess—just make it readable.

**Deliverable:** Full landing page content added

---

**2. Add Legal Disclaimers (10 min)**

Add to:
- Homepage (visible above the fold)
- Footer (small text)
- Email template (bottom of email)

Text:
> TenantShield provides educational information about California tenant rights. This is NOT legal advice and does not create an attorney-client relationship. Consult a licensed attorney for legal advice.

**Deliverable:** Disclaimers visible everywhere

---

**3. Full End-to-End Test (30 min)**

1. Go to Framer site (incognito browser)
2. Fill out form with realistic data
3. Submit
4. Check email (user side): Did you get analysis + payment links?
5. Click Calendly link: Does it work?
6. Click Stripe link: Does payment page load?
7. Submit test payment (use test card: 4242 4242 4242 4242)
8. Verify payment shows in Stripe dashboard

**If anything breaks:** Fix it now.

**Deliverable:** ✅ End-to-end flow verified

---

**4. Publish Framer Site (10 min)**

1. Click "Publish" in Framer
2. Choose domain (Framer subdomain or custom)
3. Wait 30 seconds for deployment
4. Test live site on mobile + desktop

**Deliverable:** 🚀 **SITE IS LIVE**

---

**5. Set Up Google Analytics (10 min)**

1. Create GA4 account
2. Copy Measurement ID
3. Paste into Framer (Settings → Analytics)
4. Verify tracking (visit site, check GA4 Real-Time report)

**Deliverable:** Analytics tracking live

---

**Checkpoint at 8:30 PM:**
- ✅ Site is published and live
- ✅ End-to-end test passed
- ✅ Disclaimers visible
- ✅ Analytics tracking

**YOU NOW HAVE A LIVE PRODUCT.** 🎉

---

## BLOCK 6: SOCIAL PUSH (8:30-10:00 PM)

**Objective:** Drive traffic to your live site

### **Tasks:**

**1. Post to Social Media (30 min)**

Post in 5+ Bakersfield groups:

> "I just launched a free tool for Bakersfield renters dealing with landlord issues (security deposit, eviction, etc.). It uses AI to analyze your case and tell you if you have a claim under California law. Takes 2 minutes. Check it out: [LINK]"

**Where to post:**
- Facebook groups (3-5 groups)
- Nextdoor (Bakersfield)
- Reddit r/Bakersfield
- Twitter/X (use hashtags: #Bakersfield, #TenantRights, #California)

**Deliverable:** Posted in 5+ places

---

**2. Email Tenant Advocate Orgs (20 min)**

Find 3-5 local tenant advocacy orgs:
- "Bakersfield Legal Aid"
- "Kern County Tenant Union"
- "California Rural Legal Assistance"

Send email:
> "Hi [Org], I just launched a free tool that helps Bakersfield tenants analyze landlord disputes using AI. Thought you might want to share with your network. Link: [SITE]"

**Deliverable:** 3-5 emails sent

---

**3. Set Up Google Ads (Optional, 30 min)**

If you have $5-$10 to spend:

1. Create Google Ads account
2. Set up Search campaign
3. Target keywords: "landlord tenant dispute Bakersfield", "security deposit not returned"
4. Ad copy: "Stuck in a Landlord Fight? Free Case Analysis in 5 Minutes"
5. Budget: $5/day
6. Launch

**Deliverable:** Google Ads running (optional)

---

**4. Monitor First Submissions (20 min)**

- Set up notifications: Zapier sends you SMS or Slack alert when form submits
- Keep phone nearby
- Respond to first submission within 10 minutes (manual follow-up if needed)

**Deliverable:** Alert system set up

---

**Checkpoint at 10:00 PM:**
- ✅ Posted in 5+ groups
- ✅ Emailed 3-5 orgs
- ✅ Ads running (optional)
- ✅ Monitoring for leads

**NOW: WAIT.** Go to sleep (or keep iterating if you have energy).

---

## OVERNIGHT (10:00 PM - 8:00 AM)

### **Possible Activities:**

1. **Sleep** (recommended—you'll need energy tomorrow)
2. **Monitor submissions** (check email/Zapier every hour)
3. **Respond to provider emails** (if any came in)
4. **Post in more groups** (if you have energy)
5. **Refine copy** (tweak headline, CTA, etc.)

**Don't stress if you get 0 submissions overnight.** Most traffic comes during daytime hours.

---

## BLOCK 7: PROVIDER CALLS (8:00-11:00 AM THURSDAY)

**Objective:** Lock in 1-2 providers for test batch

### **Tasks:**

**1. Check Provider Responses (30 min)**

- Review emails from providers
- Respond to any questions
- Schedule calls for 9 AM, 10 AM, 11 AM

**Deliverable:** 2-3 calls scheduled

---

**2. Provider Call #1 (30 min)**

Use script from `provider-outreach/call-deck.md`

**Pitch:**
- Explain TenantShield
- Show sample case
- Offer test batch (5 free leads)
- Close: "Can I send you 1 lead this week?"

**Deliverable:** 1 provider agrees to test batch

---

**3. Provider Call #2 (30 min)**

Same as above. Goal: Get 2nd provider.

**Deliverable:** 2nd provider agrees (ideally)

---

**4. Send First Lead (30 min)**

If you got a real user submission overnight:
- Use template from `ai-prompts/provider-handoff.txt`
- Forward to provider
- Include: user info, AI analysis, case strength
- Ask provider to contact user within 24 hours

**Deliverable:** ✅ **FIRST LEAD SENT TO PROVIDER**

---

**5. Follow-Up with Providers (30 min)**

Send recap email to providers who agreed:

> "Great talking today! Here's what we agreed on:
> - I'll send you [1-5] leads this week
> - You'll provide free 15-min consults
> - No cost for test batch
>
> First lead coming [today/tomorrow].
>
> Talk soon!"

**Deliverable:** Confirmation emails sent

---

**Checkpoint at 11:00 AM:**
- ✅ 1-2 providers committed
- ✅ First lead sent (if available)
- ✅ Follow-up emails sent

---

## BLOCK 8: FIRST LEAD HANDLING (11:00 AM - 1:00 PM)

**Objective:** Ensure first user + provider have great experience

### **Tasks:**

**1. User Follow-Up (if you got submissions)**

If a user submitted a form:
- Reply to their auto-response email with a personal note:
  > "Hi [Name], I saw your situation about [issue]. Your case looks [strong/moderate]. A local advocate will reach out within 24 hours. Let me know if you have questions!"

**Deliverable:** Personalized follow-up sent

---

**2. Provider Check-In**

Text or call provider:
> "Hey [Name], just sent you [User]'s case. Let me know when you connect with them!"

**Deliverable:** Provider reminded to contact user

---

**3. Review Metrics (30 min)**

Check:
- **Form submissions:** How many in first 24 hours?
- **Provider interest:** How many responded?
- **Email open rates:** Are users opening emails?
- **Payment clicks:** Any Stripe link clicks?

**Deliverable:** Metrics tracked in spreadsheet

---

**4. Iterate Based on Feedback (60 min)**

Common issues and fixes:

| **Issue** | **Fix** |
|-----------|---------|
| Low traffic | Post in 5 more groups, increase ad spend |
| Form not converting | Simplify form (fewer fields), add examples |
| Emails going to spam | Change sender email to custom domain |
| Providers not responding | Follow up, offer higher revenue share |

**Deliverable:** 1-2 quick improvements made

---

**Checkpoint at 1:00 PM (24 HOURS LATER):**

---

## 🎉 24-HOUR SPRINT COMPLETE!

### **What You Should Have:**

- ✅ Live website with working form
- ✅ Zapier workflow (form → AI → email)
- ✅ Stripe payment links
- ✅ 1-2 providers onboarded (test batch)
- ✅ First lead sent to provider (if available)
- ✅ 5-20 form submissions (goal)
- ✅ $0-$100 revenue (realistic for Day 1)

---

## 📊 SUCCESS CRITERIA (DAY 1)

**Minimum viable success (you did it!):**
- ✅ Site is live
- ✅ End-to-end flow works
- ✅ 1 provider interested
- ✅ 1+ form submissions

**Strong success (you crushed it!):**
- ✅ 10+ form submissions
- ✅ 2+ providers committed
- ✅ 1 lead sent to provider
- ✅ 1 upsell sale ($15-$29)

**Exceptional success (wow!):**
- ✅ 20+ form submissions
- ✅ 3+ providers committed
- ✅ 3+ leads sent
- ✅ $50-$200 revenue

---

## 📅 NEXT 7 DAYS

### **Day 2-3: Iterate**
- Fix bugs users report
- Test different headlines
- Post in more groups
- Follow up with providers

### **Day 4-5: Scale**
- Increase ad spend to $20/day (if ads are working)
- Onboard 2-3 more providers
- Send 5-10 more leads

### **Day 6-7: Optimize**
- Review metrics (what's working?)
- Double down on best channels
- Cut what's not working
- Plan Week 2 strategy

---

## 🚨 IF THINGS GO WRONG

**Scenario 1: Zero form submissions in 24 hours**

**Fix:**
- Post in 10 more groups (cast wider net)
- DM people directly on Facebook: "Hey, saw you asking about landlord issues. I built a free tool that might help: [LINK]"
- Increase ad spend to $20/day
- Test different headline: "Landlord Won't Return Your Deposit? Find Out If You Can Sue (Free)"

**Scenario 2: Providers ghost you**

**Fix:**
- Follow up: "Hey [Name], still interested in those leads?"
- Offer better terms: "First 10 leads free instead of 5?"
- Find new providers: Call local legal aid orgs directly

**Scenario 3: Tech breaks (Zapier fails, emails bounce, etc.)**

**Fix:**
- Check Zapier task history for errors
- Test with different email (maybe Gmail is blocking)
- Manually respond to users while you debug
- Post in Zapier community for help

**Scenario 4: Users complain ("This isn't helpful!" or "AI is wrong!")**

**Fix:**
- Respond quickly: "Thanks for the feedback! Can you tell me what was missing?"
- Improve AI prompt based on feedback
- Offer manual review: "Let me personally review your case and get back to you in 24 hours."

---

## ✅ FINAL CHECKLIST (END OF DAY 1)

- [ ] Site is live and functional
- [ ] At least 1 provider onboarded
- [ ] At least 1 form submission
- [ ] No major bugs or errors
- [ ] You survived 24 hours without quitting 😅

**If all checked: YOU DID IT.** 🎉

---

## 🚀 WHAT'S NEXT?

1. **Sleep** (you earned it)
2. **Review metrics** (what worked? what didn't?)
3. **Iterate** (fix bugs, improve copy, test new channels)
4. **Scale** (more providers, more ads, more traffic)

**Week 1 goal:** $50-$200 revenue
**Week 4 goal:** $1,000-$2,500 revenue
**Month 3 goal:** $3,000-$5,000 revenue

---

**You've got the foundation. Now it's about execution and iteration.**

**Good luck! 🚀**

---

**Timeline last updated:** 2026-01-14
