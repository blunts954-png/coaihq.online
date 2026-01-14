# ZAPIER WORKFLOW GUIDE
Complete Step-by-Step Setup for TenantShield Automation

## OVERVIEW

**Time to complete:** 45-60 minutes
**Difficulty:** Medium
**Prerequisites:**
- Zapier account (free tier allows 100 tasks/month)
- Framer form live (from framer-setup.md)
- Claude API key OR OpenAI API key
- Gmail or SendGrid account for emails

**What this workflow does:**
1. Receives form submission from Framer
2. Sends data to Claude API for analysis
3. Emails user with AI analysis + next steps
4. Sends lead info to you (for provider handoff)

---

## STEP 1: CREATE ZAPIER WEBHOOK

1. Log into Zapier (zapier.com)
2. Click **"Create Zap"**
3. Name it: `TenantShield - Form to AI Analysis`

### Trigger Setup:

1. **Choose app:** Webhooks by Zapier
2. **Choose trigger:** Catch Hook
3. Click **"Continue"**
4. Zapier will show you a webhook URL (looks like: `https://hooks.zapier.com/hooks/catch/123456/abcdef/`)
5. **COPY THIS URL** — you'll paste it into Framer form settings
6. Click **"Test trigger"**
7. **NOW:** Go to your Framer site, fill out the form with test data, submit
8. **BACK TO ZAPIER:** Click "Test trigger" again — it should find your test submission
9. Click **"Continue"**

---

## STEP 2: ADD AI ANALYSIS STEP

Now we send the user's form data to Claude (or OpenAI) for analysis.

### Option A: Claude API (Recommended)

1. **Add step:** Click the **"+"** button
2. **Choose app:** Code by Zapier
3. **Choose action:** Run Python
4. Click **"Continue"**

**Configure the code:**

```python
import requests
import json

# Claude API settings
CLAUDE_API_KEY = "YOUR_CLAUDE_API_KEY_HERE"  # Get from console.anthropic.com
CLAUDE_MODEL = "claude-3-5-sonnet-20241022"

# Get form data from Zapier
first_name = input_data.get('firstName', '')
last_name = input_data.get('lastName', '')
email = input_data.get('email', '')
phone = input_data.get('phone', '')
issue_type = input_data.get('issueType', '')
situation = input_data.get('situation', '')
timeline = input_data.get('timeline', '')
previous_legal = input_data.get('previousLegalHelp', '')

# Load the AI prompt (tenant-case-analyzer.txt)
# For simplicity, we'll inline it here. In production, store in a file or database.
system_prompt = """
You are TenantShield, an AI legal analyst specializing in California tenant rights.

[PASTE FULL CONTENT FROM ai-prompts/tenant-case-analyzer.txt HERE]
"""

# User's situation
user_prompt = f"""
User: {first_name} {last_name}
Issue Type: {issue_type}
Timeline: {timeline}
Previous Legal Help: {previous_legal}

Situation:
{situation}

Please analyze this case according to California tenant law and provide a detailed assessment.
"""

# Call Claude API
response = requests.post(
    "https://api.anthropic.com/v1/messages",
    headers={
        "x-api-key": CLAUDE_API_KEY,
        "anthropic-version": "2023-06-01",
        "content-type": "application/json"
    },
    json={
        "model": CLAUDE_MODEL,
        "max_tokens": 4000,
        "system": system_prompt,
        "messages": [
            {"role": "user", "content": user_prompt}
        ]
    }
)

# Parse response
result = response.json()
ai_analysis = result['content'][0]['text']

# Return analysis (Zapier will make this available to next steps)
output = {
    'analysis': ai_analysis,
    'first_name': first_name,
    'email': email
}
```

5. **Input Data:** Map form fields from Step 1
   - `firstName` → Form field "firstName"
   - `lastName` → Form field "lastName"
   - `email` → Form field "email"
   - `phone` → Form field "phone"
   - `issueType` → Form field "issueType"
   - `situation` → Form field "situation"
   - `timeline` → Form field "timeline"
   - `previousLegalHelp` → Form field "previousLegalHelp"

6. Click **"Test action"**
7. Verify output contains `analysis` field with AI response

### Option B: OpenAI API (Alternative)

If you prefer OpenAI (ChatGPT):

