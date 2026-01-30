# Campaign Nurture Playbook

## Marketing Campaign Framework for Ministry SaaS

**Version:** 1.0
**Last Updated:** January 30, 2026
**Owner:** Demand Generation

---

## Table of Contents

1. [Nurture Strategy Overview](#nurture-strategy-overview)
2. [Ministry SaaS Prospect Campaigns](#ministry-saas-prospect-campaigns)
3. [Ads & Other Prospect Campaigns](#ads--other-prospect-campaigns)
4. [Customer Retention Campaigns](#customer-retention-campaigns)
5. [Event-Triggered Campaigns](#event-triggered-campaigns)
6. [Campaign Templates](#campaign-templates)
7. [Email Sequences](#email-sequences)
8. [Campaign Measurement](#campaign-measurement)
9. [Workflow Implementation](#workflow-implementation)

---

## Nurture Strategy Overview

### Campaign Philosophy

Our nurture strategy follows a **stage-appropriate, behavior-triggered** approach:

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                        NURTURE CAMPAIGN FRAMEWORK                           │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│    AWARENESS          CONSIDERATION          DECISION          RETENTION   │
│    ─────────          ─────────────          ────────          ─────────   │
│                                                                             │
│    ┌─────────┐        ┌─────────────┐        ┌────────┐        ┌─────────┐ │
│    │ Welcome │──────▶ │ Lead Nurture│──────▶ │ Accel. │──────▶ │Onboard  │ │
│    │ Series  │        │             │        │ Nurture│        │         │ │
│    └─────────┘        └─────────────┘        └────────┘        └─────────┘ │
│         │                   │                     │                  │     │
│         │                   │                     │                  │     │
│    ┌────▼────┐        ┌─────▼─────┐          ┌───▼────┐        ┌────▼────┐ │
│    │ Content │        │ Event     │          │ Sales  │        │ Adoption│ │
│    │ Nurture │        │ Follow-up │          │ Support│        │ Campaigns│ │
│    └─────────┘        └───────────┘          └────────┘        └─────────┘ │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Campaign Prioritization

| Priority | Campaign Type | Target | Goal |
|:--------:|---------------|--------|------|
| 1 | Churn Prevention | At-Risk Customers | Retain |
| 2 | Renewal | Renewal in 90 days | Renew |
| 3 | Sales Support | SQL/Opportunity | Close |
| 4 | Accelerated Nurture | Warm Leads (500-999) | MQL → SQL |
| 5 | Lead Nurture | Cold/Developing Leads | Qualify |
| 6 | Event Follow-up | Event Attendees | Convert |
| 7 | Re-engagement | Dormant (60+ days) | Reactivate |
| 8 | Welcome Series | New Subscribers | Educate |

### Global Campaign Rules

| Rule | Specification |
|------|---------------|
| **Mutual Exclusion** | Contact in only ONE nurture at a time |
| **Priority Override** | Higher priority campaign supersedes lower |
| **Frequency Cap** | Max 3 marketing emails per week |
| **Suppression** | Active sales deal, unsubscribed, bounced |
| **Cool-down** | 48 hours between campaign emails |
| **Re-enrollment** | After exit, wait 30 days before re-enroll |

---

## Ministry SaaS Prospect Campaigns

### Campaign 1: Welcome Series

**Purpose**: Introduce Ministry SaaS to new contacts and build brand awareness.

| Attribute | Value |
|-----------|-------|
| **Segment** | New Subscribers (Database Segment = Ministry SaaS Prospect) |
| **Enrollment Trigger** | New contact created AND Lifecycle Stage = Subscriber |
| **Goal** | Convert Subscriber → Lead |
| **Duration** | 14 days (4 emails) |
| **Success Metric** | 40% progress to Lead stage |

**Email Sequence:**

| Day | Email | Subject | Content Focus | CTA |
|:---:|-------|---------|---------------|-----|
| 0 | Welcome | Welcome to the Ministry SaaS community | Brand intro, mission alignment | Explore resources |
| 3 | Education | How [similar org] reaches 10x more people | Industry challenge, solution overview | Read case study |
| 7 | Value | The complete platform for ministry growth | Feature highlights, value props | Watch demo video |
| 14 | Engagement | Ready to see what's possible? | Consultation offer | Book a call |

**Exit Conditions:**
- Lifecycle Stage changes to Lead, MQL, or SQL
- Books a meeting
- Requests demo
- Unsubscribes

---

### Campaign 2: Lead Nurture (Standard)

**Purpose**: Educate and qualify leads to MQL status.

| Attribute | Value |
|-----------|-------|
| **Segment** | Leads with score < 500 |
| **Enrollment Trigger** | Lifecycle Stage = Lead AND Lead Score < 500 |
| **Goal** | Progress to MQL (score 500+) |
| **Duration** | 45 days (6 emails) |
| **Success Metric** | 25% conversion to MQL |

**Email Sequence:**

| Day | Email | Subject | Content Focus | CTA |
|:---:|-------|---------|---------------|-----|
| 0 | Intro | Your ministry's digital potential | Industry trends, challenges | Download guide |
| 7 | Education | 5 ways leading ministries expand their reach | Best practices | Read article |
| 14 | Case Study | How [Church Name] grew 300% | Customer success story | View full story |
| 21 | Feature | Simplify your content distribution | Product feature deep-dive | See it in action |
| 30 | Social Proof | Join 500+ ministries growing digitally | Testimonials, logos | Request demo |
| 45 | Re-engage | Still exploring? Let's talk | Direct outreach offer | Schedule call |

**Scoring Impact:**
- Email open: +5 points
- Email click: +10 points
- Content download: +15 points
- Demo request: +50 points (exits campaign)

---

### Campaign 3: Accelerated Nurture (Warm Leads)

**Purpose**: Fast-track warm leads to sales-ready status.

| Attribute | Value |
|-----------|-------|
| **Segment** | Leads with score 500-999 |
| **Enrollment Trigger** | Lead Score >= 500 AND < 1000 |
| **Goal** | Progress to SQL (sales acceptance) |
| **Duration** | 21 days (5 emails) |
| **Success Metric** | 40% conversion to SQL |

**Email Sequence:**

| Day | Email | Subject | Content Focus | CTA |
|:---:|-------|---------|---------------|-----|
| 0 | Value | [First Name], let's accelerate your mission | Personalized value prop | Book strategy call |
| 3 | ROI | Calculate your growth potential | ROI calculator, metrics | Use calculator |
| 7 | Comparison | Ministry SaaS vs. doing it alone | Feature comparison | See the difference |
| 14 | Urgency | Limited: Free platform assessment | Exclusive offer | Claim assessment |
| 21 | Direct | Can we schedule 15 minutes? | Personal outreach from AE | Reply to schedule |

**Personalization:**
- Insert ICP tier messaging
- Company-specific challenges (from Company Type)
- Industry-specific metrics

---

### Campaign 4: Event Follow-up

**Purpose**: Convert event attendees into qualified opportunities.

| Attribute | Value |
|-----------|-------|
| **Segment** | Recent event attendees (last 30 days) |
| **Enrollment Trigger** | First Conversion = [Event Form] AND Conversion Date < 30 days |
| **Goal** | Book follow-up meeting |
| **Duration** | 14 days (4 emails) |
| **Success Metric** | 30% meeting booked |

**Email Sequence:**

| Day | Email | Subject | Content Focus | CTA |
|:---:|-------|---------|---------------|-----|
| 1 | Thank You | Great meeting you at [Event Name]! | Event recap, personal note | Connect on LinkedIn |
| 3 | Value Add | [Event] Key Takeaways + Bonus Resource | Exclusive content from event | Download resource |
| 7 | Demo Offer | See how we help ministries like yours | Tailored demo offer | Book demo |
| 14 | Direct | [First Name], quick follow-up from [Event] | Personal outreach | Reply with questions |

**Event-Specific Variants:**
- NRB: Broadcasting/media focus
- C3: Church growth focus
- Exponential: Church planting focus
- Pastor Retreats: Pastoral care focus

---

### Campaign 5: Re-engagement

**Purpose**: Reactivate dormant leads.

| Attribute | Value |
|-----------|-------|
| **Segment** | No activity in 60+ days |
| **Enrollment Trigger** | Last Activity Date > 60 days AND Lifecycle Stage IN (Lead, MQL) |
| **Goal** | Generate re-engagement OR confirm disinterest |
| **Duration** | 30 days (4 emails) |
| **Success Metric** | 15% reactivation, clean list |

**Email Sequence:**

| Day | Email | Subject | Content Focus | CTA |
|:---:|-------|---------|---------------|-----|
| 0 | Check-in | We miss you, [First Name] | Gentle re-engagement | Update preferences |
| 7 | New Value | Big updates you might have missed | Product updates, new features | See what's new |
| 14 | Social Proof | Ministries are growing with us | Recent success stories | Hear their stories |
| 30 | Last Chance | Should we stay in touch? | Preference center, opt-down | Update or unsubscribe |

**Exit Actions:**
- Re-engagement (click/activity): Exit to Lead Nurture
- No activity after 30 days: Move to Sunset list
- Unsubscribe: Remove from marketing

---

### Campaign 6: ICP-Specific Nurture Tracks

#### ICP 1 Track (Enterprise)

| Attribute | Value |
|-----------|-------|
| **Segment** | ICP Tier = ICP 1 |
| **Content Theme** | Enterprise scale, multi-campus, executive messaging |
| **Personalization** | C-level language, ROI focus, strategic partnership |

**Content Emphasis:**
- Multi-location deployment
- Enterprise security & compliance
- Executive ROI case studies
- Dedicated account management
- Custom integrations

#### ICP 2 Track (Media Ministry)

| Attribute | Value |
|-----------|-------|
| **Segment** | ICP Tier = ICP 2 |
| **Content Theme** | Content distribution, audience growth, monetization |
| **Personalization** | Media metrics, reach expansion |

**Content Emphasis:**
- Content distribution network
- Audience analytics
- Monetization strategies
- Cross-platform publishing
- Media ministry case studies

#### ICP 3 Track (Growth Stage)

| Attribute | Value |
|-----------|-------|
| **Segment** | ICP Tier = ICP 3 |
| **Content Theme** | Digital transformation, growth enablement |
| **Personalization** | Growth-focused, digital-first messaging |

**Content Emphasis:**
- Digital transformation playbook
- Affordable growth solutions
- Getting started guides
- Peer church success stories
- DIY vs. platform comparison

---

## Ads & Other Prospect Campaigns

### Campaign: Ads Introduction

**Purpose**: Introduce advertising solutions to qualified prospects.

| Attribute | Value |
|-----------|-------|
| **Segment** | Ads-qualified prospects, no deal |
| **Enrollment Trigger** | Database Segment = "Ads & Other Prospect" AND No associated Deal |
| **Goal** | Generate ad opportunity |
| **Duration** | 30 days (4 emails) |

**Email Sequence:**

| Day | Email | Subject | Content Focus | CTA |
|:---:|-------|---------|---------------|-----|
| 0 | Intro | Reach faith-based audiences at scale | Ads platform intro | Learn more |
| 7 | Value | 10M+ engaged faith-based listeners | Audience reach, demographics | See audience data |
| 14 | Case Study | How [Brand] reached new audiences | Ad success story | Read case study |
| 30 | Offer | Let's discuss your advertising goals | Media planning offer | Schedule call |

---

### Campaign: Ads Cross-Sell (from Ministry SaaS)

**Purpose**: Introduce ads to existing Ministry SaaS customers.

| Attribute | Value |
|-----------|-------|
| **Segment** | Ministry SaaS Customers with media potential |
| **Enrollment Trigger** | Lifecycle Stage = Customer AND Company Type IN (Media Ministry, Podcast) |
| **Goal** | Cross-sell advertising product |
| **Duration** | 21 days (3 emails) |

**Email Sequence:**

| Day | Email | Subject | Content Focus | CTA |
|:---:|-------|---------|---------------|-----|
| 0 | Intro | [First Name], expand your ministry's impact | Ads intro for existing customers | Learn about ads |
| 10 | Value | New revenue stream for your ministry | Monetization opportunity | Explore options |
| 21 | Offer | Exclusive: Priority ad placement | Customer-exclusive offer | Schedule review |

---

## Customer Retention Campaigns

### Campaign: Onboarding (New Customers)

**Purpose**: Activate new customers and drive platform adoption.

| Attribute | Value |
|-----------|-------|
| **Segment** | New Customers (0-90 days) |
| **Enrollment Trigger** | Deal Stage = Closed Won |
| **Goal** | Full platform activation |
| **Duration** | 90 days (8 emails) |

**Email Sequence:**

| Day | Email | Subject | Content Focus | CTA |
|:---:|-------|---------|---------------|-----|
| 0 | Welcome | Welcome to Ministry SaaS! Let's get started | Getting started guide | Begin setup |
| 3 | Setup | Complete your profile in 5 minutes | Profile completion | Complete profile |
| 7 | First Win | Upload your first piece of content | First action | Upload content |
| 14 | Feature 1 | Unlock the power of [Key Feature] | Feature education | Try feature |
| 21 | Check-in | How's it going? Quick tips for success | Tips, support resources | Contact support |
| 30 | Feature 2 | Advanced feature: [Feature Name] | Advanced feature | Enable feature |
| 60 | Review | Your first 60 days: A quick review | Progress summary | Schedule review |
| 90 | Success | Ready to grow? Let's plan your next steps | Expansion discussion | Plan next phase |

---

### Campaign: Feature Adoption

**Purpose**: Drive adoption of underutilized features.

| Attribute | Value |
|-----------|-------|
| **Segment** | Customers not using feature X |
| **Enrollment Trigger** | Feature X usage = 0 AND Account age > 30 days |
| **Goal** | Feature activation |
| **Duration** | 21 days (3 emails) |

**Email Sequence:**

| Day | Email | Subject | Content Focus | CTA |
|:---:|-------|---------|---------------|-----|
| 0 | Awareness | Did you know you can [Feature Benefit]? | Feature introduction | Learn more |
| 7 | Tutorial | How to [Feature Action] in 3 easy steps | Step-by-step guide | Try it now |
| 21 | Support | Need help with [Feature]? | Support offer | Get help |

---

### Campaign: At-Risk Intervention

**Purpose**: Prevent churn among at-risk customers.

| Attribute | Value |
|-----------|-------|
| **Segment** | At-Risk Customers (declining usage, support issues) |
| **Enrollment Trigger** | Risk Score = High OR Usage declined > 30% |
| **Goal** | Re-engagement, issue resolution |
| **Duration** | 14 days (4 touchpoints) |

**Sequence:**

| Day | Action | Channel | Content Focus |
|:---:|--------|---------|---------------|
| 0 | Alert | Internal | Notify CSM of at-risk account |
| 1 | Email | Email | Check-in, value reminder |
| 3 | Call | Phone | CSM outreach call |
| 7 | Email | Email | Success resources, support offer |
| 14 | Escalation | Internal | If no response, escalate to manager |

---

### Campaign: Renewal

**Purpose**: Secure contract renewals.

| Attribute | Value |
|-----------|-------|
| **Segment** | Renewal date within 90 days |
| **Enrollment Trigger** | Contract end date - 90 days |
| **Goal** | Renewal + potential expansion |
| **Duration** | 90 days (5 touchpoints) |

**Sequence:**

| Day | Action | Owner | Content Focus |
|:---:|--------|-------|---------------|
| -90 | Email | Marketing | Year in review, success metrics |
| -60 | Call | CSM | Renewal discussion, expansion opportunity |
| -45 | Email | Marketing | Renewal benefits, what's coming |
| -30 | Email | AE/CSM | Contract proposal |
| -14 | Urgency | AE | Final renewal push |

---

### Campaign: Leader Engagement (Platform Leaders)

**Purpose**: Keep leaders active and engaged on the platform.

| Attribute | Value |
|-----------|-------|
| **Segment** | Leader contacts (Contact Type = Leader OR Associated Leader exists) |
| **Enrollment Trigger** | Leader identified AND Activity < 30 days |
| **Goal** | Maintain leader engagement |
| **Duration** | Ongoing (monthly) |

**Monthly Touchpoints:**

| Week | Content Type | Topic |
|:----:|--------------|-------|
| 1 | Newsletter | Platform updates, new features |
| 2 | Best Practices | Content optimization tips |
| 3 | Community | Leader spotlight, peer content |
| 4 | Support | Resources, help content |

---

### Campaign: Churned Win-Back

**Purpose**: Re-engage churned customers.

| Attribute | Value |
|-----------|-------|
| **Segment** | Lifecycle Stage = Churned, churned > 90 days ago |
| **Enrollment Trigger** | Date entered Churned > 90 days AND < 18 months |
| **Goal** | Re-acquisition |
| **Duration** | 60 days (4 emails) |

**Email Sequence:**

| Day | Email | Subject | Content Focus | CTA |
|:---:|-------|---------|---------------|-----|
| 0 | Re-intro | [First Name], a lot has changed | Product updates since churn | See what's new |
| 14 | Value | What you've been missing | New features, improvements | Explore features |
| 30 | Offer | Special offer to welcome you back | Win-back incentive | Claim offer |
| 60 | Last | Final invitation to reconnect | Final outreach | Let's talk |

---

## Event-Triggered Campaigns

### Trigger: High-Value Form Submission

| Trigger | Form Type | Action |
|---------|-----------|--------|
| Demo Request | Demo form | Immediate sales notification + confirmation email |
| Pricing Request | Pricing form | Sales alert + pricing follow-up sequence |
| Contact Sales | Contact form | Route to AE + acknowledgment email |
| Content Download | Gated content | Enroll in content nurture |

### Trigger: Website Behavior

| Trigger | Behavior | Action |
|---------|----------|--------|
| Pricing Page Visit | 2+ visits in 7 days | Add to high-intent list, trigger AE notification |
| Case Study View | Viewed 3+ case studies | Enroll in accelerated nurture |
| Competitor Page | Viewed comparison content | Add competitive flag, send comparison email |

### Trigger: Engagement Milestones

| Trigger | Milestone | Action |
|---------|-----------|--------|
| Email Engagement | Opened 5+ emails in 30 days | Promote to higher priority nurture |
| Score Threshold | Lead score crosses 500 | Move from standard to accelerated nurture |
| Stage Change | Moved to MQL | Notify BDR, enroll in MQL sequence |

---

## Campaign Templates

### Email Template Structure

```
┌─────────────────────────────────────────────────────────────────┐
│ FROM: [Personalized Sender Name] <email@ministrysaas.com>      │
│ SUBJECT: [Personalized, A/B tested subject line]               │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  [HEADER: Ministry SaaS logo, clean design]                    │
│                                                                 │
│  Hi [First Name],                                              │
│                                                                 │
│  [OPENING: Hook relevant to segment/stage]                     │
│                                                                 │
│  [BODY: 2-3 short paragraphs with value proposition]           │
│                                                                 │
│  [SUPPORTING CONTENT: Bullet points, image, or quote]          │
│                                                                 │
│  [CTA: Single, clear call-to-action button]                    │
│                                                                 │
│  [SIGNATURE: Personal signature with photo]                    │
│  [Name]                                                         │
│  [Title]                                                        │
│                                                                 │
│  [FOOTER: Unsubscribe, preferences, address]                   │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Subject Line Formulas

| Type | Formula | Example |
|------|---------|---------|
| Personalized | [First Name], [benefit/question] | "John, ready to reach 10x more people?" |
| Curiosity | [Number] ways to [outcome] | "5 ways leading churches expand their reach" |
| Social Proof | How [Company] achieved [result] | "How Elevation Church grew 300%" |
| Urgency | [Time-sensitive offer] | "48 hours: Your exclusive demo access" |
| Question | [Pain point question]? | "Struggling to reach beyond Sunday?" |
| Direct | [Simple, clear statement] | "Your ministry growth roadmap" |

### Personalization Tokens

| Token | Property | Example |
|-------|----------|---------|
| `{{contact.firstname}}` | First Name | John |
| `{{contact.company}}` | Company | Grace Church |
| `{{company.icp_tier}}` | ICP Tier | ICP 1 |
| `{{company.company_type}}` | Company Type | Church |
| `{{company.church_size_attendance}}` | Church Size | 1,000+ |
| `{{deal.amount}}` | Deal Amount | $50,000 |
| `{{owner.firstname}}` | Owner First Name | Sarah |

---

## Campaign Measurement

### KPIs by Campaign Type

#### Acquisition Campaigns (Ministry SaaS Prospects)

| Metric | Target | Calculation |
|--------|--------|-------------|
| Open Rate | >25% | Opens / Delivered |
| Click Rate | >3% | Clicks / Delivered |
| MQL Conversion | >15% | MQLs / Enrolled |
| Meeting Booked | >5% | Meetings / Enrolled |
| Influenced Pipeline | Track | Pipeline $ where campaign touchpoint |

#### Retention Campaigns (Customers)

| Metric | Target | Calculation |
|--------|--------|-------------|
| Retention Rate | >90% | Renewed / Up for Renewal |
| Feature Adoption | +20% | New feature users / Campaign enrolled |
| Expansion Revenue | Track | Upsell $ from campaign contacts |
| NPS Impact | +5 points | Post-campaign NPS vs. baseline |

### Campaign Attribution

| Model | Use Case | Property |
|-------|----------|----------|
| First Touch | Lead source credit | `hs_analytics_first_touch_converting_campaign` |
| Last Touch | Conversion credit | `hs_analytics_last_touch_converting_campaign` |
| Linear | Multi-touch journey | Custom attribution property |
| Campaign Membership | Influence tracking | Campaign member lists |

### Reporting Cadence

| Report | Frequency | Audience |
|--------|-----------|----------|
| Campaign Performance Summary | Weekly | Marketing team |
| MQL/SQL from Campaigns | Weekly | Demand Gen, Sales |
| Campaign Influence on Pipeline | Monthly | Marketing leadership |
| Nurture Funnel Analysis | Monthly | Marketing Ops |
| Customer Campaign Impact | Monthly | Customer Marketing, CS |

---

## Workflow Implementation

### HubSpot Workflow Structure

#### Enrollment Workflow Example (Lead Nurture)

```
WORKFLOW: Lead Nurture - Standard
├── TRIGGER: Lifecycle Stage = Lead AND Lead Score < 500
│
├── ENROLLMENT CRITERIA:
│   └── Database Segment = Ministry SaaS Prospect
│   └── NOT in active nurture campaign
│   └── Email Status = Valid
│   └── NOT Unsubscribed
│
├── ACTIONS:
│   ├── Day 0: Send Email 1 (Intro)
│   ├── Day 0: Set Property "Active Nurture" = "Lead Nurture Standard"
│   ├── Day 7: IF/THEN Branch
│   │   ├── IF clicked previous email: Send Email 2 (Education)
│   │   └── ELSE: Send Email 2 (Education) anyway
│   ├── Day 14: Send Email 3 (Case Study)
│   ├── Day 21: Send Email 4 (Feature)
│   ├── Day 30: Send Email 5 (Social Proof)
│   └── Day 45: Send Email 6 (Re-engage)
│
├── GOAL CRITERIA (exits workflow):
│   └── Lifecycle Stage becomes MQL, SQL, or Opportunity
│   └── Books a meeting
│   └── Requests demo
│
└── END ACTIONS:
    └── Clear Property "Active Nurture"
    └── Add to "Nurture Completed" list
```

#### Suppression Logic

```
WORKFLOW: Suppression Check
├── ALWAYS SUPPRESS IF:
│   ├── Deal Stage IN (Qualifying, Pitch, Proposal, Contract Sent)
│   ├── Owner has contacted in last 7 days
│   ├── Meeting scheduled in next 14 days
│   ├── Unsubscribed from all email
│   ├── Email hard bounced
│   └── Contact Type = Competitor
```

### Workflow Naming Convention

```
[SEGMENT]-[STAGE]-[CAMPAIGN TYPE]-[VERSION]

Examples:
- MSAAS-LEAD-NURTURE-V1
- MSAAS-MQL-ACCELERATED-V2
- CUS-NEW-ONBOARDING-V1
- CUS-ATRISK-INTERVENTION-V1
- ADS-PROSPECT-INTRO-V1
```

### Campaign Folder Structure

```
📁 Workflows
├── 📁 Ministry SaaS Prospects
│   ├── 📁 Welcome & Onboarding
│   │   └── Welcome Series
│   ├── 📁 Lead Nurture
│   │   ├── Standard Nurture
│   │   └── Accelerated Nurture
│   ├── 📁 Event Campaigns
│   │   ├── NRB Follow-up
│   │   ├── C3 Follow-up
│   │   └── [Other Events]
│   └── 📁 Re-engagement
│       └── Dormant Re-engagement
├── 📁 Ads & Other Prospects
│   ├── Ads Introduction
│   └── Ads Cross-sell
├── 📁 Customer Retention
│   ├── 📁 Onboarding
│   │   └── New Customer Onboarding
│   ├── 📁 Feature Adoption
│   │   └── [Feature-specific campaigns]
│   ├── 📁 At-Risk
│   │   └── At-Risk Intervention
│   ├── 📁 Renewal
│   │   └── Renewal Campaign
│   └── 📁 Leader Engagement
│       └── Leader Monthly Engagement
└── 📁 Win-back
    └── Churned Win-back
```

---

## Appendix: Quick Reference

### Campaign Enrollment Quick Reference

| Campaign | Segment Property | Lifecycle Stage | Score | Other Criteria |
|----------|------------------|-----------------|-------|----------------|
| Welcome | Ministry SaaS Prospect | Subscriber | Any | New contact |
| Lead Nurture | Ministry SaaS Prospect | Lead | < 500 | Not in other nurture |
| Accelerated | Ministry SaaS Prospect | Lead, MQL | 500-999 | Not in other nurture |
| Event Follow-up | Ministry SaaS Prospect | Any | Any | Event attendance < 30 days |
| Re-engagement | Ministry SaaS Prospect | Lead, MQL | Any | No activity 60+ days |
| Onboarding | Customer | Customer | N/A | New customer |
| At-Risk | Customer | Customer | N/A | Risk score high |
| Renewal | Customer | Customer | N/A | Renewal < 90 days |
| Ads Intro | Ads Prospect | Any | Any | No deal |
| Win-back | Churned | Churned | Any | Churned 90+ days |

### Email Frequency Caps

| Segment | Max Emails/Week | Cool-down |
|---------|:---------------:|:---------:|
| Hot Leads (1000+) | 3 | 24 hours |
| Warm Leads (500-999) | 3 | 24 hours |
| Standard Leads | 2 | 48 hours |
| Customers | 2 | 48 hours |
| At-Risk Customers | 3 | 24 hours |
| Dormant | 1 | 1 week |

---

*Campaign Nurture Playbook maintained by Demand Generation. For new campaign requests, submit through Marketing Ops with segment definition, goal metrics, and content requirements.*
