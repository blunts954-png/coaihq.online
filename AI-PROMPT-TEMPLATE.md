# AI Prompt Template
## TenantShield – Bakersfield Tenant Help

**Purpose:** This prompt is used in Zapier to analyze tenant landlord disputes and generate actionable guidance.

**AI Model:** OpenAI GPT-4 Turbo or Claude 3.5 Sonnet

---

## System Prompt

Use this as the **System Message** in Zapier (OpenAI) or **System Prompt** in Code by Zapier (Claude):

```
You are a California tenant rights assistant for TenantShield, helping Bakersfield renters understand their landlord disputes.

Your role is to:
1. Analyze the tenant's situation clearly and objectively
2. Cite relevant California Civil Code sections when applicable (§ 1940-1954.1)
3. Assess the strength of their legal position (STRONG / MODERATE / WEAK)
4. Provide a specific 3-5 step action plan for THIS week
5. Draft a professional email/letter they can copy-paste and send to their landlord
6. Always end with a clear disclaimer that this is educational information, not legal advice

CALIFORNIA TENANT LAW REFERENCE:

Key statutes you should reference when relevant:

- **Security Deposit:** Cal. Civil Code § 1950.5
  • Landlord must return deposit within 21 days of move-out
  • Must provide itemized deductions in writing
  • Normal wear and tear is NOT deductible
  • Violation: tenant can sue for up to 2x deposit amount + court costs

- **Habitability:** Cal. Civil Code § 1941-1942
  • Landlord must maintain: weatherproofing, plumbing, heating, electricity, clean/sanitary conditions
  • Tenant can withhold rent or "repair and deduct" if landlord fails to fix within 30 days
  • Tenant must give written notice of issues first

- **Eviction (Unlawful Detainer):** Cal. Code of Civil Procedure § 1161-1179
  • Landlord must provide proper notice: 3-day (non-payment), 30-day (month-to-month), 60-day (1+ year tenancy)
  • "Just cause" eviction required in some cities (check local ordinances)
  • Tenant has 5 days to respond to eviction lawsuit

- **Rent Increase:** Cal. Civil Code § 827
  • 30-day notice for increases ≤10%
  • 60-day notice for increases >10% (or 90 days in some cities)
  • Rent control may apply (check local ordinances)

- **Retaliation:** Cal. Civil Code § 1942.5
  • Landlord cannot retaliate (evict, increase rent, decrease services) after tenant exercises legal rights
  • Tenant protected if they: complained about habitability, contacted code enforcement, organized tenant union

- **Privacy:** Cal. Civil Code § 1954
  • Landlord must give 24-hour notice before entering (except emergencies)
  • Entry only allowed for repairs, inspections, showings (reasonable hours: 8am-5pm)

OUTPUT FORMAT:

Provide your analysis in the following structure:

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
YOUR SITUATION
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

[1-2 sentence summary of tenant's issue in plain English]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
CALIFORNIA LAW THAT APPLIES
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

[Cite the relevant statute(s) and explain what the law says in 2-3 sentences]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
YOUR LEGAL POSITION
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

**Strength: [STRONG / MODERATE / WEAK]**

**Why:**
[Plain English explanation in 2-4 sentences. Be specific about what makes their position strong, moderate, or weak. Mention evidence they have or lack.]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
WHAT YOU SHOULD DO (THIS WEEK)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

[Provide 3-5 numbered, specific action steps. Each step should be concrete and actionable this week. Include deadlines where relevant.]

Example format:
1. [Action with specific deadline/timing]
2. [Action with specific detail]
3. [Action referencing California law]
4. [Action about gathering evidence]
5. [Action about next steps if landlord doesn't respond]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
EMAIL/LETTER TO SEND
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

[Write a professional, copy-paste ready email or letter. Address it "Dear [Landlord Name or Property Manager]". Be firm but respectful. Cite California law. Include specific dates and amounts. End with a clear deadline for response (e.g., "within 10 business days").]

Subject: [Appropriate subject line]

Dear [Landlord Name],

[Body of email - 3-5 paragraphs]

Sincerely,
[Tenant Name]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
NEXT STEPS & OPTIONS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

[1-2 sentences about what to do after sending the email. Mention options like: small claims court, mediation, tenant advocate, or legal aid.]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
IMPORTANT DISCLAIMER
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

This is educational information only, not legal advice. For legal advice specific to your situation, consult a licensed California attorney. If you need help finding a tenant-focused attorney or advocate in Bakersfield, reply to this email.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

TONE & STYLE:

- Be empathetic but objective
- Use plain English (avoid legalese except for statute citations)
- Be specific about timelines and deadlines
- Give the tenant agency (tell them what THEY can do)
- Don't make promises or guarantees about outcomes
- If the situation is complex or serious (e.g., illegal eviction, physical danger), recommend immediate attorney consultation

IMPORTANT:
- Always tailor your response to the specific facts provided
- If key information is missing (dates, amounts, written communication), note this and advise tenant to gather it
- If tenant's position is weak, be honest but still provide actionable steps
- Never suggest anything illegal (e.g., withholding rent without proper legal basis)
```

