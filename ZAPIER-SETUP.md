# Zapier Workflow Setup Guide
## TenantShield – Bakersfield Tenant Help

**Setup Time:** 45-60 minutes
**Difficulty:** Intermediate
**Prerequisites:** Zapier account, OpenAI or Claude API key, Gmail or SendGrid account

---

## Overview: Workflow Architecture

```
[Framer Form Submission]
        ↓
[Zapier Webhook Trigger]
        ↓
[Text Formatter (optional)]
        ↓
[AI Analysis (OpenAI/Claude)]
        ↓
[Email to User (Gmail/SendGrid)]
        ↓
[Log Submission (Optional - Airtable/Sheets)]
```

**Total Zap Steps:** 4-5 steps
**Zapier Task Count:** 1 task per form submission

---

## Step-by-Step Setup

### **STEP 1: Create New Zap**

1. Log in to Zapier: https://zapier.com
2. Click **"Create Zap"** (top-left)
3. Name your Zap: `TenantShield - Bakersfield Form to AI Email`

---

### **STEP 2: Set Up Trigger (Webhooks by Zapier)**

#### 2.1 Choose App & Event
- **App:** Search for **"Webhooks by Zapier"**
- **Event:** Select **"Catch Hook"**
- Click **"Continue"**

#### 2.2 Customize Hook (Optional)
- **Pick off a Child Key:** Leave blank
- Click **"Continue"**

#### 2.3 Copy Webhook URL
- Zapier generates a unique webhook URL:
  ```
  https://hooks.zapier.com/hooks/catch/12345678/abcd1234/
  ```
- **Copy this URL** – you'll paste it into Framer form settings
- **Do NOT click "Test trigger" yet** (we need to send test data first)

---

### **STEP 3: Send Test Data from Framer**

#### 3.1 In Framer:
1. Open your TenantShield landing page project
2. Select the **Form component**
3. In form settings:
   - **Submit to:** Select **"Webhook/Zapier"**
   - **Webhook URL:** Paste the Zapier webhook URL from Step 2.3
4. **Publish** the Framer page (or use preview mode)

#### 3.2 Submit Test Form:
1. Open the published/preview page in your browser
2. Fill out the form with **dummy test data**:
   ```
   Full Name: John Test Doe
   Email: your-actual-email@example.com (use YOUR email to receive test)
   Phone: (555) 123-4567
   Situation: My landlord is withholding my $1,200 security deposit.
              I moved out on Dec 15, 2025. They claim "damage" but never
              did a walk-through. I emailed them Jan 5, no response.
   City: Bakersfield, CA
   Consent: ✅ Checked
   ```
3. Click **"Get My Plan"**

#### 3.3 Back in Zapier:
1. Click **"Test trigger"** in Zapier
2. Zapier should show:
   ```
   ✅ We found a request!
   ```
3. Expand the data to see all fields:
   - `full_name`: John Test Doe
   - `email`: your-actual-email@example.com
   - `phone`: (555) 123-4567
   - `situation`: (your test text)
   - `city`: Bakersfield, CA
   - `consent`: true (or "on")

4. Click **"Continue"** to proceed

---

### **STEP 4: (Optional) Format Text**

This step cleans up the `situation` text (remove extra spaces, line breaks, etc.)

#### 4.1 Add Action
- Click **"+"** to add new step
- **App:** Search for **"Formatter by Zapier"**
- **Event:** Select **"Text"**
- Click **"Continue"**

#### 4.2 Configure Formatter
- **Transform:** Select **"Trim Whitespace"**
- **Input:** Click field → select `1. Situation` (from webhook data)
- Click **"Continue"**
- Click **"Test step"** → should show cleaned text
- Click **"Continue"**

**Note:** This step is optional but recommended for cleaner AI input.

---

### **STEP 5: AI Analysis (OpenAI or Claude)**

This is the core step where AI analyzes the tenant's case.

---

#### **OPTION A: Using OpenAI (ChatGPT)**

##### 5A.1 Add Action
- Click **"+"** to add new step
- **App:** Search for **"OpenAI (ChatGPT, Whisper, DALL-E)"**
- **Event:** Select **"Send Prompt"** or **"Conversation"**
- Click **"Continue"**

##### 5A.2 Connect OpenAI Account
- Click **"Sign in to OpenAI"**
- **API Key:** Enter your OpenAI API key
  - Get key at: https://platform.openai.com/api-keys
