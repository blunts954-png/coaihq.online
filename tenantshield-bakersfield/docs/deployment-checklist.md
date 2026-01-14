# DEPLOYMENT CHECKLIST
Pre-Launch Verification for TenantShield

## OVERVIEW

Use this checklist before launching TenantShield to the public. Every item must be checked off.

**Estimated time to complete:** 30-45 minutes
**Best done:** Right before you post the site publicly

---

## ✅ 1. FRAMER SITE VERIFICATION

### **Landing Page:**

- [ ] Hero headline is clear and compelling
- [ ] Subheadline explains value proposition
- [ ] Benefit bullets are visible (5 bullets)
- [ ] CTA button is prominent ("Analyze My Case")
- [ ] Form is embedded and visible (not hidden)

### **Form Functionality:**

- [ ] All 9 form fields are present:
  - [ ] First Name (required)
  - [ ] Last Name (required)
  - [ ] Email (required)
  - [ ] Phone (required)
  - [ ] Issue Type dropdown (required)
  - [ ] Situation textarea (required)
  - [ ] Timeline dropdown (required)
  - [ ] Previous legal help (required)
  - [ ] Consent checkbox (required)
- [ ] Submit button works (no errors on click)
- [ ] Success message appears after submission
- [ ] Form data is sent to Zapier webhook (verify in Zapier task history)

### **Content Sections:**

- [ ] "How It Works" section (4 steps with icons)
- [ ] Benefits section (5 benefits)
- [ ] FAQ section (10 questions with answers)
- [ ] Footer with contact info + disclaimer

### **Legal Compliance:**

- [ ] Disclaimer is visible on homepage: "NOT LEGAL ADVICE"
- [ ] Disclaimer in footer
- [ ] Privacy policy linked (even if basic)
- [ ] Terms of service linked (even if basic)

### **Mobile Responsiveness:**

- [ ] Test on mobile device (or browser mobile view)
- [ ] Text is readable (minimum 16px font)
- [ ] Buttons are tap-friendly (minimum 44px height)
- [ ] Form fields work on mobile (no weird zooming)
- [ ] No horizontal scrolling

### **Performance:**

- [ ] Page loads in <3 seconds (test with PageSpeed Insights)
- [ ] Images are optimized (not huge file sizes)
- [ ] No console errors (F12 → Console tab)

---

## ✅ 2. ZAPIER WORKFLOW VERIFICATION

### **Trigger (Webhook):**

- [ ] Zapier webhook is turned ON
- [ ] Webhook URL is correctly pasted in Framer form settings
- [ ] Test submission triggers Zapier (check task history)
- [ ] All form fields are captured in Zapier (firstName, email, situation, etc.)

### **AI Analysis Step:**

- [ ] Claude/OpenAI API key is valid and active
- [ ] System prompt is loaded (from `ai-prompts/tenant-case-analyzer.txt`)
- [ ] Test submission returns AI analysis (not an error)
- [ ] AI analysis includes:
  - [ ] Situation summary
  - [ ] California law citation
  - [ ] Case strength (STRONG/MODERATE/WEAK)
  - [ ] Action plan (3-5 steps)
  - [ ] Draft email/letter
  - [ ] Disclaimer

### **Email to User:**

- [ ] Email is sent to user's email address (from form)
- [ ] Email subject line is clear: "Your Case Analysis is Ready - TenantShield"
- [ ] Email body includes:
  - [ ] Greeting with first name
  - [ ] Full AI analysis
  - [ ] Next steps (Option 1: Free consult, Option 2: Premium, Option 3: Paid consult)
  - [ ] Working links (Calendly, Stripe)
  - [ ] Disclaimer at bottom
- [ ] Email doesn't go to spam (check spam folder)
- [ ] Email is formatted nicely (HTML not broken)

### **Email to You (Lead Notification):**

- [ ] Email is sent to your email address
- [ ] Subject line includes user name + issue type
- [ ] Body includes:
  - [ ] User contact info
  - [ ] User's situation
  - [ ] AI analysis
  - [ ] Next steps for you
- [ ] Email arrives within 30 seconds of form submission

### **Zapier Task Limits:**

- [ ] You're aware of your task limit (100/month on free tier)
- [ ] You know when to upgrade (if you exceed limit)

---

## ✅ 3. STRIPE PAYMENT LINKS VERIFICATION