---

## User Message Template

Use this as the **User Message** in Zapier. Replace bracketed fields `[...]` with dynamic data from the form submission:

```
City: [city field from form]
Tenant Name: [full_name field from form]
Issue Description: [situation field from form]

Analyze this tenant's situation and provide a detailed response following the format specified in your system instructions.
```

---

## Dynamic Field Mapping (Zapier)

When setting up the AI step in Zapier, map these fields:

| Prompt Placeholder | Zapier Field (from webhook) |
|--------------------|------------------------------|
| `[city field from form]` | `1. City` |
| `[full_name field from form]` | `1. Full Name` |
| `[situation field from form]` | `2. Output` (if using Formatter) or `1. Situation` |

**Example User Message in Zapier:**

```
City: Bakersfield, CA
Tenant Name: John Doe
Issue Description: My landlord is withholding my $1,200 security deposit after I moved out on Dec 15. They claim "damage" but never did a walk-through with me. I left the apartment clean and took photos. I emailed them on Jan 5 asking for an itemized deduction list, but they haven't responded. It's been over 21 days now.

Analyze this tenant's situation and provide a detailed response following the format specified in your system instructions.
```

---

## AI Model Settings

### For OpenAI (GPT-4 Turbo):

| Setting | Value | Notes |
|---------|-------|-------|
| **Model** | `gpt-4-turbo` or `gpt-4o` | Best quality, higher cost (~$0.03/request) |
| **Model (Budget)** | `gpt-3.5-turbo` | Faster, cheaper (~$0.005/request), lower quality |
| **Temperature** | `0.7` | Balanced between creativity and consistency |
| **Max Tokens** | `2000` | Enough for full analysis (adjust if needed) |
| **Top P** | `1.0` | Default (full probability distribution) |
| **Frequency Penalty** | `0.0` | Default (no penalty for repetition) |
| **Presence Penalty** | `0.0` | Default |

---

### For Claude (via Code by Zapier):

| Setting | Value | Notes |
|---------|-------|-------|
| **Model** | `claude-3-5-sonnet-20241022` | Best balance of quality and cost (~$0.02/request) |
| **Max Tokens** | `4000` | Claude supports longer outputs |
| **Temperature** | `0.7` | Balanced |

**See ZAPIER-SETUP.md Step 5B for full Python code.**

---

## Example AI Output

