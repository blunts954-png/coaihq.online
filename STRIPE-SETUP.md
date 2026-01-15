# Stripe Payment Links Setup Guide
## TenantShield – Bakersfield Tenant Help

**Setup Time:** 15-20 minutes
**Difficulty:** Easy
**Prerequisites:** Stripe account (free to create)

---

## Overview

Stripe Payment Links allow you to accept payments **without writing any code**. You'll create simple links that users can click to purchase:

1. **Premium Letter Package** – Done-for-you demand letters and documents
2. **Paralegal 15-min Call** – Quick consultation with tenant-focused paralegal

**No backend integration needed.** Just paste the links in your emails and website.

---

## Step-by-Step Setup

### **STEP 1: Create Stripe Account**

1. Go to: https://stripe.com
2. Click **"Start now"** (top-right)
3. Sign up with email and password
4. Complete business profile:
   - **Business name:** `COAI HQ` or `TenantShield`
   - **Business type:** `Individual` or `Company`
   - **Industry:** `Software/SaaS` or `Professional Services`
   - **Website:** `https://coaihq.online`

5. **Activate account:**
   - Provide tax information (for US: SSN or EIN)
   - Add bank account for payouts (ACH transfer, no fees)
   - Verify email and phone

**Note:** You can start in **Test Mode** while building, then switch to **Live Mode** for real payments.

---

### **STEP 2: Create Product #1 – Premium Letter Package**

#### 2.1 Navigate to Products

1. In Stripe Dashboard, go to: **Product catalog** (left sidebar)
2. Click **"Add product"** (top-right)

#### 2.2 Configure Product

**Product Information:**

| Field | Value |
|-------|-------|
| **Name** | Premium Letter Package – TenantShield |
| **Description** | Get your demand letter professionally formatted, ready for certified mail. Includes: security deposit demand template, habitability complaint letter, rent withholding notice, notary affidavit template, small claims checklist. Delivered via email within 24 hours. |
| **Image** | (Optional) Upload a product image (e.g., stack of documents icon) |

**Pricing:**

| Field | Value |
|-------|-------|
| **Pricing model** | Standard pricing |
| **Price** | `$29.00` USD (or your chosen price: $19-$49) |
| **Billing period** | One-time |
| **Tax behavior** | Taxable (enable tax collection for California) |

**Additional Options:**