### **Premium Letter Package ($29):**

- [ ] Product created in Stripe
- [ ] Payment link generated
- [ ] Payment link works (test with test card: 4242 4242 4242 4242)
- [ ] Success message appears after payment
- [ ] Payment shows up in Stripe Dashboard → Payments
- [ ] Payment link is embedded in:
  - [ ] User email template
  - [ ] Framer landing page (optional)

### **Paid Paralegal Consult ($15):**

- [ ] Product created in Stripe
- [ ] Payment link generated
- [ ] Payment link works (test with test card)
- [ ] Success message appears after payment
- [ ] Payment link is embedded in user email template

### **Stripe Settings:**

- [ ] You're in LIVE MODE (not test mode) for production
- [ ] Bank account added for payouts
- [ ] Email notifications enabled (for successful payments)
- [ ] Tax settings configured (if applicable)

### **Delivery Automation (Optional but Recommended):**

- [ ] Zapier workflow set up for Premium Letters delivery
  - Trigger: Stripe - New Payment
  - Action: Send email with Google Drive download link
- [ ] Google Drive folder set up with Premium Letter Package
- [ ] Download link works (test it)

---

## ✅ 4. PROVIDER ONBOARDING VERIFICATION

### **Provider Pipeline:**

- [ ] 5+ Bakersfield paralegals/advocates identified
- [ ] Pitch emails sent to at least 5 providers
- [ ] At least 2 providers responded with interest
- [ ] At least 1 provider agreed to test batch (5 free leads)

### **Provider Communication:**

- [ ] Provider has your contact info (email + phone)
- [ ] You have provider's contact info
- [ ] Provider knows what to expect:
  - [ ] Free 15-min consultations
  - [ ] Pre-screened leads with AI analysis
  - [ ] Test batch = 5 leads, no cost
- [ ] Provider handoff template is ready (`ai-prompts/provider-handoff.txt`)

---

## ✅ 5. ANALYTICS & TRACKING

### **Google Analytics 4:**

- [ ] GA4 account created
- [ ] Measurement ID added to Framer (Settings → Analytics)
- [ ] GA4 Real-Time report shows activity (test by visiting your site)
- [ ] Conversion events set up (form submission, payment)

### **Internal Tracking:**

- [ ] Spreadsheet or Airtable ready to track:
  - [ ] User submissions (name, email, issue, date)
  - [ ] Provider conversions (which leads converted to cases)
  - [ ] Revenue (upsells + provider payments)

---

## ✅ 6. LEGAL & COMPLIANCE

### **Disclaimers:**

- [ ] "NOT LEGAL ADVICE" disclaimer on homepage
- [ ] Disclaimer in every email
- [ ] Disclaimer in footer
- [ ] Consent checkbox in form (user acknowledges educational nature)

### **Privacy Policy:**

- [ ] Privacy policy page created (even if basic)
- [ ] Covers:
  - [ ] What data you collect (name, email, phone, issue description)
  - [ ] How you use it (AI analysis, provider referrals)
  - [ ] Who you share it with (local advocates, with consent)
  - [ ] User rights (can request deletion)

### **Terms of Service:**

- [ ] Terms of service page created
- [ ] Covers:
  - [ ] Service is educational, not legal advice
  - [ ] No guarantees of outcomes
  - [ ] User responsible for their own legal decisions

**Note:** For Week 1, basic policies are fine. Hire a lawyer to review if you scale.

---

## ✅ 7. MARKETING READINESS

### **Social Posts Drafted:**

- [ ] 3-5 social posts ready to publish:
  - [ ] Facebook groups (Bakersfield Residents, etc.)
  - [ ] Nextdoor (Bakersfield area)
  - [ ] Reddit (r/Bakersfield, r/legaladvice—carefully)

### **Ad Campaign (Optional):**

- [ ] Google Ads account set up
- [ ] Search ad created (keywords: "landlord tenant dispute Bakersfield")
- [ ] Ad copy written
- [ ] Budget set ($5-$10/day to start)
- [ ] Ad approved by Google (takes 24 hours)

### **Outreach Lists:**

- [ ] 5-10 Bakersfield FB groups identified
- [ ] 3-5 tenant advocate organizations identified
- [ ] 5-10 local news/blog contacts (for potential PR)

---