1. **Add step:** Choose "OpenAI (GPT-4)" app
2. **Choose action:** Send Prompt
3. **Configure:**
   - **API Key:** Your OpenAI API key
   - **Model:** GPT-4
   - **System Prompt:** [Paste content from `ai-prompts/tenant-case-analyzer.txt`]
   - **User Prompt:**
     ```
     User: {{firstName}} {{lastName}}
     Issue: {{issueType}}
     Situation: {{situation}}
     Timeline: {{timeline}}

     Analyze this California tenant case.
     ```
4. Click **"Test action"**

---

## STEP 3: SEND EMAIL TO USER

Now we email the user with their AI analysis.

1. **Add step:** Click **"+"**
2. **Choose app:** Gmail (or SendGrid, Mailgun, etc.)
3. **Choose action:** Send Email
4. Click **"Continue"**

**Configure email:**

- **To:** `{{email}}` (from Step 1)
- **From:** your-email@gmail.com (or custom domain)
- **Reply To:** hello@tenantshield.com
- **Subject:** `Your Case Analysis is Ready - TenantShield`
- **Body Type:** HTML
- **Body:**

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    body { font-family: Arial, sans-serif; line-height: 1.6; color: #333; }
    .container { max-width: 600px; margin: 0 auto; padding: 20px; }
    .header { background-color: #2563EB; color: white; padding: 20px; text-align: center; }
    .content { background-color: #f9f9f9; padding: 20px; margin: 20px 0; }
    .cta-button { display: inline-block; background-color: #10B981; color: white; padding: 15px 30px; text-decoration: none; border-radius: 5px; margin: 10px 0; }
    .disclaimer { font-size: 12px; color: #666; border-top: 1px solid #ddd; padding-top: 20px; margin-top: 20px; }
  </style>
</head>
<body>
  <div class="container">
    <div class="header">
      <h1>TenantShield</h1>
    </div>

    <p>Hi {{firstName}},</p>

    <p>Thank you for submitting your landlord-tenant issue to TenantShield. I've analyzed your situation and have your results ready.</p>

    <div class="content">
      <h2>Your Case Analysis:</h2>
      {{analysis}}
    </div>

    <h3>Next Steps - Choose Your Path:</h3>

    <p><strong>OPTION 1 (FREE - RECOMMENDED):</strong><br>
    Connect with a local Bakersfield tenant advocate for a free 15-minute consultation.</p>

    <p style="text-align: center;">
      <a href="https://calendly.com/your-link" class="cta-button">📅 Schedule Your Free Consult</a>
    </p>

    <p><strong>OPTION 2 ($29 - PREMIUM):</strong><br>
    Get the Premium Letter Package with professionally formatted documents.</p>

    <p style="text-align: center;">
      <a href="https://buy.stripe.com/your-link" class="cta-button">💳 Get Premium Letters</a>
    </p>

    <p><strong>OPTION 3 ($15):</strong><br>
    10-minute paid consultation with a California-licensed paralegal.</p>

    <p style="text-align: center;">
      <a href="https://buy.stripe.com/your-other-link" class="cta-button">💳 Book Paid Consult</a>
    </p>

    <p>Questions? Just reply to this email.</p>

    <p>Good luck with your case!<br>
    The TenantShield Team</p>

    <div class="disclaimer">
      <p><strong>IMPORTANT DISCLAIMER:</strong><br>
      TenantShield provides educational information about California tenant rights. This is NOT legal advice and does not create an attorney-client relationship. For legal advice specific to your situation, consult a licensed California attorney.</p>
    </div>
  </div>
</body>
</html>
```

5. Replace placeholders:
   - `{{firstName}}` → from Step 1
   - `{{analysis}}` → from Step 2 (AI output)
   - `https://calendly.com/your-link` → Your Calendly link
   - `https://buy.stripe.com/your-link` → Your Stripe payment link (see stripe-setup.md)

6. Click **"Test action"**
7. Check your email inbox — you should receive the test email

---

## STEP 4: SEND LEAD NOTIFICATION TO YOU

This emails you whenever a new lead comes in, so you can forward it to providers.

1. **Add step:** Click **"+"**
2. **Choose app:** Gmail
3. **Choose action:** Send Email

**Configure:**

- **To:** your-email@gmail.com
- **Subject:** `🚨 New TenantShield Lead: {{firstName}} {{lastName}} - {{issueType}}`
- **Body:**

```
NEW LEAD ALERT
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Name: {{firstName}} {{lastName}}
Email: {{email}}
Phone: {{phone}}
Issue Type: {{issueType}}
Timeline: {{timeline}}
Previous Legal Help: {{previousLegalHelp}}

Situation:
{{situation}}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
AI ANALYSIS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

{{analysis}}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
NEXT STEPS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

1. Forward this to a provider (see provider-handoff template)
2. Track in Airtable/Notion
3. Follow up if provider doesn't contact within 24 hours

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

4. Click **"Test action"**

---

## STEP 5: TURN ON ZAP

1. Click **"Publish"** in top-right corner
2. Name your Zap: `TenantShield - Form to AI Analysis`
3. Click **"Turn on Zap"**

**Your Zap is now live!** 🎉

---

## STEP 6: TEST END-TO-END

1. Go to your Framer site
2. Fill out the form with REAL test data (use your own email)
3. Submit
4. Wait 30-60 seconds
5. Check your email inbox:
   - You should receive the user email (with AI analysis)
   - You should receive the lead notification email

**If emails don't arrive:**
- Check spam folder
- Check Zapier "Task History" for errors
- Verify Gmail connection is authorized

---

## STEP 7: SET UP FOLLOW-UP EMAILS (Optional)

You can add more Zaps for follow-up emails 2 days and 7 days later.

### Zap 2: Follow-Up Email (2 Days)

1. **Trigger:** Delay After Queue (Zapier built-in)
   - Wait: 2 days after form submission

2. **Action:** Send Email (Gmail)
   - Subject: "Quick check-in about your landlord issue"
   - Body: [Use template from `email-templates/user-response-email.txt` - Email 2]

### Zap 3: Final Follow-Up (7 Days)

Same as above, but 7-day delay + different email copy (Email 3 template).

**Note:** Free Zapier tier doesn't support multi-step delays well. Consider upgrading to Zapier Starter ($19.99/month) or use a different tool (e.g., Mailchimp, ConvertKit).

---

## STEP 8: ADD UPSELL TRIGGERS (Optional)

If you want to trigger different upsells based on case strength (STRONG vs. WEAK), add a **Filter** step:

1. **Add step:** Filter by Zapier
2. **Condition:** "Analysis contains 'STRONG'"
   - If TRUE: Send premium upsell email
   - If FALSE: Send free consult email only

This requires parsing the AI analysis output to detect case strength. Advanced setup.

---

## TROUBLESHOOTING

### Form submissions not triggering Zap:
- Check webhook URL in Framer (correct? typo?)
- Check Zapier "Task History" → any errors?
- Verify Zap is turned ON (not paused)

### AI analysis returning errors:
- Check API key (Claude or OpenAI) is valid
- Check API rate limits (free tier has limits)
- Check Python code for syntax errors

### Emails not sending:
- Check Gmail connection (is it authorized?)
- Check spam folder
- Verify email addresses are correct
- Check Zapier task history for delivery status

### Emails going to spam:
- Use a custom domain email (not Gmail)
- Set up SPF/DKIM records for your domain
- Avoid spammy words in subject line
- Include unsubscribe link

---

## ZAPIER TASK LIMITS

**Free tier:** 100 tasks/month
- 1 form submission = ~3-4 tasks (trigger + AI + 2 emails)
- **Max ~25-30 leads/month on free tier**

**Starter tier ($19.99/month):** 750 tasks/month
- **Max ~180-200 leads/month**

**Professional tier ($49/month):** 2,000 tasks/month
- **Max ~500-600 leads/month**

Plan accordingly based on your expected volume.

---

## ALTERNATIVE: NO-CODE TOOLS

If Zapier is too complex:

- **Make (formerly Integromat):** Similar to Zapier, sometimes cheaper
- **n8n:** Open-source, self-hosted (free but requires technical setup)
- **Pipedream:** Developer-friendly, generous free tier

All work similarly to Zapier.

---

## NEXT STEPS

Once Zapier workflow is live:
1. Set up Stripe payment links (see `stripe-setup.md`)
2. Set up Calendly (see provider-outreach folder)
3. Test end-to-end flow multiple times
4. Launch marketing (see execution-timeline.md)

---

**Estimated total time: 45-60 minutes**

**If you get stuck, Zapier has excellent documentation: https://zapier.com/help**
