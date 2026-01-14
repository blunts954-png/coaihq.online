# STRIPE SETUP GUIDE
Payment Links for TenantShield Upsells

## OVERVIEW

**Time to complete:** 15-20 minutes
**Difficulty:** Easy
**Prerequisites:**
- Stripe account (free to create)
- Bank account for payouts

**What you'll create:**
- Payment link for Premium Letter Package ($29)
- Payment link for Paid Paralegal Consult ($15)
- Optional: Bundle pricing

---

## STEP 1: CREATE STRIPE ACCOUNT

1. Go to stripe.com
2. Click **"Start now"** or **"Sign up"**
3. Enter your email, create password
4. Verify email address
5. Complete business profile:
   - Business name: TenantShield (or your legal business name)
   - Type: Individual or Company
   - Industry: Professional Services → Legal Services
   - Website: tenantshield.com (or Framer site URL)
   - Location: United States
   - Tax ID: Your SSN or EIN

**Important:** You won't be able to receive payouts until you complete identity verification (upload driver's license + bank info). Do this ASAP.

---

## STEP 2: CREATE PRODUCT 1 - PREMIUM LETTER PACKAGE

1. In Stripe Dashboard, click **"Products"** in left sidebar
2. Click **"+ Add product"**

**Product Details:**

- **Name:** Premium Letter Package
- **Description:**
  ```
  Professionally formatted demand letters, certified mail templates, notary-ready affidavits, small claims filing checklist, and evidence organization guide. Everything you need to take legal action with confidence.
  ```
- **Pricing:**
  - **Price:** $29.00 USD
  - **Billing:** One-time
  - **Tax:** Enable automatic tax collection (if applicable)
- **Image:** Upload an image (optional, but recommended — use a simple document icon or legal forms graphic)

3. Click **"Save product"**

---

## STEP 3: CREATE PAYMENT LINK FOR PREMIUM LETTERS

1. In the Premium Letter Package product page, click **"Create payment link"**
2. Configure:

**Payment Settings:**
- **Collect customer information:**
  - ✅ Name
  - ✅ Email address
  - ⬜ Phone number (optional)
  - ⬜ Billing address (not needed)
  - ⬜ Shipping address (digital product, no shipping)

**After payment:**
- **Success page:** Custom message
  - **Message:**
    ```
    Thank you for your purchase! 🎉

    Your Premium Letter Package is ready for download.

    We'll email you the download link within 2 minutes. Check your inbox (and spam folder).

    Questions? Reply to the email or contact us at hello@tenantshield.com.
    ```
- **Redirect URL (optional):** Leave blank for now (or add a custom thank-you page URL later)