## ✅ 8. END-TO-END TESTING

### **Full User Flow Test:**

1. [ ] Go to Framer site (incognito mode)
2. [ ] Fill out form with real test data
3. [ ] Submit form
4. [ ] Verify success message appears
5. [ ] Check email inbox (user email)
   - [ ] Received email with AI analysis
   - [ ] Links work (Calendly, Stripe)
6. [ ] Check your email inbox (lead notification)
   - [ ] Received lead notification
   - [ ] All user info present
7. [ ] Click Stripe payment link
   - [ ] Payment page loads
   - [ ] Test payment works (use test card if in test mode)
8. [ ] Verify payment shows up in Stripe Dashboard
9. [ ] (Optional) Verify delivery email sent for Premium Letters

**If ANY step fails, fix before launching.**

---

## ✅ 9. BACKUP & RECOVERY

### **Data Backup:**

- [ ] Framer project backed up (export if possible)
- [ ] Zapier workflows documented (screenshots or notes)
- [ ] Email templates saved locally
- [ ] AI prompts saved locally (already done if using this repo)

### **Failure Plans:**

- [ ] If Zapier breaks: Have manual email template ready to respond to users
- [ ] If Stripe breaks: Have PayPal or Venmo as backup (manual invoicing)
- [ ] If Framer breaks: Have backup landing page (Carrd, Wix, etc.)

---

## ✅ 10. LAUNCH READINESS

### **Personal Readiness:**

- [ ] Calendar cleared for next 48 hours (you'll need to respond quickly)
- [ ] Phone/email notifications ON (don't miss leads)
- [ ] Coffee ready ☕ (you might be up late)

### **Support Readiness:**

- [ ] hello@tenantshield.com email set up (or your contact email)
- [ ] Auto-responder optional (e.g., "Thanks for reaching out! I'll respond within 24 hours.")
- [ ] FAQ doc ready for common user questions

### **Mental Prep:**

- [ ] Accept that Week 1 will be messy (that's normal)
- [ ] Expect bugs (fix them as they come)
- [ ] Prepare for criticism (some people will hate it—ignore them)
- [ ] Celebrate small wins (first form submission, first provider interest, first dollar)

---

## 🚀 FINAL PRE-LAUNCH CHECK

**Before you post your first social media link, verify:**

- [ ] ✅ All sections above are checked off
- [ ] ✅ You've tested end-to-end flow at least once
- [ ] ✅ You have at least 1 provider ready to receive leads
- [ ] ✅ You're mentally prepared to iterate based on feedback

**If all checked: YOU'RE READY TO LAUNCH.** 🎉

---

## 📊 POST-LAUNCH MONITORING (FIRST 24 HOURS)

### **Metrics to watch:**

- [ ] Form submissions (goal: 3-5 in first 24 hours)
- [ ] Email deliverability (are emails landing in inbox or spam?)
- [ ] Provider responses (did you forward first lead?)
- [ ] User questions (what are people confused about?)
- [ ] Payment conversions (any sales in first 48 hours?)

### **Common issues in first 24 hours:**

| **Issue** | **Fix** |
|-----------|---------|
| No form submissions | Increase social posts, add urgency, test different FB groups |
| Emails go to spam | Send from custom domain (not Gmail), check SPF/DKIM records |
| Users confused by form | Simplify form (fewer fields), add examples |
| Providers don't respond | Follow up, offer to hop on quick call |
| No sales | Expected—most sales come Days 3-7, not Day 1 |

---

## ✅ WEEK 1 SUCCESS CRITERIA

If you hit these by Day 7, you're on track:

- [ ] 10-20 form submissions
- [ ] 1-2 provider conversations
- [ ] 1 lead sent to provider
- [ ] $50-$200 revenue (from any source)

**If you don't hit these:** Iterate. Don't give up. Week 1 is about learning, not perfection.

---

## 📞 NEED HELP?

If you're stuck:

1. **Check docs:** Re-read setup guides (Framer, Zapier, Stripe)
2. **Google errors:** Copy/paste error messages into Google
3. **Ask community:** Post in Indie Hackers, Reddit r/startups, or relevant Discord servers
4. **DM providers:** Ask paralegals what they'd want to see (they'll help refine your pitch)

---

**Good luck! Now go launch.** 🚀

---

**Checklist last updated:** 2026-01-14
