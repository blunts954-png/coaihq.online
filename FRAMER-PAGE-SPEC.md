# Framer Landing Page Specification
## TenantShield – Bakersfield Tenant Help

**Page URL:** https://coaihq.online/bakersfield-tenant-help
**Build Time:** 30-45 minutes
**Tool:** Framer (framer.com)

---

## 1. SEO Setup

### Page Settings → SEO

| Field | Value |
|-------|-------|
| **Page Title** | `Bakersfield Tenant Help – AI Landlord Dispute Analysis \| COAI HQ` |
| **Meta Description** | `Stuck in a landlord fight in Bakersfield? Get AI-powered case analysis, a step-by-step plan, and connection to local tenant advocates in minutes. Not legal advice.` |
| **Canonical URL** | `https://coaihq.online/bakersfield-tenant-help` |
| **OG Title** | `Bakersfield Tenant Help – TenantShield by COAI HQ` |
| **OG Description** | Same as meta description |
| **OG Type** | `website` |
| **OG URL** | `https://coaihq.online/bakersfield-tenant-help` |

---

## 2. Design System

### Colors

```css
Primary Blue:    #2563EB
Secondary Green: #10B981
Dark Gray:       #111827
Light Gray:      #F9FAFB
White:           #FFFFFF
Border Gray:     #E5E7EB
```

### Typography

