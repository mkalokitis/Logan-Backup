# GHL WORKFLOW PROMPTS — Realtor Social Media Funnel (V2)

---

## UPDATED FORM (With Disclaimer)

**Add this to the landing page form:**

---

**FORM FIELD: Instagram/Facebook Profile Link**

**Help Text:**
> IMPORTANT: Your profile must be **PUBLIC** for us to analyze it.
>
> [How to make your Instagram public](#)
> [How to make your Facebook public](#)

**Checkbox (required):**
☐ I confirm my profile is public and can be viewed by anyone

**Error Message (if field empty):**
"Please provide your profile link"

---

## UPDATED WORKFLOW: SWQT FORM SUBMISSION

### TRIGGER: Form submitted on Realtor Landing Page

### CONDITION CHECK:

**Check:** Is the profile link provided?

- **IF NO:** Send email: "We need your profile link" → Ask them to resubmit

- **IF YES:** Continue to GHL Workflow:

---

## WORKFLOW 1: LEAD CAPTURE + PROFILE CHECK

**Actions:**

1. **Create Contact**
   - Name: from form
   - Email: from form
   - Profile URL: from form
   - Tags: `realtor-lead`, `swot-pending`
   - Source: `realtor-landing-page`

2. **Add to Pipeline**
   - Pipeline: "Booked 247 Realtor"
   - Stage: "Profile Submitted"

3. **Check Profile (Automated)**

   - Try to fetch profile URL via web
   - If accessible (public): Continue
   - If blocked (private): Send "Profile Private" email

---

## WORKFLOW 2A: PROFILE IS PUBLIC (Automated Analysis)

**Trigger:** Profile is accessible

**Actions:**

1. **Fetch Profile Data** (via web)
   - Follower count
   - Recent post count (last 10)
   - Engagement estimates (if available)

2. **Calculate SWOT Score** (automated)
   - Based on metrics collected
   - Assign score 0-100

3. **Generate SWOT Report** (I create this)

4. **Send SWOT Report Email**

5. **Update Contact**
   - Tags: `swot-sent`, `profile-public`
   - Stage: "SWOT Sent"

---

## WORKFLOW 2B: PROFILE IS PRIVATE

**Trigger:** Cannot fetch profile (private)

**Actions:**

1. **Send Email** (Template: "Make Your Profile Public")

```
Subject: One quick step before we send your audit

Hi [First Name],

Thanks for requesting your free SWOT analysis!

We couldn't access your profile because it's currently set to **PRIVATE**.

Here's how to fix it:

📱 **Instagram:**
1. Go to your profile
2. Tap the menu (three lines)
3. Settings → Privacy → Account
4. Set "Private Account" to OFF

📘 **Facebook:**
1. Go to Settings & Privacy → Settings
2. Who can see your future posts? → Set to "Public"
3. Profile and Tagging → Set to "Public"

🔗 **Once public, click here to rerun your audit:**
[LINK TO FORM]

We promise we won't spam you — this is just so we can analyze your page.

— Logan
Booked 247 — We think. You post.
```

2. **Update Contact**
   - Tags: `swot-pending`, `profile-private`
   - Stage: "Awaiting Public Profile"

3. **Wait:** 5 days

4. **Send Follow-Up:** "Did you make your profile public?"

---

## WORKFLOW 3: SWQT EMAIL (After Public Profile Confirmed)

**Same as before — automated email with:**

- Overall Score (XX/100)
- Rating (Excellent/Good/Needs Work/Weak)
- Strengths (based on data found)
- Weaknesses (based on data found)
- Opportunities
- Threats
- Top 3 Quick Wins
- Content Ideas for Week
- CTA to Subscribe ($19/mo)

---

## WORKFLOW 4: FOLLOW-UP SEQUENCE

Same as V1 — 3-day, 5-day, 30-day follow-ups if no purchase.

---

## WORKFLOW 5: NEW SUBSCRIPTION

Same as V1 — Stripe payment → Welcome email → Active Client

---

## WORKFLOW 6: CANCELLATION

Same as V1 — Churn flow

---

## UPDATED PIPELINE STAGES

1. **Lead** — Form submitted
2. **Profile Submitted** — Awaiting check
3. **Awaiting Public Profile** — Private, sent instructions
4. **SWOT Sent** — Audit delivered
5. **Opportunity** — Considering
6. **Active Client** — Paying
7. **Cancelled** — Churned

---

## UPDATED TAGS

- `realtor-lead`
- `realtor-profile-submitted`
- `realtor-profile-private`
- `realtor-profile-public`
- `realtor-swot-sent`
- `realtor-active`
- `realtor-churned`

---

## KEY IMPROVEMENTS IN V2:

✅ Form requires profile link + checkbox confirming it's public
✅ Error message if no link provided
✅ Automated profile check (public vs private)
✅ If private → instructions sent automatically
✅ No manual involvement needed from Mark
✅ Fully automated SWOT based on available data

---

This way: You (Mark) are never involved. I handle it all. Customer makes profile public → I analyze → I email. Done.