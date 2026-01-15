# Email Templates
## TenantShield – Bakersfield Tenant Help

**Purpose:** Ready-to-use email templates for the Zapier workflow and customer communication.

---

## Template 1: User Response Email (Immediate – After Form Submission)

**When to send:** Immediately after form submission via Zapier (Step 6 of ZAPIER-SETUP.md)

**Subject:**
```
Your Bakersfield Tenant Case – Analysis & Next Steps
```

**Body (Plain Text / HTML):**

```
Hi [Full Name],

Thanks for submitting your landlord issue to TenantShield. Here's your AI-powered case analysis for your situation in Bakersfield:

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
YOUR CASE ANALYSIS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

[PASTE AI ANALYSIS OUTPUT HERE]

(This is where the full AI-generated analysis from Claude/OpenAI goes, including:
- Situation summary
- California law that applies
- Legal position strength
- Action plan
- Draft email/letter
- Disclaimer)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
READY TO TAKE ACTION?
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

We offer three ways to help you move forward:


1. ✅ PREMIUM LETTER PACKAGE ($29)

Get your demand letter professionally formatted and ready for certified mail.

Includes:
• Security deposit demand template (customized for YOUR case)
• Habitability complaint letter template
• Rent withholding notice template
• Notary affidavit template
• Small claims court filing checklist
• Delivered via email within 24 hours

👉 Get Premium Package:
https://buy.stripe.com/XXXXXXXXXXXX
(Replace with your Stripe link)


2. ✅ 10-MINUTE PARALEGAL CONSULTATION ($15)

Quick phone or video call with a California-licensed paralegal who specializes in tenant rights.

What you get:
• Review of your specific case details
• Answers to your most urgent questions
• Guidance on next steps
• Scheduling link sent immediately after purchase

👉 Book Consultation:
https://buy.stripe.com/YYYYYYYYYYYY
(Replace with your Stripe link)


3. ✅ FREE 15-MINUTE ADVOCATE CALL (NO COST)

Connect with a Bakersfield tenant advocate for free guidance. No obligation.

👉 Schedule Free Call:
https://calendly.com/tenantshield-bakersfield/free-call
(Replace with your Calendly link)


━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
QUESTIONS?
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Reply to this email anytime. We're here to help.

Best,
The TenantShield Team
COAI HQ – Chaotically Organized AI

support@coaihq.online


━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
LEGAL DISCLAIMER
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

This is educational information only, not legal advice. For legal advice specific to your situation, consult a licensed California attorney. TenantShield is not a law firm.
```

---

### Dynamic Fields for Zapier:

When setting up this email in Zapier (Step 6 of ZAPIER-SETUP.md), replace these placeholders:

| Placeholder | Zapier Field | Source |
|-------------|--------------|--------|
| `[Full Name]` | `1. Full Name` | Webhook trigger (Step 1) |
| `[PASTE AI ANALYSIS OUTPUT HERE]` | `5. Analysis` (OpenAI) or `5. Output Analysis` (Claude) | AI step (Step 5) |

**Stripe Links:** Replace `XXXXXXXXXXXX` and `YYYYYYYYYYYY` with your actual Stripe payment links from STRIPE-SETUP.md.