- **Statement descriptor:** `COAI LETTER PKG` (what appears on customer's credit card)
- **Unit label:** Leave blank

#### 2.3 Save Product

- Click **"Save product"** (top-right)
- Product is now created ✅

---

### **STEP 3: Create Payment Link for Product #1**

#### 3.1 Create Payment Link

1. In Product catalog, find your "Premium Letter Package" product
2. Click on the product name to open details
3. On the right side, click **"Create payment link"**

#### 3.2 Configure Payment Link

**Link settings:**

| Field | Value |
|-------|-------|
| **Collect customer addresses** | ✅ Enabled (for tax calculation) |
| **Collect phone numbers** | ✅ Optional |
| **Allow promotion codes** | ❌ Disabled (or enable if you plan discounts) |
| **Quantity** | Fixed quantity: 1 (user can't buy multiple) |

**After payment:**

| Field | Value |
|-------|-------|
| **After payment** | Show confirmation page |
| **Success message** | Thank you for your purchase! You'll receive your Premium Letter Package via email within 24 hours. Check your inbox (and spam folder) for an email from support@coaihq.online |
| **Button text** | Return to TenantShield |
| **Button link** | `https://coaihq.online/bakersfield-tenant-help` |

**Tax:**

- **Collect taxes:** ✅ Enabled
- **Tax location:** United States → California

#### 3.3 Create & Copy Link

1. Click **"Create link"** (bottom-right)
2. Stripe generates a Payment Link:
   ```
   https://buy.stripe.com/XXXXXXXXXXXX
   ```
3. **Copy this link** and save it:
   ```
   Premium Letter Package Link:
   https://buy.stripe.com/XXXXXXXXXXXX
   ```

---

### **STEP 4: Create Product #2 – Paralegal Consultation**

#### 4.1 Add Second Product

1. Go to **Product catalog**
2. Click **"Add product"**

#### 4.2 Configure Product

**Product Information:**

| Field | Value |
|-------|-------|
| **Name** | 10-Minute Paralegal Consultation – TenantShield |
| **Description** | Quick phone or video consultation with a California-licensed paralegal specializing in tenant rights. Get specific answers about your landlord issue. Scheduling link sent immediately after purchase. |
| **Image** | (Optional) Professional headshot or "consultation" icon |

**Pricing:**

| Field | Value |
|-------|-------|
| **Price** | `$15.00` USD (or your chosen price: $10-$25) |
| **Billing period** | One-time |
| **Tax behavior** | Taxable |

**Statement descriptor:** `COAI PARALEGAL`

#### 4.3 Save Product

- Click **"Save product"**

---

### **STEP 5: Create Payment Link for Product #2**

#### 5.1 Create Payment Link

1. Click on "10-Minute Paralegal Consultation" product
2. Click **"Create payment link"** (right sidebar)

#### 5.2 Configure Payment Link

**Link settings:**
- Collect customer addresses: ✅ Yes
- Collect phone numbers: ✅ **Required** (needed for call scheduling)

**After payment:**
- Success message:
  ```
  Thank you for booking your consultation! You'll receive a scheduling link via email
  within 5 minutes. Check your inbox for an email from support@coaihq.online with
  your Calendly booking link. Choose a time that works for you.
  ```
- Button text: `Return to TenantShield`
- Button link: `https://coaihq.online/bakersfield-tenant-help`

**Tax:** Enabled (California)

#### 5.3 Create & Copy Link

1. Click **"Create link"**
2. Save the generated URL:
   ```
   Paralegal Consultation Link:
   https://buy.stripe.com/YYYYYYYYYYYY
   ```

---

### **STEP 6: (Optional) Create Bundle – Premium Package + Consult**

If you want to offer a discounted bundle:

#### 6.1 Create Bundle Product

**Product Information:**

| Field | Value |
|-------|-------|
| **Name** | Premium Package + Paralegal Consult (Bundle) |
| **Description** | Best value! Get both the Premium Letter Package AND a 10-minute paralegal consultation. Save $5 when you bundle. |

**Pricing:**

| Field | Value |
|-------|-------|
| **Price** | `$39.00` USD (save $5 vs. buying separately) |
| **Billing period** | One-time |

#### 6.2 Create Payment Link (same as above)

**After payment success message:**
```
Thank you! You'll receive TWO emails:
1. Your Premium Letter Package (within 24 hours)
2. Scheduling link for your paralegal consultation (within 5 minutes)

Check your inbox at [customer email]
```

---

### **STEP 7: Configure Tax Settings**

#### 7.1 Enable Tax Collection

1. In Stripe Dashboard, go to: **Settings** → **Tax** (left sidebar)
2. Click **"Enable tax collection"**
3. **Tax registration:**
   - Select **United States** → **California**
   - Enter your business tax ID (if applicable)
   - If you don't have a business yet, you can still collect tax (Stripe handles it)

4. **Tax calculation:**
   - Stripe will auto-calculate California sales tax (currently ~7.25%-10.25% depending on county)

#### 7.2 Save Tax Settings

- Click **"Save"**
- Tax is now automatically applied to all purchases ✅

---

### **STEP 8: Set Up Payouts**

#### 8.1 Add Bank Account

1. Go to: **Settings** → **Bank accounts and scheduling**
2. Click **"Add bank account"**
3. Enter:
   - **Routing number:** (your bank's 9-digit routing number)
   - **Account number:** (your bank account number)
   - **Account holder name:** (must match Stripe business name)

4. **Verify bank account:**
   - Stripe sends 2 small test deposits (2-3 business days)
   - Confirm amounts in Stripe Dashboard

#### 8.2 Payout Schedule

| Field | Value |
|-------|-------|
| **Payout frequency** | Daily (recommended) or Weekly |
| **Minimum payout** | $1 (Stripe default) |
| **Payout method** | Bank transfer (ACH) – **FREE** |

**Stripe fees:**
- **Per transaction:** 2.9% + $0.30
- Example: $29 sale → You receive ~$27.76 after fees

**No monthly fees.** You only pay when you make sales.

---

### **STEP 9: Copy Payment Links to Use**

After creating both products, you should have:

**Payment Link #1 (Premium Letter Package):**
```
https://buy.stripe.com/XXXXXXXXXXXX
```

**Payment Link #2 (Paralegal Consultation):**
```
https://buy.stripe.com/YYYYYYYYYYYY
```

**Payment Link #3 (Optional Bundle):**
```
https://buy.stripe.com/ZZZZZZZZZZZZ
```

---

### **STEP 10: Add Links to Email Template**

Now update your Zapier email template (see ZAPIER-SETUP.md, Step 6) with these links:

**Example Email Body (updated):**

```
Hi [Full Name],

Thanks for submitting your landlord issue. Here's your AI-powered case analysis:

────────────────────────────────────────

[AI Analysis Here]

────────────────────────────────────────

READY TO TAKE ACTION?

We offer three ways to help you move forward:

1. ✅ Premium Letter Package ($29)
   Get your demand letter professionally formatted, ready for certified mail.
   Includes templates, notary affidavits, and small claims checklist.

   👉 Get Premium Package:
   https://buy.stripe.com/XXXXXXXXXXXX

2. ✅ 10-Min Paralegal Consultation ($15)
   Quick phone/video call with a California-licensed paralegal.
   Get specific answers about your case.

   👉 Book Consultation:
   https://buy.stripe.com/YYYYYYYYYYYY

3. ✅ Free 15-Min Advocate Call (No Cost)
   Connect with a Bakersfield tenant advocate for guidance.

   👉 Schedule Free Call:
   https://calendly.com/tenantshield-bakersfield/free-call

────────────────────────────────────────

Questions? Reply to this email or contact support@coaihq.online

Best,
The TenantShield Team

DISCLAIMER: This is educational information, not legal advice.
```

**Update Zapier email with your actual Stripe links.**

---

### **STEP 11: Add Links to Website (Optional)**

You can also add payment links to your Framer landing page:

**In the "Upsell Teaser" section:**

**Button 1:** "See Letter Package Options →"
- Link to: `https://buy.stripe.com/XXXXXXXXXXXX`

**Button 2:** "Talk to a Paralegal →"
- Link to: `https://buy.stripe.com/YYYYYYYYYYYY`

---

## Testing Payments

### Test Mode (Before Going Live)

1. In Stripe Dashboard, ensure **"Test mode"** is enabled (toggle in top-right)
2. Click on a Payment Link
3. Use Stripe test card:
   ```
   Card number: 4242 4242 4242 4242
   Expiration: Any future date (e.g., 12/28)
   CVC: Any 3 digits (e.g., 123)
   ZIP: Any 5 digits (e.g., 90210)
   ```
4. Complete checkout
5. Check Stripe Dashboard → **Payments** to see test transaction
6. Test success page and confirmation message

### Live Mode (Real Payments)

1. Switch to **"Live mode"** (toggle in top-right)
2. Create new Payment Links in Live mode (Test mode links won't work in Live)
3. Use real credit card to test
4. Verify payout appears in Stripe Dashboard → **Balances**

**Important:** Always test in Test Mode first to avoid accidental charges.

---

## Fulfillment Process (After Purchase)

When a customer purchases, you need to deliver the product:

### **Premium Letter Package Fulfillment:**

**Manual Delivery (Week 1):**
1. Check Stripe Dashboard → **Payments** daily
2. For each "Premium Letter Package" purchase:
   - Get customer email from payment details
   - Send email with templates (Word docs or PDFs):
     - Security deposit demand letter template
     - Habitability complaint letter template
     - Rent withholding notice template
     - Notary affidavit template
     - Small claims court checklist
   - Personalize templates with customer's name and situation (from original form submission)

**Automated Delivery (Future - via Zapier):**
- Set up Zap: Stripe Payment → Send Email with Templates
- Use Zapier's "Stripe: New Payment" trigger
- Filter for product name = "Premium Letter Package"
- Send email with pre-formatted templates

### **Paralegal Consultation Fulfillment:**

1. When customer purchases, they receive success message with:
   ```
   You'll receive a scheduling link via email within 5 minutes.
   ```

2. **Manual process (Week 1):**
   - Check Stripe Dashboard for "Paralegal Consultation" purchases
   - Email customer with Calendly link:
     ```
     Subject: Your Paralegal Consultation – Schedule Now

     Hi [Name],

     Thank you for booking your consultation! Please choose a time that works for you:

     👉 https://calendly.com/tenantshield-bakersfield/10min-consultation

     Your paralegal will call you at the scheduled time. They'll have reviewed your case details
     from your original form submission.

     See you soon!
     TenantShield Team
     ```

3. **Automated (Future):**
   - Set up Zap: Stripe Payment (Paralegal Consultation) → Send Email with Calendly link

---

## Stripe Dashboard Overview

**Key pages to monitor:**

| Page | Purpose |
|------|---------|
| **Home** | Overview of recent activity and revenue |
| **Payments** | List of all transactions (successful, failed, refunded) |
| **Customers** | Customer profiles (auto-created on purchase) |
| **Balances** | Your available balance and payout schedule |
| **Products** | Manage products and pricing |
| **Disputes** | Handle chargebacks (rare, but possible) |

**Daily tasks (Week 1):**
1. Check **Payments** page for new orders
2. Fulfill orders (send templates or Calendly link)
3. Monitor **Balances** for payouts

---

## Pricing Recommendations

### Starting Prices:

| Product | Suggested Price | Rationale |
|---------|-----------------|-----------|
| **Premium Letter Package** | $29 | Low enough for impulse buy, high enough for value perception |
| **Paralegal Consultation** | $15 | Quick consultation, low barrier to entry |
| **Bundle (both)** | $39 | Save $5 vs. buying separately (incentivizes bundle) |

### Scaling Strategy:

**Month 1-2 (Validation):**
- Keep prices low ($29/$15) to get initial customers
- Focus on testimonials and reviews

**Month 3+ (Optimization):**
- Test higher prices ($49/$25)
- Add premium tier ($99 for full legal doc package)

---

## Stripe Fees Breakdown

| Sale Price | Stripe Fee | You Receive |
|------------|------------|-------------|
| $15 | $0.74 | $14.26 |
| $29 | $1.14 | $27.86 |
| $39 | $1.43 | $37.57 |
| $49 | $1.72 | $47.28 |

**Tax:** Stripe collects tax on top of price (customer pays), you don't lose revenue to tax.

**Refunds:** If you refund a customer, Stripe fee is NOT returned (you lose $0.30 + 2.9%).

---

## Handling Refunds

If a customer requests a refund:

1. Go to: **Payments** → Find the transaction
2. Click transaction → Click **"Refund"** (top-right)
3. **Refund amount:** Full refund or partial
4. **Reason:** Select reason (helps with analytics)
5. Click **"Refund payment"**

**Customer receives refund in 5-10 business days** (depends on their bank).

**Stripe fee ($0.30) is NOT refunded to you.**

---

## Security & Compliance

**Stripe handles:**
- ✅ PCI DSS compliance (credit card security)
- ✅ Fraud detection and prevention
- ✅ 3D Secure authentication (for high-risk transactions)
- ✅ Dispute management

**You handle:**
- ✅ Customer support (refunds, questions)
- ✅ Product fulfillment (send templates, schedule calls)
- ✅ Tax reporting (Stripe provides 1099-K if you earn >$600/year)

---

## Common Issues & Troubleshooting

### Issue: Customer says payment failed
- **Cause:** Insufficient funds, wrong card details, or fraud protection
- **Solution:** Ask customer to try different card or contact their bank

### Issue: Payment link doesn't load
- **Cause:** Link is in Test Mode but you're in Live Mode (or vice versa)
- **Solution:** Ensure you're using Live Mode links for real customers

### Issue: Customer didn't receive confirmation email
- **Cause:** Email in spam folder or wrong email entered
- **Solution:** Check Stripe Dashboard → **Payments** → Customer email, resend manually

### Issue: Payout delayed
- **Cause:** First payout takes 7-14 days (Stripe verification period)
- **Solution:** Wait for initial payout period to complete, then payouts are daily/weekly

---

## Next Steps After Stripe Setup

1. ✅ Copy Payment Links and save them
2. ✅ Update Zapier email template with links (see ZAPIER-SETUP.md)
3. ✅ Test purchase in Test Mode (use Stripe test card)
4. ✅ Switch to Live Mode and create Live Payment Links
5. ✅ Set up Calendly for free advocate calls (https://calendly.com)
6. ✅ Prepare fulfillment templates (Word docs for Premium Letter Package)
7. ✅ Launch and monitor first 5 purchases

---

## Payment Links Summary (Save This!)

After setup, save your links here:

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
STRIPE PAYMENT LINKS – TENANTSHIELD BAKERSFIELD
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Product 1: Premium Letter Package ($29)
Link: https://buy.stripe.com/XXXXXXXXXXXX

Product 2: Paralegal Consultation ($15)
Link: https://buy.stripe.com/YYYYYYYYYYYY

Product 3: Bundle – Both ($39) [Optional]
Link: https://buy.stripe.com/ZZZZZZZZZZZZ

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

**Use these links in:**
- ✅ Zapier email template (Step 6 of ZAPIER-SETUP.md)
- ✅ Framer website upsell section (optional)

---

**Last Updated:** 2026-01-15
**Version:** 1.0