**Advanced Settings:**
- **Payment methods:** Credit card, debit card, Apple Pay, Google Pay (all enabled by default)
- **Require billing address:** No (not needed for digital product)
- **Quantity:** Fixed at 1 (users can't buy multiple)

3. Click **"Create link"**
4. **COPY THE PAYMENT LINK** (looks like: `https://buy.stripe.com/test_abc123xyz`)
5. **Save this link** — you'll use it in:
   - Zapier email templates
   - Framer landing page
   - Social media promotions

---

## STEP 4: CREATE PRODUCT 2 - PAID PARALEGAL CONSULT

1. Click **"Products"** → **"+ Add product"**

**Product Details:**

- **Name:** 10-Minute Paralegal Consultation
- **Description:**
  ```
  Get immediate answers to your California tenant rights questions from a licensed paralegal. Best for quick questions about your lease, deposit dispute, or eviction notice.
  ```
- **Pricing:**
  - **Price:** $15.00 USD
  - **Billing:** One-time
  - **Tax:** Enable automatic tax collection

2. Click **"Save product"**

---

## STEP 5: CREATE PAYMENT LINK FOR PAID CONSULT

1. In the Paid Paralegal Consultation product page, click **"Create payment link"**
2. Configure same as above:
   - Collect name + email
   - Custom success message:
     ```
     Thank you! Your consultation is confirmed.

     We'll email you within 10 minutes to schedule your call with a paralegal.

     Check your inbox for next steps.
     ```

3. Click **"Create link"**
4. **COPY THE PAYMENT LINK**
5. **Save this link** for use in emails/landing page

---

## STEP 6: TEST PAYMENT LINKS

**CRITICAL: Test before launching!**

1. Use Stripe's **Test Mode** (toggle in top-right corner of dashboard)
2. Click on one of your payment links
3. Use a **test card number:**
   - **Card number:** 4242 4242 4242 4242
   - **Expiry:** Any future date (e.g., 12/34)
   - **CVC:** Any 3 digits (e.g., 123)
   - **ZIP:** Any 5 digits (e.g., 12345)

4. Complete the test payment
5. Verify:
   - Success message appears
   - Payment shows up in Stripe Dashboard → Payments
   - Email confirmation is sent (if you configured it)

6. **IMPORTANT:** After testing, switch to **Live Mode** and create the same payment links for real transactions.

---

## STEP 7: SET UP EMAIL DELIVERY (PREMIUM LETTERS)

When someone buys the Premium Letter Package, you need to deliver it. Options:

### Option A: Manual Delivery (Week 1)

1. In Stripe Dashboard, enable **Email Notifications**:
   - Settings → Emails → Customer emails → Enable "Successful payments"

2. When you get a payment notification:
   - Upload Premium Letter Package to Google Drive or Dropbox
   - Send email with download link manually

**Pros:** Simple, no setup
**Cons:** Manual work, not scalable

### Option B: Automated Delivery (Recommended)

1. Upload Premium Letter Package to Google Drive (shareable link)
2. Create a Zapier workflow:
   - **Trigger:** Stripe - New Payment
   - **Filter:** Product = "Premium Letter Package"
   - **Action:** Send Email (Gmail) with download link

**Zapier email template:**

```
Subject: Your Premium Letter Package is Ready! 📄

Hi {{customer_name}},

Thanks for purchasing the Premium Letter Package!

📥 DOWNLOAD YOUR PACKAGE:
https://drive.google.com/file/d/YOUR-FILE-ID/view

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
WHAT'S INCLUDED
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

✓ Demand letter templates
✓ Certified mail instructions
✓ Notary-ready affidavits
✓ Small claims filing checklist
✓ Evidence organization guide

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
WHAT TO DO NEXT
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

1. Download the package
2. Fill in the blanks with your information
3. Print and send via certified mail
4. Keep copies for your records

Questions? Reply to this email.

Good luck!
TenantShield Team
```

**Pros:** Automated, scalable
**Cons:** Requires Zapier ($20/month after free tier)

---

## STEP 8: SET UP CONSULTATION BOOKING (PAID CONSULT)

When someone buys the Paid Paralegal Consult, you need to schedule them. Options:

### Option A: Manual Scheduling

1. Get Stripe payment notification
2. Email customer with Calendly link manually
3. Mark task as complete

### Option B: Automated Scheduling (Recommended)

1. Create Zapier workflow:
   - **Trigger:** Stripe - New Payment
   - **Filter:** Product = "10-Minute Paralegal Consultation"
   - **Action:** Send Email with Calendly link

**Zapier email template:**

```
Subject: Your Consultation is Confirmed! 📅

Hi {{customer_name}},

Thanks for booking a 10-minute paralegal consultation!

📅 SCHEDULE YOUR CALL:
https://calendly.com/your-paralegal-link

Pick a time that works for you. You'll receive a confirmation email with call details.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
BEFORE YOUR CALL
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

To make the most of your 10 minutes, have ready:
✓ Your lease agreement
✓ Emails/texts with your landlord
✓ Photos (if relevant)
✓ Your top 3 questions written down

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

See you soon!
TenantShield Team
```

---

## STEP 9: ENABLE STRIPE TAX (OPTIONAL BUT RECOMMENDED)

Depending on your state/country, you may need to collect sales tax on digital products.

1. In Stripe Dashboard: Settings → Tax
2. Enable **Stripe Tax**
3. Configure:
   - **Product tax category:** Digital products
   - **Tax collection:** Automatic (Stripe calculates based on customer location)

**Note:** Stripe Tax costs 0.5% per transaction. Check your local laws to see if you need it.

---

## STEP 10: SET UP PAYOUTS

1. In Stripe Dashboard: Settings → Payouts
2. Add your **bank account** (routing number + account number)
3. Set **payout schedule:**
   - **Daily:** Receive funds every business day (default)
   - **Weekly:** Receive funds once per week
   - **Monthly:** Receive funds once per month

4. Stripe holds funds for 2-7 days initially (fraud protection). After that, payouts are automatic.

---

## OPTIONAL: CREATE BUNDLE PRICING

If you want to offer a discount for buying both products together:

1. Create a new product: **"Premium Package + Consult"**
   - Price: $39 (instead of $44 separately)
   - Description: "Save $5 — Get Premium Letters + 10-min Paralegal Consult"

2. Create payment link
3. Add to emails/landing page as an upsell option

---

## STRIPE FEES

**Standard pricing:**
- 2.9% + $0.30 per successful card charge
- Example: $29 sale = you receive $27.76 ($29 - $1.14 fee)

**No monthly fee** for basic Stripe account.

**Payouts:** Free (ACH bank transfer in US)

---

## SECURITY & COMPLIANCE

Stripe handles:
- ✅ PCI compliance (you don't store card data)
- ✅ Fraud detection
- ✅ 3D Secure authentication
- ✅ Encryption

You just need to:
- Keep your Stripe API keys secret (don't share publicly)
- Use HTTPS on your website (Framer does this automatically)
- Comply with Stripe's terms of service

---

## TROUBLESHOOTING

### Payment link not working:
- Check you're in **Live Mode** (not Test Mode)
- Verify product is active (not archived)
- Check link wasn't accidentally deleted

### Customer not receiving email:
- Check Stripe email settings (are customer emails enabled?)
- Check customer's spam folder
- Verify email address was entered correctly

### Payout not received:
- Check bank account details are correct
- Check payout schedule (might be weekly/monthly, not daily)
- Check Stripe Dashboard → Payouts for status

### Refund request:
- In Stripe Dashboard: Payments → Find transaction → Click "Refund"
- Refund can be full or partial
- Stripe fee is NOT refunded

---

## NEXT STEPS

Once Stripe is set up:
1. Add payment links to Zapier email templates
2. Add payment links to Framer landing page
3. Test end-to-end flow (form → email → purchase → delivery)
4. Launch marketing

---

## RESOURCES

- Stripe documentation: https://stripe.com/docs
- Stripe support: https://support.stripe.com
- Test card numbers: https://stripe.com/docs/testing

---

**Estimated total time: 15-20 minutes**

**Stripe is very reliable. If you hit issues, their support chat is excellent!**