**Calendly Link:** Replace with your actual Calendly booking link (create at https://calendly.com).

---

## Template 2: Lead Notification Email (To You – Internal)

**When to send:** Immediately after form submission (optional internal notification)

**Purpose:** Get notified when someone submits the form so you can follow up.

**To:** `your-email@example.com` (your personal email or team email)

**Subject:**
```
🔔 New TenantShield Lead: [Full Name] – [City]
```

**Body:**

```
New tenant case submission from Bakersfield:

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
LEAD DETAILS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Name: [Full Name]
Email: [Email]
Phone: [Phone]
City: [City]

Submitted: [Timestamp]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
SITUATION DESCRIPTION
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

[Situation]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
AI ANALYSIS SUMMARY
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

[AI Analysis - Full Output]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
FOLLOW-UP
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

- [ ] Review AI analysis for quality (first 10 submissions)
- [ ] Follow up in 2-3 days if they don't purchase
- [ ] Add to email sequence (if using Mailchimp/ConvertKit)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

View in Dashboard: [Link to Google Sheets/Airtable if using]
```

**Dynamic Fields:**

| Placeholder | Zapier Field |
|-------------|--------------|
| `[Full Name]` | `1. Full Name` |
| `[Email]` | `1. Email` |
| `[Phone]` | `1. Phone` |
| `[City]` | `1. City` |
| `[Situation]` | `1. Situation` (or `2. Output` if formatted) |
| `[Timestamp]` | `1. Timestamp` (auto-generated by Zapier) |
| `[AI Analysis - Full Output]` | `5. Analysis` or `5. Output Analysis` |

---

## Template 3: Premium Letter Package Delivery Email

**When to send:** After customer purchases Premium Letter Package via Stripe

**Subject:**
```
Your Premium Letter Package – TenantShield [Order #12345]
```

**Body:**

```
Hi [Customer Name],

Thank you for purchasing the Premium Letter Package from TenantShield!

Your customized tenant rights documents are attached to this email:

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
YOUR DOCUMENTS (5 TEMPLATES)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

1. ✅ Security Deposit Demand Letter (Word Doc)
   → Customized with your name, address, and situation details
   → Ready to send via certified mail

2. ✅ Habitability Complaint Letter (Word Doc)
   → Template for notifying landlord of repair issues
   → Includes California Civil Code citations

3. ✅ Rent Withholding Notice (Word Doc)
   → Use if landlord fails to make repairs after notice
   → Legally compliant with Cal. Civil Code § 1942

4. ✅ Notary Affidavit Template (PDF)
   → Sworn statement template for court
   → Instructions for getting it notarized included

5. ✅ Small Claims Court Filing Checklist (PDF)
   → Step-by-step guide for filing in Kern County Superior Court
   → Court address, fees, and filing instructions


━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
HOW TO USE THESE DOCUMENTS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

1. **Review each template** and fill in any remaining blanks (highlighted in yellow).

2. **Send via certified mail** with return receipt requested (costs ~$8 at USPS).
   - Keep a copy for your records.
   - The return receipt proves your landlord received the letter.

3. **Set a deadline** for landlord response (typically 10-14 business days).

4. **If landlord doesn't respond:** Follow the Small Claims Court Checklist to file your case.


━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
NEED MORE HELP?
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

If you have questions about using these templates or want personalized guidance:

👉 Book a 10-Min Paralegal Consultation ($15):
https://buy.stripe.com/YYYYYYYYYYYY

Or reply to this email and we'll connect you with a Bakersfield tenant advocate (free).


━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Questions? Reply to this email or contact support@coaihq.online

Best,
The TenantShield Team
COAI HQ

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
LEGAL DISCLAIMER: This package contains educational templates, not legal advice.
For legal advice, consult a licensed attorney.
```

**Attachments:**
- 5 Word/PDF documents with templates (create these in advance)

**Automation:**
- **Manual (Week 1):** Send this email manually after checking Stripe Dashboard for new "Premium Letter Package" purchases.
- **Automated (Future):** Set up Zapier integration:
  - Trigger: Stripe → New Payment
  - Filter: Product Name = "Premium Letter Package"
  - Action: Gmail/SendGrid → Send Email with Attachments

---

## Template 4: Paralegal Consultation Booking Email

**When to send:** After customer purchases Paralegal Consultation via Stripe

**Subject:**
```
Your Paralegal Consultation – Schedule Now [Order #12345]
```

**Body:**

```
Hi [Customer Name],

Thank you for booking a 10-minute paralegal consultation with TenantShield!

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
SCHEDULE YOUR CALL
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Please choose a time that works for you:

👉 Schedule Here:
https://calendly.com/tenantshield-bakersfield/10min-paralegal
(Replace with your Calendly link)

Available times:
Monday-Friday, 9am-5pm PST


━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
WHAT TO PREPARE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

To make the most of your 10 minutes:

1. Have your lease agreement handy (if possible)
2. Write down your top 2-3 questions
3. Have key dates and amounts ready (deposit amount, rent, when issues started)

Your paralegal will have reviewed your original case submission, so they'll already be familiar with your situation.


━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
HOW IT WORKS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

- You'll receive a phone call at your scheduled time
- Your paralegal specializes in California tenant law
- Ask specific questions about your landlord dispute
- Get actionable advice (not legal representation)


━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Questions? Reply to this email or contact support@coaihq.online

Looking forward to helping you!

Best,
The TenantShield Team
COAI HQ

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
LEGAL DISCLAIMER: This consultation provides educational information, not legal advice or attorney representation.
```

**Automation:**
- **Manual (Week 1):** Check Stripe Dashboard daily for "Paralegal Consultation" purchases, send this email manually.
- **Automated (Future):** Zapier integration (same as Template 3, but filter for "Paralegal Consultation" product).

---

## Template 5: Follow-Up Email (2 Days After Initial Submission – No Purchase)

**When to send:** 2 days after user submits form but hasn't purchased anything (optional nurture sequence)

**Subject:**
```
Quick check-in about your landlord issue
```

**Body:**

```
Hi [Full Name],

I wanted to follow up on the case analysis we sent you a couple days ago about your landlord situation in Bakersfield.

Did the action plan we provided help you take next steps?

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

I know dealing with a difficult landlord can be stressful. If you're ready to move forward, here are your options again:

1. ✅ Premium Letter Package ($29) – Done-for-you demand letters
   https://buy.stripe.com/XXXXXXXXXXXX

2. ✅ 10-Min Paralegal Call ($15) – Quick answers from an expert
   https://buy.stripe.com/YYYYYYYYYYYY

3. ✅ Free 15-Min Advocate Call – Connect with local help (no cost)
   https://calendly.com/tenantshield-bakersfield/free-call


━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Or if you have questions, just hit reply. I'm here to help.

Best,
[Your Name]
TenantShield Team

P.S. Don't wait too long – California has strict deadlines for security deposit claims (21 days) and eviction responses (5 days). The sooner you act, the better your outcome.
```

**Automation:**
- **Manual (Week 1):** Manually send to non-purchasers after 2 days.
- **Automated (Future):**
  - Tool: Mailchimp, ConvertKit, or Zapier Delay
  - Trigger: Form submission
  - Delay: 2 days
  - Condition: If no Stripe purchase, send this email

---

## Template 6: Follow-Up Email (7 Days After Initial Submission – Last Touch)

**When to send:** 7 days after form submission if user still hasn't purchased (final follow-up)

**Subject:**
```
Last check-in – Don't let your landlord win
```

**Body:**

```
Hi [Full Name],

This is my last check-in about your landlord issue.

I know it's easy to put this off, but here's the reality:

• If it's been more than 21 days since your landlord was supposed to return your deposit, you're losing time to file a small claims case.

• If you received an eviction notice, you only have 5 days to respond or you could lose your home by default.

• The longer you wait, the weaker your position gets.


━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

You have three options to take action TODAY:

1. ✅ Get your demand letter formatted and ready to send ($29)
   https://buy.stripe.com/XXXXXXXXXXXX

2. ✅ Talk to a paralegal who can answer your specific questions ($15)
   https://buy.stripe.com/YYYYYYYYYYYY

3. ✅ Schedule a free call with a Bakersfield tenant advocate (no cost)
   https://calendly.com/tenantshield-bakersfield/free-call


━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

I've helped dozens of Bakersfield tenants stand up to bad landlords.

Don't let yours get away with it.

Best,
[Your Name]
TenantShield Team

P.S. If you're not moving forward, reply and let me know why. I'd love to hear your feedback so we can improve.
```

**Automation:**
- **Manual (Week 1):** Send manually after 7 days to non-purchasers.
- **Automated (Future):** Email automation tool with 7-day delay.

---

## Template 7: Support/Help Email (User Replies with Questions)

**When to send:** When a user replies to any email with questions

**Subject:** `Re: [Their Original Subject]`

**Body:**

```
Hi [Name],

Thanks for reaching out!

[Answer their specific question here – be helpful, empathetic, and direct]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

If you'd like more personalized guidance, here are your options:

1. Book a 10-minute paralegal consultation ($15):
   https://buy.stripe.com/YYYYYYYYYYYY

2. Schedule a free call with a local tenant advocate:
   https://calendly.com/tenantshield-bakersfield/free-call


━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Let me know if you have any other questions!

Best,
[Your Name]
TenantShield Team
support@coaihq.online
```

---

## Email Sequence Summary (Optional Automated Nurture)

If you want to set up a full email sequence:

| Email # | Timing | Subject | Purpose |
|---------|--------|---------|---------|
| **Email 1** | Immediate | Your Bakersfield Tenant Case – Analysis & Next Steps | Deliver AI analysis + upsell |
| **Email 2** | 2 days later | Quick check-in about your landlord issue | Soft follow-up |
| **Email 3** | 7 days later | Last check-in – Don't let your landlord win | Urgency + final CTA |
| **Email 4** | After purchase (Premium) | Your Premium Letter Package – Order #12345 | Deliver templates |
| **Email 5** | After purchase (Paralegal) | Your Paralegal Consultation – Schedule Now | Send Calendly link |

---

## Calendly Setup (for Free Advocate Call)

1. Create account at https://calendly.com (free tier)
2. Create event type:
   - **Event Name:** "15-Min Tenant Advocate Call"
   - **Duration:** 15 minutes
   - **Availability:** Set your availability (or your paralegal partner's)
3. Copy Calendly link:
   ```
   https://calendly.com/tenantshield-bakersfield/free-call
   ```
4. Paste this link in all email templates where it says `[Insert Calendly link]`

---

## Quick Reference: All Links to Include in Emails

**Stripe Payment Links (from STRIPE-SETUP.md):**
- Premium Letter Package: `https://buy.stripe.com/XXXXXXXXXXXX`
- Paralegal Consultation: `https://buy.stripe.com/YYYYYYYYYYYY`

**Calendly Link:**
- Free Advocate Call: `https://calendly.com/tenantshield-bakersfield/free-call`

**Website Link:**
- Landing page: `https://coaihq.online/bakersfield-tenant-help`

**Support Email:**
- `support@coaihq.online`

---

**Last Updated:** 2026-01-15
**Version:** 1.0