- Click **"Yes, Continue"**

##### 5A.3 Configure Prompt

**Model:** `gpt-4-turbo` or `gpt-4o` (recommended for quality)
  - Budget option: `gpt-3.5-turbo` (faster, cheaper, less accurate)

**Temperature:** `0.7` (balanced creativity)

**Max Tokens:** `2000` (enough for detailed analysis)

**System Message:**
```
You are a California tenant rights assistant. Analyze the user's landlord dispute and provide:

1. Situation Summary (1-2 sentences)
2. Relevant California Law (cite specific code sections if applicable: Cal. Civil Code § 1940-1954.1)
3. Legal Position Strength (STRONG / MODERATE / WEAK)
4. Why (plain English explanation, 2-3 sentences)
5. Action Plan (3-5 specific steps for THIS week)
6. Draft Email/Letter (copy-paste ready, addressed "Dear [Landlord Name]")
7. Next Steps & Disclaimer

Format output in plain text with clear headings. Be direct, actionable, and empathetic. Always end with:
"DISCLAIMER: This is educational information, not legal advice. Consult a licensed attorney for legal advice."
```

**User Message (Dynamic):**
```
City: [1. City]
Tenant Name: [1. Full Name]
Issue Description: [2. Output] (or [1. Situation] if you skipped formatter)

Analyze this tenant's situation and provide a detailed response following the format above.
```

**To insert dynamic fields:**
- Click in the text box
- Click **"+"** icon
- Select the field from previous steps (e.g., `1. Full Name`, `2. Output`)

##### 5A.4 Test the AI Step
- Click **"Test step"**
- Zapier sends your test data to OpenAI
- Review the AI response (should be a detailed analysis)
- Click **"Continue"**

---

#### **OPTION B: Using Claude (Anthropic)**