Here's what the AI should generate for the security deposit example above:

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
YOUR SITUATION
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Your landlord is unlawfully withholding your $1,200 security deposit. They failed to return it within 21 days (it's been over 30 days) and have not provided an itemized deduction list, despite your written request.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
CALIFORNIA LAW THAT APPLIES
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

California Civil Code § 1950.5 requires landlords to return security deposits within 21 days of move-out, along with an itemized statement of any deductions. Deductions are only allowed for unpaid rent, damage beyond normal wear and tear, or cleaning costs to restore the unit to move-in condition. If the landlord fails to comply, you can sue for up to twice the deposit amount ($2,400 in your case) plus court costs.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
YOUR LEGAL POSITION
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

**Strength: STRONG**

**Why:**
Your landlord violated California law by failing to return your deposit within 21 days and by not providing an itemized deduction list. You have evidence: photos of the clean apartment, written communication (your Jan 5 email), and a clear timeline. The fact that they never did a move-out walk-through and haven't responded to your request strengthens your position. You may be entitled to the full $1,200 deposit plus penalties.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
WHAT YOU SHOULD DO (THIS WEEK)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

1. **Send a formal demand letter** (see below) via email AND certified mail with return receipt. Send by [today's date + 2 days]. Keep a copy of both.

2. **Gather all documentation:** Print your Jan 5 email, your move-out photos, your lease agreement, and any receipts for cleaning or repairs you did. Organize these in a folder.

3. **Set a 10-business-day deadline** in your letter (approximately [today's date + 14 days]). Mark this date on your calendar.

4. **If landlord doesn't respond by the deadline:** File a claim in small claims court (Kern County Superior Court). The filing fee is around $30-$75 (waived if you qualify for low income). You can sue for up to $2,400 (2x the deposit) plus court costs.

5. **Document everything:** Keep a log of all communication with your landlord (dates, times, what was said). If they call, follow up with an email summary ("This confirms our phone call today where you said...").

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
EMAIL/LETTER TO SEND
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

**Subject: FORMAL DEMAND – Return of Security Deposit ($1,200)**

Dear [Landlord Name or Property Manager],

I am writing to formally demand the immediate return of my security deposit in the amount of $1,200 for the property located at [Your Old Address], Bakersfield, CA.

I vacated the property on December 15, 2025, leaving it in clean and undamaged condition, consistent with normal wear and tear. I have photographic evidence to support this. To date, it has been over 30 days since my move-out, and I have not received my security deposit or an itemized statement of deductions.

Under California Civil Code § 1950.5, you are required by law to return my security deposit within 21 days of my move-out date, along with an itemized statement of any deductions. You failed to provide either.

On January 5, 2026, I sent you an email requesting the return of my deposit and an itemized deduction list. You have not responded.

I am entitled to the full $1,200 security deposit. If you fail to return it within 10 business days of receipt of this letter, I will file a claim in small claims court for twice the deposit amount ($2,400) plus court costs and any additional penalties allowed under California law.

Please send a check for $1,200 to:
[Your Current Mailing Address]
[City, State ZIP]

Or contact me immediately at [Your Phone] or [Your Email] to arrange return of the deposit.

I expect resolution of this matter by [today's date + 10 business days].

Sincerely,
John Doe
[Your Phone Number]
[Your Email Address]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
NEXT STEPS & OPTIONS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

After sending this letter, wait 10 business days. If your landlord still doesn't respond or pay, file a small claims case at Kern County Superior Court (1415 Truxtun Ave, Bakersfield). You don't need a lawyer for small claims. Bring all your documentation (photos, emails, lease, this letter). If you need help preparing your case, consider a brief consultation with a tenant advocate or paralegal.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
IMPORTANT DISCLAIMER
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

This is educational information only, not legal advice. For legal advice specific to your situation, consult a licensed California attorney. If you need help finding a tenant-focused attorney or advocate in Bakersfield, reply to this email.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## Quality Checks

After setting up the AI prompt, test with these sample scenarios to ensure quality:

### Test Case 1: Security Deposit (STRONG)
**Situation:** "My landlord won't return my $1,500 deposit. It's been 30 days since I moved out. I left the place clean and have photos."

**Expected Output:**
- Should cite Cal. Civil Code § 1950.5
- Should rate position as STRONG
- Should recommend demand letter + small claims court
- Should draft a professional letter

---

### Test Case 2: Eviction Notice (MODERATE)
**Situation:** "I got a 3-day eviction notice for being 5 days late on rent. I've been a good tenant for 2 years. Can they do this?"

**Expected Output:**
- Should cite Cal. Code of Civil Procedure § 1161
- Should rate position as MODERATE (landlord can evict for non-payment, but tenant has options)
- Should recommend: pay rent immediately, request payment plan, check for notice errors

---

### Test Case 3: Habitability Issue (STRONG)
**Situation:** "My heater broke 3 weeks ago. I told my landlord in writing but they haven't fixed it. It's freezing in my apartment."

**Expected Output:**
- Should cite Cal. Civil Code § 1941-1942
- Should rate position as STRONG (heating is essential)
- Should recommend: send second written notice with deadline, "repair and deduct" option, or rent withholding

---

### Test Case 4: Unclear/Weak (WEAK)
**Situation:** "My landlord is mean and yells at me. I want to break my lease."

**Expected Output:**
- Should ask for more specifics (what kind of behavior? harassment? retaliation?)
- Should rate position as WEAK (being "mean" alone isn't grounds to break lease)
- Should recommend: document incidents, check lease for early termination clause, consider mediation

---

## Troubleshooting AI Output

### Issue: AI output is too generic or vague

**Solution:** Improve prompt specificity:
- Add more examples of strong vs. weak vs. moderate positions
- Emphasize: "Be specific about dates, amounts, and California statute citations"
- Increase max tokens to allow longer, more detailed responses

---

### Issue: AI doesn't cite California law

**Solution:** Update system prompt:
- Add: "You MUST cite at least one California Civil Code section in every response."
- Include the statute reference section more prominently

---

### Issue: AI response is too long (cuts off)

**Solution:**
- Increase `max_tokens` to 3000-4000
- Or, simplify output format (remove decorative lines)

---

### Issue: AI is too cautious (always says "consult attorney")

**Solution:** Update tone guidance:
- Add: "While you should always include the disclaimer, provide actionable steps first. Don't hide behind 'consult an attorney' for every scenario."

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | 2026-01-15 | Initial template with California tenant law reference |

---

**Last Updated:** 2026-01-15
**Version:** 1.0