- **Font Family:** Inter (Framer default) or system font
- **H1:** 48px, bold, dark gray (#111827)
- **H2:** 32px, semi-bold, dark gray
- **H3:** 24px, semi-bold
- **Body:** 18px, regular, dark gray
- **Small:** 14px, regular, gray

---

## 3. Page Structure (Sections in Order)

---

### **SECTION 1: Navigation**

**Layout:** Horizontal flexbox, sticky on scroll (optional)
**Background:** White (#FFFFFF)
**Padding:** 16px top/bottom, 24px left/right

#### Left Side
- **Logo Text:** "COAI HQ"
  - Font: 20px, semi-bold
  - Color: Dark gray (#111827)
  - Link: `/`

#### Right Side (Links)
- "How it Works" → smooth scroll to `#how`
- "FAQ" → smooth scroll to `#faq`
- "Contact" → smooth scroll to footer

**Style:** Links as text, 16px, hover underline

---

### **SECTION 2: Hero**

**Layout:** Centered text, max-width 800px
**Background:** Light gradient or solid light gray (#F9FAFB)
**Padding:** 80px top, 60px bottom

#### Small Label (above H1)
```
TenantShield by COAI HQ
```
- Font: 14px, uppercase, semi-bold
- Color: Primary Blue (#2563EB)
- Margin bottom: 16px

#### H1
```
Stuck in a Landlord Fight in Bakersfield?
Get a Clear Plan in 5 Minutes.
```
- Font: 48px (mobile: 32px), bold
- Color: Dark gray (#111827)
- Margin bottom: 24px

#### Subhead
```
AI-powered analysis plus a connection to Bakersfield tenant advocates.
No lawyer fees, no guessing. Just clarity.
```
- Font: 20px (mobile: 18px), regular
- Color: Dark gray (#111827)
- Line height: 1.6
- Margin bottom: 32px

#### Primary CTA Button
```
Analyze My Case →
```
- Style: Large button, primary blue background (#2563EB)
- Text: White, 18px, semi-bold
- Padding: 16px 32px
- Border radius: 8px
- Hover: Darken blue
- **Action:** Smooth scroll to form section (`#form`)

#### Secondary Link (below button)
```
How this works ↓
```
- Font: 16px, underline
- Color: Primary blue
- **Action:** Smooth scroll to `#how`

---

### **SECTION 3: Form Section** (ID: `form`)

**Layout:** Centered, max-width 600px, bordered card
**Background:** White (#FFFFFF)
**Border:** 1px solid border gray (#E5E7EB)
**Border Radius:** 12px
**Padding:** 40px
**Margin:** 60px auto

#### Form Header
```
Tell Us What's Happening
```
- Font: 24px, semi-bold
- Margin bottom: 24px

#### Form Fields

**Use Framer's native Form component.**

| Field | Type | Label | Placeholder | Required |
|-------|------|-------|-------------|----------|
| `full_name` | Text | Your Full Name | John Doe | ✅ Yes |
| `email` | Email | Email Address | you@example.com | ✅ Yes |
| `phone` | Text | Phone Number (Optional) | (555) 123-4567 | ❌ No |
| `situation` | Textarea | Describe Your Situation | Example: My landlord is withholding my $1,200 security deposit after I moved out on Dec 15. They claim "damage" but never did a walk-through. I emailed them Jan 5 asking for an itemized list, but no response... | ✅ Yes |
| `city` | Text | City | Bakersfield, CA | ✅ Yes |

**Field Styling:**
- Input background: Light gray (#F9FAFB)
- Border: 1px solid border gray (#E5E7EB)
- Border radius: 6px
- Padding: 12px 16px
- Font: 16px
- Focus: Border color changes to primary blue

**Textarea (`situation`):**
- Min height: 120px
- Max height: 300px (scrollable)

#### Consent Checkbox

**Field:** `consent` (Checkbox)

**Label:**
```
☐ I understand this is information only, not legal advice.
```
- Font: 14px
- Required: ✅ Yes
- Color: Dark gray

#### Submit Button

**Text:** "Get My Plan →"

**Style:**
- Background: Secondary green (#10B981)
- Text: White, 18px, semi-bold
- Padding: 16px 32px
- Border radius: 8px
- Full width on mobile
- Hover: Darken green

**Form Behavior (JavaScript/Framer Interactions):**

1. **On Submit (before webhook call):**
   - Disable button (prevent double-submit)
   - Change button text to: "Analyzing your case..."
   - Show inline loading message below button:
     ```
     ⏳ Analyzing your case (30–60 seconds)...
     ```

2. **On Success (after webhook returns 200):**
   - Hide form
   - Show success message (replace form content):
     ```
     ✅ Done. Check your email in the next few minutes
     for your analysis and next steps.
     ```
   - Font: 20px, centered, green text

3. **On Error (webhook fails):**
   - Re-enable button
   - Show error message:
     ```
     ❌ Something went wrong. Please try again or email support@coaihq.online
     ```
   - Font: 16px, red text

**Webhook Integration:**

- **Framer Form Setting:** "Submit to: Webhook/Zapier"
- **Webhook URL:** `[Paste Zapier webhook URL here]`
  - (Generated in Zapier setup, see ZAPIER-SETUP.md)

---

### **SECTION 4: Benefits** (above or below form)

**Layout:** Centered, max-width 800px
**Padding:** 40px 24px

#### Section Header
```
What You Get (Free)
```
- Font: 28px, semi-bold
- Margin bottom: 32px
- Centered

#### Benefits List (5 items)

**Layout:** Vertical list or 2-column grid (mobile: 1 column)

**Each Benefit:**
- Icon: ✅ (green checkmark)
- Text: 18px, dark gray
- Margin between items: 16px

**Copy:**
1. ✅ **Instant situation breakdown in plain English**
2. ✅ **Clear 3–5 step action plan for THIS week**
3. ✅ **Copy-paste emails and letters ready to send today**
4. ✅ **Optional connection to a Bakersfield tenant advocate**
5. ✅ **Built for California tenant law (not generic advice)**

---

### **SECTION 5: How It Works** (ID: `how`)

**Layout:** 3-column grid (mobile: 1 column stacked)
**Background:** Light gray (#F9FAFB)
**Padding:** 80px 24px

#### Section Header
```
How It Works
```
- Font: 36px, semi-bold, centered
- Margin bottom: 48px

#### 3 Steps (Columns)

**Layout for Each Step:**
- Icon/Number at top (large, centered)
- Heading (H3)
- Body text (paragraph)

---

**Step 1**

**Icon/Number:** Large "1" in circle (primary blue background, white text)

**Heading:**
```
Tell Us What Happened
```
- Font: 24px, semi-bold

**Body:**
```
You describe your landlord issue in a few sentences.
Dates, amounts, what they said.
```
- Font: 16px, line-height 1.6

---

**Step 2**

**Icon/Number:** Large "2" in circle (primary blue)

**Heading:**
```
AI Analyzes Your Case
```

**Body:**
```
Our AI looks at your situation through the lens of California tenant law
and scores how strong your position is.
```

---

**Step 3**

**Icon/Number:** Large "3" in circle (primary blue)

**Heading:**
```
Get a Plan + Options
```

**Body:**
```
You get an email with a summary, a step-by-step plan, draft emails,
and options to talk to a local advocate.
```

---

### **SECTION 6: Upsell Teaser**

**Layout:** Centered, max-width 700px
**Background:** White
**Border:** 1px dashed border gray
**Border Radius:** 12px
**Padding:** 40px
**Margin:** 60px auto

#### Headline
```
Want Done-For-You Documents?
```
- Font: 28px, semi-bold
- Margin bottom: 16px

#### Copy
```
For some cases, you can upgrade to get your letters formatted,
ready for certified mail, or get a short paid consult with a tenant-focused paralegal.
```
- Font: 18px, line-height 1.6
- Margin bottom: 24px

#### Two Buttons (Horizontal on desktop, stacked on mobile)

**Button 1:** "See Letter Package Options →"
- Style: Outlined button (border: primary blue, text: primary blue)
- Padding: 12px 24px
- Border radius: 8px
- **Link:** `#` (placeholder) or mention "link will be in your email"
- Hover: Fill with light blue background

**Button 2:** "Talk to a Paralegal →"
- Style: Outlined button (border: secondary green, text: secondary green)
- Same styling as button 1
- **Link:** `#` (placeholder for Calendly/Stripe link)

**Note Below Buttons (small text):**
```
(You'll receive these options in your email after submitting the form above)
```
- Font: 14px, gray, centered

---

### **SECTION 7: FAQ** (ID: `faq`)

**Layout:** Centered, max-width 800px
**Background:** Light gray (#F9FAFB)
**Padding:** 80px 24px

#### Section Header
```
Frequently Asked Questions
```
- Font: 36px, semi-bold, centered
- Margin bottom: 48px

#### FAQ Items (Accordion or Static)

**Recommendation:** Use Framer's Accordion component for collapse/expand.

**Each FAQ Item:**
- Question: 20px, semi-bold, dark gray
- Answer: 16px, regular, dark gray, line-height 1.6
- Margin between items: 24px

---

**Q1:**
```
Q: Is this legal advice?
A: No. This is information to help you understand your situation.
   Always speak to a licensed attorney for legal advice.
```

**Q2:**
```
Q: How fast do I get my analysis?
A: Usually within a few minutes, delivered to your email.
```

**Q3:**
```
Q: Who will you connect me with?
A: Tenant-focused paralegals or advocates in the Bakersfield/Kern County area.
   No obligation.
```

**Q4:**
```
Q: What does it cost?
A: The basic AI analysis is free. Optional document packages or consults
   may have a fee, clearly shown before you pay.
```

---

### **SECTION 8: Footer**

**Layout:** Centered, dark background
**Background:** Dark gray (#111827)
**Text Color:** White (#FFFFFF)
**Padding:** 40px 24px

#### Content (Centered)

**Brand Name:**
```
COAI HQ – Chaotically Organized AI
```
- Font: 18px, semi-bold
- Margin bottom: 8px

**Product Name:**
```
TenantShield – Bakersfield Tenant Help
```
- Font: 16px, regular
- Margin bottom: 16px

**Contact Email:**
```
support@coaihq.online
```
- Font: 16px, underline on hover
- Link: `mailto:support@coaihq.online`
- Margin bottom: 24px

**Disclaimer (Small Print):**
```
Not a law firm. Not legal advice. For information purposes only.
```
- Font: 12px, gray (#9CA3AF)
- Centered

**Optional Links (Small):**
- Privacy Policy (if available)
- Terms of Service (if available)

---

## 4. Responsive Design Notes

### Desktop (1440px+)
- Max content width: 1200px (centered)
- Form: 600px max-width
- 3-column grid for "How It Works"

### Tablet (768px - 1440px)
- 2-column grid for "How It Works"
- Form: Full width with padding

### Mobile (< 768px)
- All sections stack vertically (1 column)
- H1: 32px (down from 48px)
- Button: Full width
- Navigation: Hamburger menu (optional, or horizontal scroll)

---

## 5. Framer-Specific Setup

### Step-by-Step in Framer:

1. **Create New Project**
   - Name: "COAI HQ – TenantShield Bakersfield"
   - Template: Blank canvas

2. **Set Up Custom Domain**
   - Go to Site Settings → Custom Domain
   - Add: `coaihq.online`
   - Create subdirectory: `/bakersfield-tenant-help`
   - (Root `/` can redirect or be a simple hub)

3. **Build Sections**
   - Use Framer's "Stack" layout for vertical sections
   - Add anchor IDs for scroll links:
     - Form section: `#form`
     - How It Works: `#how`
     - FAQ: `#faq`

4. **Add Form Component**
   - Insert → Form
   - Configure fields as per table in Section 3
   - Set form action to "Webhook"
   - Paste Zapier webhook URL (get from ZAPIER-SETUP.md)

5. **Add Interactions**
   - Smooth scroll for CTA buttons
   - Form submit loading state
   - Success/error message display

6. **Test Form**
   - Submit test data
   - Verify webhook receives data in Zapier
   - Check email delivery

7. **Publish**
   - Click "Publish" in top-right
   - Site goes live at `https://coaihq.online/bakersfield-tenant-help`

---

## 6. Copy-Paste Checklist for Dev

**Provide to your developer:**

- ✅ This entire spec document
- ✅ Zapier webhook URL (from ZAPIER-SETUP.md)
- ✅ Brand assets:
  - Logo: "COAI HQ" (text only)
  - Product name: "TenantShield – Bakersfield Tenant Help"
- ✅ Color palette (see Section 2)
- ✅ All copy from sections above
- ✅ Disclaimer: "Not a law firm. Not legal advice."

**Dev Instruction:**
> Build `/bakersfield-tenant-help` first. Focus on speed and robustness.
> Use Framer defaults where possible. Don't over-design.
> Goal: User submits form → receives AI analysis via email within 2-5 minutes.

---

## 7. Launch Checklist

Before publishing:

- [ ] Test form submission (3 test cases)
- [ ] Verify webhook receives all fields correctly
- [ ] Check email delivery (test email arrives within 2-5 min)
- [ ] Mobile responsive test (iPhone, Android)
- [ ] Desktop test (Chrome, Safari, Firefox)
- [ ] SEO meta tags populated
- [ ] Analytics tracking (optional Google Analytics)
- [ ] Legal disclaimer visible on page
- [ ] Contact email working (`support@coaihq.online`)
- [ ] Custom domain pointing correctly

---

**Last Updated:** 2026-01-15
**Version:** 1.0