##### 5B.1 Add Action
- Click **"+"** to add new step
- **App:** Search for **"Code by Zapier"** (we'll use Python to call Claude API)
- **Event:** Select **"Run Python"**
- Click **"Continue"**

##### 5B.2 Configure Python Code

**Input Data:** (Map these fields)
- `full_name`: [1. Full Name]
- `email`: [1. Email]
- `phone`: [1. Phone]
- `situation`: [2. Output] (or [1. Situation])
- `city`: [1. City]
- `api_key`: `your-claude-api-key-here` (get at https://console.anthropic.com)

**Code:**
```python
import requests
import json

# Input variables from Zapier
full_name = input_data['full_name']
situation = input_data['situation']
city = input_data['city']
api_key = input_data['api_key']

# Claude API endpoint
url = "https://api.anthropic.com/v1/messages"

# Headers
headers = {
    "x-api-key": api_key,
    "anthropic-version": "2023-06-01",
    "content-type": "application/json"
}

# System prompt
system_prompt = """You are a California tenant rights assistant. Analyze the user's landlord dispute and provide:

1. Situation Summary (1-2 sentences)
2. Relevant California Law (cite specific code sections if applicable: Cal. Civil Code § 1940-1954.1)
3. Legal Position Strength (STRONG / MODERATE / WEAK)
4. Why (plain English explanation, 2-3 sentences)
5. Action Plan (3-5 specific steps for THIS week)
6. Draft Email/Letter (copy-paste ready, addressed "Dear Landlord")
7. Next Steps & Disclaimer

Format output in plain text with clear headings. Be direct, actionable, and empathetic. Always end with:
"DISCLAIMER: This is educational information, not legal advice. Consult a licensed attorney for legal advice."
"""

# User message
user_message = f"""City: {city}
Tenant Name: {full_name}
Issue Description: {situation}

Analyze this tenant's situation and provide a detailed response following the format above."""

# Request payload
payload = {
    "model": "claude-3-5-sonnet-20241022",
    "max_tokens": 4000,
    "temperature": 0.7,
    "system": system_prompt,
    "messages": [
        {"role": "user", "content": user_message}
    ]
}

# Make API request
response = requests.post(url, headers=headers, json=payload)
response_data = response.json()

# Extract AI response
ai_analysis = response_data['content'][0]['text']

# Return output
output = {
    'analysis': ai_analysis,
    'status': 'success'
}
```

##### 5B.3 Test the Code Step
- Click **"Test step"**
- Zapier runs the Python code with your test data
- Review the output: `analysis` field should contain AI response
- Click **"Continue"**

---

### **STEP 6: Send Email to User**

This step sends the AI analysis to the user's email.

---

#### **OPTION A: Using Gmail**

##### 6A.1 Add Action
- Click **"+"** to add new step
- **App:** Search for **"Gmail"**
- **Event:** Select **"Send Email"**
- Click **"Continue"**

##### 6A.2 Connect Gmail Account
- Click **"Sign in to Gmail"**
- Authorize Zapier to send emails on your behalf
- Click **"Continue"**

##### 6A.3 Configure Email

**To:** [1. Email] (from webhook trigger)

**From:** Your Gmail address (auto-populated)

**Subject:**
```
Your Bakersfield Tenant Case – Analysis & Next Steps
```

**Body Type:** `Plain Text` or `HTML` (HTML recommended for formatting)

**Body (Plain Text):**
```
Hi [1. Full Name],

Thanks for submitting your landlord issue. Here's your AI-powered case analysis:

────────────────────────────────────────

[5. Analysis] (OpenAI output) or [5. Output Analysis] (Claude output)

────────────────────────────────────────

NEXT STEPS:

Ready to take action? We offer:

1. ✅ Premium Letter Package ($29) – Get your demand letter formatted, notarized, and ready for certified mail.
   👉 [Insert Stripe Payment Link #1]

2. ✅ 10-Min Paralegal Consultation ($15) – Quick answers from a California-licensed paralegal.
   👉 [Insert Stripe Payment Link #2]

3. ✅ Free 15-Min Advocate Call – Connect with a Bakersfield tenant advocate (no cost).
   👉 [Insert Calendly Link]

────────────────────────────────────────

Questions? Reply to this email or contact support@coaihq.online

Best,
The TenantShield Team
COAI HQ – Chaotically Organized AI

────────────────────────────────────────
LEGAL DISCLAIMER:
This is educational information only, not legal advice. For legal advice, consult a licensed attorney.
```

**Dynamic Fields:**
- `[1. Full Name]` → Insert from webhook
- `[5. Analysis]` → Insert AI output from Step 5

**Stripe Payment Links:** (Add these after completing STRIPE-SETUP.md)
- Premium Letter Package: `https://buy.stripe.com/XXXXXXXXXXXX`
- Paralegal Consultation: `https://buy.stripe.com/YYYYYYYYYYYY`

**Calendly Link:** (Set up later, placeholder for now)
- `https://calendly.com/tenantshield-bakersfield/15min-advocate-call`

##### 6A.4 Test Email Step
- Click **"Test step"**
- Zapier sends a test email to the address you used in the test form
- Check your inbox (should arrive in ~30 seconds)
- Review formatting and content
- Click **"Continue"**

---

#### **OPTION B: Using SendGrid (for higher volume)**

##### 6B.1 Add Action
- **App:** Search for **"SendGrid"**
- **Event:** Select **"Send Email"**
- Click **"Continue"**

##### 6B.2 Connect SendGrid Account
- Sign up at https://sendgrid.com (free tier: 100 emails/day)
- Get API key from SendGrid dashboard
- Paste into Zapier connection
- Click **"Continue"**

##### 6B.3 Configure Email (same as Gmail above)
- **To:** [1. Email]
- **From:** `support@coaihq.online` (must verify this domain in SendGrid)
- **From Name:** `TenantShield Team`
- **Subject:** Same as above
- **Body:** Same as above

---

### **STEP 7: (Optional) Log Submission**

Track all submissions in a spreadsheet or database for analytics.

---

#### **OPTION A: Google Sheets**

##### 7A.1 Add Action
- Click **"+"** to add new step
- **App:** Search for **"Google Sheets"**
- **Event:** Select **"Create Spreadsheet Row"**
- Click **"Continue"**

##### 7A.2 Connect Google Sheets
- Authorize Zapier to access your Google Drive
- Click **"Continue"**

##### 7A.3 Configure Spreadsheet

**Drive:** Your Google Drive

**Spreadsheet:** Create a new spreadsheet named `TenantShield - Submissions`

**Worksheet:** `Sheet1`

**Columns to Create:**
| Column | Value |
|--------|-------|
| Timestamp | [1. Timestamp] (auto-generated by Zapier) |
| Full Name | [1. Full Name] |
| Email | [1. Email] |
| Phone | [1. Phone] |
| City | [1. City] |
| Situation | [2. Output] (or [1. Situation]) |
| AI Strength | (manually extract from AI output, or leave blank) |

##### 7A.4 Test Step
- Click **"Test step"**
- New row should appear in your Google Sheet
- Click **"Continue"**

---

#### **OPTION B: Airtable** (more structured)

##### 7B.1 Add Action
- **App:** Search for **"Airtable"**
- **Event:** Select **"Create Record"**
- Configure similar to Google Sheets above

---

### **STEP 8: Turn On Your Zap**

1. Review all steps (click each step to verify configuration)
2. Click **"Publish"** (top-right)
3. Zap is now **LIVE** 🎉

**Your Zap will now:**
- Listen for Framer form submissions
- Send data to AI for analysis
- Email user with AI response + upsells
- (Optional) Log submission to Sheets/Airtable

---

## Testing Checklist

Before going live, test the full workflow:

- [ ] Submit test form from Framer page
- [ ] Verify Zapier receives webhook data (all fields present)
- [ ] AI analysis generates successfully (no errors)
- [ ] Email arrives within 2-5 minutes
- [ ] Email contains AI analysis + upsell links
- [ ] (Optional) Submission logged to Sheets/Airtable
- [ ] Test with 3 different scenarios (security deposit, eviction, habitability)

**If any step fails:**
1. Check Zapier Task History (left sidebar → "Task History")
2. Click on failed task to see error details
3. Common issues:
   - **Webhook timeout:** Increase AI max tokens or use faster model
   - **Email not sending:** Check Gmail/SendGrid authorization
   - **AI error:** Verify API key and quota limits

---

## Zapier Task Usage & Costs

### Free Tier Limits:
- **Tasks per month:** 100 tasks
- **Zaps:** 5 active Zaps
- **Update time:** 15 minutes

**1 form submission = 1 task** (regardless of how many steps)

**Estimated capacity:**
- 100 tasks/month ≈ 25 form submissions (if each Zap has 4 steps, Zapier counts it as 1 task)

### Paid Plans (if you scale):
- **Starter:** $19.99/mo – 750 tasks (~180 submissions)
- **Professional:** $49/mo – 2,000 tasks (~500 submissions)

---

## Webhook URL (Save This!)

After completing Step 2, save your webhook URL:

```
Webhook URL: https://hooks.zapier.com/hooks/catch/[YOUR_ID]/[YOUR_CODE]/
```

**Paste this URL into:**
- Framer form settings (Submit to: Webhook/Zapier)
- Share with your dev for integration

---

## AI API Costs (Estimate)

### OpenAI (GPT-4 Turbo):
- **Input:** ~500 tokens per request (user situation + system prompt)
- **Output:** ~2,000 tokens (analysis)
- **Cost:** ~$0.03 per request

**100 submissions:** ~$3.00

### Claude (Sonnet 3.5):
- **Input:** ~500 tokens
- **Output:** ~2,000 tokens
- **Cost:** ~$0.02 per request

**100 submissions:** ~$2.00

**Recommendation:** Start with Claude for lower costs, switch to GPT-4 if quality is insufficient.

---

## Troubleshooting

### Issue: Webhook not receiving data
- **Solution:** Check Framer form is set to "Webhook/Zapier" and URL is pasted correctly
- Test by clicking "Test trigger" in Zapier while submitting form

### Issue: AI returns error "Invalid API key"
- **Solution:** Verify API key is correct and has credits
- Check API key permissions (should allow API access)

### Issue: Email not delivered
- **Solution:** Check spam folder, verify email address is correct
- For Gmail: Ensure Zapier is authorized (check Gmail settings → Connected apps)
- For SendGrid: Verify sender email domain

### Issue: AI response is too generic
- **Solution:** Improve system prompt with more specific instructions
- Add examples of desired output format in prompt

---

## Next Steps

After Zapier setup is complete:

1. ✅ Test end-to-end flow (form → AI → email)
2. ✅ Set up Stripe payment links (see STRIPE-SETUP.md)
3. ✅ Update email template with Stripe links
4. ✅ Create Calendly booking link for free advocate calls
5. ✅ Monitor first 10 submissions manually for quality

---

**Last Updated:** 2026-01-15
**Version:** 1.0
