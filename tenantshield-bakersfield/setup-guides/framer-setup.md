# FRAMER SETUP GUIDE
Complete Step-by-Step Instructions for Building TenantShield Landing Page

## OVERVIEW

**Time to complete:** 30-45 minutes
**Difficulty:** Easy (if you know Framer basics)
**Prerequisites:** Framer account (free tier works)

---

## STEP 1: CREATE NEW FRAMER PROJECT

1. Log into Framer (framer.com)
2. Click **"New Project"**
3. Choose **"Start from scratch"** (blank canvas)
4. Project name: `TenantShield Bakersfield`

---

## STEP 2: SET UP PAGE STRUCTURE

### Create Sections:

1. **Navigation Bar** (sticky)
   - Logo: "TenantShield" (text or upload logo image)
   - Nav links: Home | How It Works | FAQ | Contact
   - CTA button (top right): "Analyze My Case"

2. **Hero Section**
   - Full-width container
   - Background: Light gradient (white to light blue)
   - Content:
     - H1 headline
     - H2 subheadline
     - Benefit bullets
     - Form (see Step 3)
     - CTA button

3. **How It Works Section**
   - 4-column grid (desktop) / 1-column (mobile)
   - Icons + text for each step

4. **Benefits Section**
   - 3-column grid (desktop) / 1-column (mobile)
   - Each benefit: icon + headline + body text

