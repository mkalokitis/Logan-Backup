# GHL WORKFLOW PROMPTS — Realtor Social Media Funnel

---

## WORKFLOW 1: FREE SWOT SIGNUP (Lead Capture)

**Trigger:** Form submitted on Realtor Landing Page

**Actions:**

1. **Create Contact**
   - Add to GHL with:
     - Name: from form
     - Email: from form
     - Phone: (optional)
     - Tags: `realtor-lead`, `swot-pending`
     - Source: `realtor-landing-page`

2. **Add to Pipeline**
   - Pipeline: "Booked 247 Realtor"
   - Stage: "SWOT Pending"

3. **Internal Notification**
   - Send email to you: "New SWOT request from [Name] — [Profile Link]"

4. **Wait:** 2 minutes (for you to perform SWOT analysis)

5. **Update Contact**
   - Tag: `swot-completed`
   - Stage: "SWOT Sent"

---

## WORKFLOW 2: SEND SWOT EMAIL (With Template)

**Trigger:** You complete the SWOT analysis (manual trigger OR after you update contact)

**Actions:**

1. **Send Email** (Template: "SWOT Analysis Report")

**Email Template:**

```
Subject: Your Free Social Media Audit Results

Hi [First Name],

Thanks for your interest! Here's your free SWOT analysis for [Profile Name].

---

📊 YOUR SCORE: [XX/100]

RATING: [Excellent / Good / Needs Work / Weak]

---

✅ STRENGTHS

1. [e.g., Posting consistency]
   - Evidence: [e.g., Posts 3x/week]

2. [e.g., Engagement]
   - Evidence: [e.g., 3%+ engagement rate]

3. [e.g., Content mix]
   - Evidence: [e.g., Mix of educational + personal]

---

❌ WEAKNESSES

1. [e.g., Low video presence]
   - Fix: Start posting Reels 2x/week

2. [e.g., Generic hooks]
   - Fix: Use more specific, personal hooks

3. [e.g., No CTA in posts]
   - Fix: Add "Save this post" or "DM me" CTAs

---

🎯 TOP 3 QUICK WINS (Next 24 Hours)

1. [Action 1]
2. [Action 2]
3. [Action 3]

---

📝 CONTENT IDEAS FOR THIS WEEK

[Post 1]: [Hook/Caption]
[Post 2]: [Hook/Caption]
[Post 3]: [Hook/Caption]

---

💬 NEXT STEPS

Want us to keep delivering weekly content? Here's what we offer:

**Social Media Manager — $19/mo**
- Weekly ideas + hooks
- Monthly scorecard
- Trend alerts

**Newsletter Writer — $14/mo**
- Monthly newsletter
- Market insights

**Both — $29/mo**

👉 [Subscribe Here]

No commitment. Cancel anytime.

---

Still have questions? Just reply to this email.

— Logan
Booked 247 — We think. You post.

```

---

2. **Update Contact**
   - Stage: "SWOT Sent"
   - Wait: 3 days

---

## WORKFLOW 3: FOLLOW-UP (If No Subscribe)

**Trigger:** 3 days after SWOT sent, no purchase

**Actions:**

1. **Send Email** (Template: "Did you see your audit?")

```
Subject: Quick question about your audit

Hi [First Name],

Just checking if you saw your SWOT results.

Your biggest win was [strength]. Your quick fix is [weakness].

We've helped [XX] Realtors get consistent content. Would weekly ideas help you?

- Social Media Manager: $19/mo
- Newsletter: $14/mo
- Both: $29/mo

👉 [See Plans Here]

Happy to answer questions — just reply.

— Logan
```

2. **Wait:** 5 days

3. **Send Email** (Template: "Last chance")

```
Subject: Your free audit is ready to view

Hey [First Name],

Just a reminder — your free audit is waiting.

Your score was [XX/100]. Here's what to do next:
1. [Quick win]
2. [Quick win]

Or let us handle it — $19/mo and we deliver ideas weekly.

👉 [Get Started]

Talk soon,
— Logan
```

4. **If still no response:**
   - Add tag: `cold-lead`
   - Move to "Nurture" list

---

## WORKFLOW 4: NEW SUBSCRIPTION (Stripe Payment)

**Trigger:** Payment succeeds in Stripe → webhook received

**Actions:**

1. **Update Contact**
   - Tags: `realtor-active`, `[service-tier]`
   - Stage: "Active Client"
   - Subscription: [Tier] — [Price/mo]
   - Start Date: [Today's date]

2. **Send Welcome Email** (Template: "Welcome to Booked 247")

```
Subject: You're In! Here's What Happens Next

Hi [First Name],

Welcome to Booked 247! 🎉

Here's what to expect:

📅 Every Tuesday:
- Your weekly content pack arrives
- 3-5 post ideas
- Hooks ready to copy-paste

📧 Every 1st of Month:
- Your newsletter arrives
- Ready to send to your database

📊 Monthly:
- Your scorecard update
- See your growth

---

Need anything? Just reply to this email.

— Logan
Booked 247 — We think. You post.
```

3. **Add to Client Workflow**
   - Trigger: Subscription active
   - Start recurring content delivery

---

## WORKFLOW 5: CANCELLATION (Churn)

**Trigger:** Stripe payment fails / Subscription cancelled

**Actions:**

1. **Update Contact**
   - Tag: `churned`
   - Stage: "Cancelled"
   - Remove: `[service-tier]` tag
   - Add: `re churned` tag

2. **Send Goodbye Email**

```
Subject: We're sorry to see you go

Hi [First Name],

Thanks for being part of Booked 247.

Your content ideas from [time period] are yours to keep using.

If you ever want to come back, we'll be here.

— Logan
Booked 247 — We think. You post.
```

3. **Wait:** 30 days

4. **Send Re-engagement Email**

```
Subject: We miss you!

Hi [First Name],

It's been 30 days since you left. How's your social media going?

If you ever need us again, we're here.

— Logan
```

---

## PIPELINE STAGES

1. **Lead** — Form submitted
2. **SWOT Pending** — Awaiting analysis
3. **SWOT Sent** — Audit delivered
4. **Opportunity** — Considering subscription
5. **Active Client** — Paying subscriber
6. **Cancelled** — Churned

---

## TAGS TO USE

- `realtor-lead`
- `realtor-swot-pending`
- `realtor-swot-sent`
- `realtor-active`
- `realtor-sm` — Social Media Manager
- `realtor-nl` — Newsletter
- `realtor-bundle` — Both
- `realtor-churned`
- `realtor-cold`

---

## STRIPE SETUP

1. Connect Stripe to GHL
2. Create products:
   - Social Media Manager: $19/mo (recurring)
   - Newsletter Writer: $14/mo (recurring)
   - Bundle: $29/mo (recurring)
3. Set up webhooks to trigger workflows on payment events
4. Test with $1 test purchase

---

**Put it all together:** Landing page → Form → SWOT Workflow → Subscription Workflow → Ongoing delivery