5. **FAQ Section**
   - Accordion-style (use Framer's accordion component)
   - 10 questions (see homepage-copy.txt)

6. **Footer**
   - 4-column grid
   - Links, contact info, disclaimer

---

## STEP 3: BUILD THE FORM

This is the most important part. The form captures user data and triggers the entire workflow.

### Form Fields (in order):

1. **First Name** (text input)
   - Field name: `firstName`
   - Required: Yes
   - Placeholder: "Your first name"

2. **Last Name** (text input)
   - Field name: `lastName`
   - Required: Yes
   - Placeholder: "Your last name"

3. **Email** (email input)
   - Field name: `email`
   - Required: Yes
   - Placeholder: "you@example.com"

4. **Phone** (tel input)
   - Field name: `phone`
   - Required: Yes
   - Placeholder: "(661) 555-1234"

5. **Issue Type** (dropdown/select)
   - Field name: `issueType`
   - Required: Yes
   - Options:
     - Security deposit dispute
     - Eviction or eviction notice
     - Uninhabitable conditions
     - Illegal rent increase
     - Landlord harassment or retaliation
     - Privacy violations
     - Other

6. **Situation Description** (textarea)
   - Field name: `situation`
   - Required: Yes
   - Rows: 5
   - Placeholder: "Example: My landlord kept my $1,200 deposit 3 weeks after I moved out..."

7. **Timeline** (dropdown/select)
   - Field name: `timeline`
   - Required: Yes
   - Options:
     - Within the last week
     - 1-4 weeks ago
     - 1-3 months ago
     - 3-6 months ago
     - More than 6 months ago

8. **Previous Legal Help** (radio buttons)
   - Field name: `previousLegalHelp`
   - Required: Yes
   - Options:
     - No
     - Yes, but they didn't help
     - Yes, I'm working with one now

9. **Consent Checkbox** (checkbox)
   - Field name: `consent`
   - Required: Yes
   - Label: "I want AI analysis of my case + an intro to a local tenant advocate. I understand this is educational information, not legal advice."

### Submit Button:
- Text: "GET MY FREE ANALYSIS →"
- Style: Large, prominent, blue background (#2563EB)
- On hover: Slightly darker blue

---

## STEP 4: CONFIGURE FORM SUBMISSION

### Option A: Framer Forms (Easiest)

1. Select the form component
2. In the right panel, click **"Form Settings"**
3. Enable **"Form Submission"**
4. Configure:
   - **Method:** POST
   - **Action:** Leave blank (we'll use Zapier webhook)
   - **Success message:** "Thanks! Check your email in 2 minutes for your case analysis."
   - **Error message:** "Oops! Something went wrong. Please try again."

### Option B: Custom Form Handler

If using custom code:

```javascript
// Add this to a Code component in Framer
export function handleFormSubmit(formData) {
  // Send to Zapier webhook
  fetch('https://hooks.zapier.com/hooks/catch/YOUR_WEBHOOK_ID/', {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json',
    },
    body: JSON.stringify(formData),
  })
  .then(response => response.json())
  .then(data => {
    console.log('Success:', data);
    // Show success message
  })
  .catch((error) => {
    console.error('Error:', error);
    // Show error message
  });
}
```

---

## STEP 5: ADD CONTENT

Copy all content from `landing-page-content/homepage-copy.txt` and paste into your Framer components:

- Hero headline & subheadline
- Benefit bullets
- How It Works steps
- Benefits/features
- FAQ questions & answers
- Footer links

**Pro tip:** Use Framer's CMS feature if you want to easily update content later.

---

## STEP 6: DESIGN & STYLING

### Typography:

- **Headlines:** Inter Bold or Poppins Bold, 48px (H1), 32px (H2)
- **Body text:** Inter Regular, 18px
- **Button text:** Inter SemiBold, 18px

### Colors:

- **Primary (buttons, links):** #2563EB (blue)
- **Secondary (accents):** #10B981 (green)
- **Text:** #111827 (dark gray)
- **Background:** #F9FAFB (light gray)

### Spacing:

- Section padding: 80px top/bottom (desktop), 48px (mobile)
- Element margin: 24px between elements
- Form field gap: 16px between fields

### Responsive Design:

1. Desktop (1440px): 3-4 column grids
2. Tablet (768px): 2 column grids
3. Mobile (375px): 1 column, stacked layout

**Test on all breakpoints!**

---

## STEP 7: ADD ANALYTICS

### Google Analytics 4:

1. In Framer, go to **Settings → General → Analytics**
2. Paste your Google Analytics 4 Measurement ID (looks like `G-XXXXXXXXXX`)
3. Save

### Facebook Pixel (optional):

1. Go to **Settings → General → Custom Code**
2. Paste Facebook Pixel code in `<head>` section
3. Save

---

## STEP 8: SET UP CUSTOM DOMAIN (optional but recommended)

### Option 1: Use Framer subdomain (free)
- `tenantshield-bakersfield.framer.app`

### Option 2: Custom domain ($5/month via Framer or external)
- Buy domain: `tenantshield.com` or `tenantshieldbakersfield.com`
- In Framer: **Settings → Hosting → Custom Domain**
- Follow DNS setup instructions

---

## STEP 9: TEST FORM SUBMISSION

**CRITICAL: Test before launching!**

1. Fill out the form with test data:
   - Name: Test User
   - Email: your-email+test@gmail.com
   - Phone: (555) 555-5555
   - Issue: Security deposit dispute
   - Situation: "This is a test submission"
   - Timeline: Within the last week
   - Previous help: No
   - Consent: Checked

2. Click "Submit"

3. Verify:
   - Success message appears
   - Data is sent to Zapier (check Zapier dashboard)
   - You receive the auto-reply email

4. If something breaks:
   - Check Framer form settings (correct webhook URL?)
   - Check Zapier trigger (is it turned on?)
   - Check browser console for errors (F12 → Console)

---

## STEP 10: OPTIMIZE FOR CONVERSIONS

### A/B Test Ideas:

1. **Hero headline:**
   - Version A: "Stuck in a Landlord Fight? Get a Clear Plan in 5 Minutes."
   - Version B: "Landlord Won't Return Your Deposit? Find Out If You Can Sue."

2. **Form placement:**
   - Version A: Embedded in hero section
   - Version B: Sticky sidebar (always visible)

3. **CTA button copy:**
   - Version A: "Analyze My Case"
   - Version B: "Get My Free Analysis"

Use Framer's variant feature or Google Optimize for A/B testing.

---

## STEP 11: PUBLISH

1. Click **"Publish"** in top-right corner
2. Choose your domain (Framer subdomain or custom)
3. Click **"Publish to Web"**
4. Wait ~30 seconds for deployment
5. Test live site on multiple devices (desktop, mobile, tablet)

---

## STEP 12: POST-LAUNCH CHECKLIST

**Verify these before promoting:**

□ Form submits successfully
□ Success message appears after submit
□ Auto-reply email is sent (check spam folder)
□ All links work (nav, footer, CTA buttons)
□ Mobile layout looks good (no weird wrapping/overflow)
□ Page loads fast (<3 seconds)
□ Analytics tracking fires (check GA4 Real-Time reports)
□ Disclaimer is visible ("NOT LEGAL ADVICE")
□ Contact info is correct

---

## TROUBLESHOOTING

### Form not submitting:
- Check Zapier webhook URL (correct? active?)
- Check browser console for JavaScript errors
- Verify all required fields are marked correctly

### Success message not showing:
- Check Framer form settings (success message configured?)
- Check for JavaScript errors in browser console

### Email not sending:
- Check Zapier workflow (is trigger connected to email step?)
- Check spam folder
- Verify email address is correct in Zapier

### Mobile layout broken:
- Check responsive breakpoints in Framer
- Ensure all text is 16px minimum (prevents zooming on mobile)
- Test on real device, not just browser simulation

---

## RESOURCES

- Framer documentation: https://framer.com/docs
- Framer community: https://framer.com/community
- Framer templates: https://framer.com/templates (for inspiration)

---

## NEXT STEPS

Once Framer site is live:
1. Set up Zapier workflow (see `zapier-workflow.md`)
2. Create Stripe payment links (see `stripe-setup.md`)
3. Set up Calendly (see provider-outreach folder)
4. Launch marketing (see execution-timeline.md)

---

**Estimated total time: 30-45 minutes**

**If you get stuck, the Framer community forum is very helpful!**
