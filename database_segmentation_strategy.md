# Database Segmentation Strategy

## Ministry SaaS CRM Segmentation Framework

**Version:** 1.0
**Last Updated:** January 30, 2026
**Owner:** Marketing Operations & Data Operations

---

## Table of Contents

1. [Segmentation Overview](#segmentation-overview)
2. [Master Database Segments](#master-database-segments)
3. [Ministry SaaS Prospects Segmentation](#ministry-saas-prospects-segmentation)
4. [Ads & Other Prospects Segmentation](#ads--other-prospects-segmentation)
5. [Current Leaders (Retention) Segmentation](#current-leaders-retention-segmentation)
6. [Segment Implementation in HubSpot](#segment-implementation-in-hubspot)
7. [Campaign Nurture Segments](#campaign-nurture-segments)
8. [Active List Definitions](#active-list-definitions)
9. [Segment Maintenance & Hygiene](#segment-maintenance--hygiene)
10. [Cross-Segment Rules](#cross-segment-rules)

---

## Segmentation Overview

### Segmentation Philosophy

The Ministry SaaS database is segmented into three primary business lines with distinct go-to-market motions:

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                         MINISTRY SAAS DATABASE                              │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────────────────┐ │
│  │   MINISTRY      │  │    ADS &        │  │    CURRENT LEADERS          │ │
│  │   SAAS          │  │    OTHER        │  │    (Retention)              │ │
│  │   PROSPECTS     │  │    PROSPECTS    │  │                             │ │
│  │                 │  │                 │  │                             │ │
│  │  Main Product   │  │  Advertising    │  │  Existing customers who     │ │
│  │  Pipeline       │  │  Solutions      │  │  are also prospects for:    │ │
│  │                 │  │  Pipeline       │  │  - Expansion                │ │
│  │                 │  │                 │  │  - Cross-sell               │ │
│  │                 │  │                 │  │  - Retention                │ │
│  └─────────────────┘  └─────────────────┘  └─────────────────────────────┘ │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Segmentation Hierarchy

```
Level 1: Business Line
├── Ministry SaaS (Main Product)
├── Ads & Other (Advertising)
└── Current Leaders (Retention/Expansion)

Level 2: Lifecycle Stage
├── Subscriber
├── Lead
├── MQL
├── SQL
├── Opportunity
├── Customer
└── Churned

Level 3: ICP & Fit
├── ICP Tier (ICP 1, ICP 2, ICP 3, IPP)
├── Company Segment (Whale → Mouse)
└── Company Type (Church, Parachurch, Media Ministry, etc.)

Level 4: Engagement & Intent
├── Lead Score Band (Hot, Warm, Cold, Developing)
├── Buying Stage (Aware, Considering, Deciding)
└── Activity Recency (Active, Dormant, Disengaged)

Level 5: Campaign-Specific
├── Event Attendees
├── Content Engagers
├── Product Interest
└── Behavioral Triggers
```

---

## Master Database Segments

### Segment 1: Ministry SaaS Prospects

**Definition**: Contacts and companies who are prospects for the core Ministry SaaS platform (Pray Channel pipeline).

**Inclusion Criteria**:
- Lifecycle Stage IN (Subscriber, Lead, MQL, SQL, Opportunity)
- NOT a current customer (Lifecycle Stage ≠ Customer)
- NOT Churned OR (Churned > 12 months ago AND re-engaged)
- Deal Pipeline = "Pray Channel" OR no active deal in "Ads and Other"

**Exclusion Criteria**:
- Company Type = Competitor
- Contact Type = Vendor
- Email Status = Bounced or Invalid
- Unsubscribed from all communications

### Segment 2: Ads & Other Prospects

**Definition**: Contacts and companies who are prospects for advertising and ancillary products.

**Inclusion Criteria**:
- Has deal in "Ads and Other" pipeline OR
- Company Type IN (Media Channel, Broadcasting platform, Ads Agency) OR
- Primary interest indicated as advertising/sponsorship
- Lifecycle Stage IN (Subscriber, Lead, MQL, SQL, Opportunity)

**Exclusion Criteria**:
- Email Status = Bounced or Invalid
- Unsubscribed from all communications

### Segment 3: Current Leaders (Retention/Expansion)

**Definition**: Customers who are content creators/leaders on the platform and are targets for retention, expansion, or cross-sell.

**Inclusion Criteria**:
- Lifecycle Stage = Customer OR
- Contact Type = Leader OR
- Has associated Leader object OR
- Associated Company Lifecycle Stage = Customer

**Sub-Segments**:
- Active Customers (healthy)
- At-Risk Customers
- Expansion Ready
- Cross-sell Candidates

---

## Ministry SaaS Prospects Segmentation

### Primary Segmentation Dimensions

#### By ICP Tier

| Segment Name | Criteria | Size (Est.) | Priority |
|--------------|----------|-------------|----------|
| Ministry SaaS - ICP 1 Prospects | ICP Tier = "ICP 1" AND Lifecycle Stage ∈ (Lead, MQL, SQL, Opportunity) | ~500 | Highest |
| Ministry SaaS - ICP 2 Prospects | ICP Tier = "ICP 2" AND Lifecycle Stage ∈ (Lead, MQL, SQL, Opportunity) | ~1,200 | High |
| Ministry SaaS - ICP 3 Prospects | ICP Tier = "ICP 3" AND Lifecycle Stage ∈ (Lead, MQL, SQL, Opportunity) | ~2,500 | Medium |
| Ministry SaaS - IPP Prospects | ICP Tier = "IPP" AND Lifecycle Stage ∈ (Lead, MQL, SQL, Opportunity) | ~300 | Partnership |

#### By Company Segment (Revenue)

| Segment Name | Criteria | Nurture Strategy |
|--------------|----------|------------------|
| Whale Prospects | Company Segment = "Whale" | Enterprise nurture, white-glove |
| Elephant Prospects | Company Segment = "Elephant" | High-touch nurture |
| Deer Prospects | Company Segment = "Deer" | Standard nurture |
| Rabbit Prospects | Company Segment = "Rabbit" | Efficient nurture |
| Mouse Prospects | Company Segment = "Mouse" | Product-led nurture |

#### By Lifecycle Stage

| Segment Name | Criteria | Marketing Goal |
|--------------|----------|----------------|
| Ministry SaaS - Subscribers | Lifecycle Stage = "Subscriber" | Convert to Lead |
| Ministry SaaS - Leads | Lifecycle Stage = "Lead" | Qualify to MQL |
| Ministry SaaS - MQLs | Lifecycle Stage = "MQL" | Accelerate to SQL |
| Ministry SaaS - SQLs | Lifecycle Stage = "SQL" | Support sales conversion |
| Ministry SaaS - Open Opportunities | Lifecycle Stage = "Opportunity" | Deal support content |

#### By Lead Score Band

| Segment Name | Score Range | Action |
|--------------|-------------|--------|
| Hot Prospects | 1,000 - 2,000 | Immediate sales engagement |
| Warm Prospects | 500 - 999 | Accelerated nurture |
| Developing Prospects | 100 - 499 | Standard nurture |
| Cold Prospects | 0 - 99 | Long-term nurture |
| Disqualified | < 0 | Exclude from marketing |

#### By Company Type

| Segment Name | Company Type Value | Content Focus |
|--------------|-------------------|---------------|
| Church Prospects | Church (Mega Church) | Multi-campus, attendance growth |
| Parachurch Prospects | Parachurch organization | Mission amplification |
| Media Ministry Prospects | Media Ministry | Content distribution |
| Podcast Prospects | Podcast (Podcaster) | Audience growth |
| Nonprofit Prospects | Nonprofit | Donor engagement |
| Agency Prospects | Agency | Partner solutions |

### Behavioral Segments

#### By Engagement Level

| Segment Name | Criteria | Next Action |
|--------------|----------|-------------|
| Highly Engaged | Email opens > 5 (last 30 days) AND Website visits > 3 | Accelerate |
| Moderately Engaged | Email opens 2-5 (last 30 days) OR Website visits 1-3 | Maintain |
| Low Engagement | Email opens < 2 (last 30 days) AND No website visits | Re-engage |
| Dormant | No activity in 60+ days | Win-back campaign |
| Disengaged | No activity in 90+ days AND No opens in 120 days | Sunset warning |

#### By Buying Stage

| Segment Name | Signals | Content Type |
|--------------|---------|--------------|
| Awareness Stage | First website visit, blog reader, subscriber | Educational content |
| Consideration Stage | Multiple page views, downloaded content, event attended | Case studies, comparisons |
| Decision Stage | Pricing page view, demo request, sales call | ROI content, objection handling |

---

## Ads & Other Prospects Segmentation

### Primary Segments

| Segment Name | Criteria | Sales Approach |
|--------------|----------|----------------|
| Ads - Active Pipeline | Deal in "Ads and Other" pipeline AND Deal Stage NOT IN (Closed Won, Closed Lost) | AE owned |
| Ads - Past Customers | Has Closed Won deal in "Ads and Other" AND No current active deal | Renewal outreach |
| Ads - Qualified Prospects | Company Type IN (Media Channel, Broadcasting platform) AND No deal | Marketing nurture |
| Ads - Lost Opportunities | Deal Stage = "Closed Lost" in "Ads and Other" AND Close Date > 6 months ago | Win-back |

### By Ad Product Interest

| Segment Name | Signal | Nurture Content |
|--------------|--------|-----------------|
| Podcast Advertisers | Has podcast, interested in ads | Audio ad case studies |
| Video Advertisers | Has video content, interested in ads | Video ad case studies |
| Sponsored Content | Content producers, interested in sponsorship | Sponsorship packages |
| Display Advertisers | General interest in ads | Display ad performance |

---

## Current Leaders (Retention) Segmentation

### Customer Lifecycle Segments

```
                    ┌─────────────────┐
                    │  NEW CUSTOMER   │
                    │  (0-90 days)    │
                    └────────┬────────┘
                             │
                    ┌────────▼────────┐
                    │   ONBOARDING    │
                    │   (Active setup)│
                    └────────┬────────┘
                             │
              ┌──────────────┼──────────────┐
              │              │              │
    ┌─────────▼─────────┐ ┌──▼───────────┐ ┌▼────────────────┐
    │   HEALTHY         │ │   AT-RISK    │ │   EXPANSION     │
    │   CUSTOMER        │ │   CUSTOMER   │ │   READY         │
    └───────────────────┘ └──────────────┘ └─────────────────┘
              │              │              │
              └──────────────┼──────────────┘
                             │
                    ┌────────▼────────┐
                    │    RENEWAL      │
                    │  (60 days out)  │
                    └────────┬────────┘
                             │
              ┌──────────────┼──────────────┐
              │              │              │
    ┌─────────▼─────────┐ ┌──▼───────────┐ ┌▼────────────────┐
    │   RENEWED         │ │   CHURNED    │ │   DOWNGRADED    │
    │                   │ │              │ │                 │
    └───────────────────┘ └──────────────┘ └─────────────────┘
```

### Customer Segment Definitions

#### 1. New Customers (Onboarding Focus)

| Segment Name | Criteria | Marketing Focus |
|--------------|----------|-----------------|
| New Customers - Week 1 | Date Entered Customer < 7 days ago | Welcome, activation |
| New Customers - Month 1 | Date Entered Customer 7-30 days ago | Feature adoption |
| New Customers - Month 2-3 | Date Entered Customer 31-90 days ago | Value realization |

#### 2. Healthy Customers

| Segment Name | Criteria | Marketing Focus |
|--------------|----------|-----------------|
| Engaged Customers | Regular platform usage AND Positive NPS (if tracked) | Advocacy, referrals |
| Growing Customers | Usage increasing month-over-month | Expansion opportunities |
| Stable Customers | Consistent usage, no issues | Maintain relationship |

#### 3. At-Risk Customers

| Segment Name | Criteria | Marketing Focus |
|--------------|----------|-----------------|
| Declining Usage | Usage decreased >20% vs. prior period | Re-engagement |
| Support Issues | Multiple support tickets, unresolved issues | Proactive outreach |
| Billing Issues | Late payments, billing disputes | Finance coordination |
| Contract End Soon | Renewal date < 90 days AND No renewal discussion | Renewal campaign |

#### 4. Expansion-Ready Customers

| Segment Name | Criteria | Marketing Focus |
|--------------|----------|-----------------|
| Usage Cap Near | Approaching plan limits | Upgrade messaging |
| Multi-Location | Customer with 3+ locations AND only 1 account | Multi-location offer |
| Feature Upsell | Using basic features, not premium | Premium feature education |
| Cross-Sell Ready | Ministry SaaS customer AND Not Ads customer | Ads introduction |

#### 5. Leader-Specific Segments

| Segment Name | Criteria | Marketing Focus |
|--------------|----------|-----------------|
| Active Leaders | Leader object EXISTS AND Last activity < 30 days | Engagement |
| High-Profile Leaders | Leader with 100K+ followers or reach | VIP treatment |
| Growing Leaders | Audience growth >10% MoM | Success stories |
| Dormant Leaders | Leader AND No activity > 60 days | Re-activation |

### Retention Risk Scoring

| Risk Factor | Weight | Indicators |
|-------------|--------|------------|
| Usage Decline | High | Platform logins decreased |
| Support Issues | High | Multiple open tickets |
| Payment Issues | High | Late or failed payments |
| Contract Timeline | Medium | <90 days to renewal |
| Engagement Drop | Medium | Email unsubscribes, no opens |
| Competitive Signals | Low | Competitor mentions, research |

---

## Segment Implementation in HubSpot

### Active List Setup

#### Master Segments (Mutual Exclusion)

**List: Ministry SaaS - All Prospects**
```
Filter Set (AND):
  - Lifecycle Stage IS ANY OF: Subscriber, Lead, MQL, SQL, Opportunity
  - Company Type IS NOT: Competitor
  - Contact Type IS NOT: Vendor
  - [Associated Company] Lifecycle Stage IS NOT: Customer

OR

Filter Set (AND):
  - Lifecycle Stage IS: Churned
  - Date Entered Churned IS MORE THAN 12 months ago
  - Last Activity Date IS LESS THAN 30 days ago
```

**List: Ads & Other - All Prospects**
```
Filter Set (OR):
  - [Associated Deal] Pipeline IS: Ads and Other
  - Company Type IS ANY OF: Media Channel, Broadcasting platform, Ads Agency
  - [Custom property] Ad Interest = True
```

**List: Current Leaders - All**
```
Filter Set (OR):
  - Lifecycle Stage IS: Customer
  - Contact Type IS: Leader
  - [Associated Leader] Record ID IS known
  - [Associated Company] Lifecycle Stage IS: Customer
```

### Segment Property Implementation

Create a calculated property to classify contacts:

**Property: Database Segment (Master)**
- Type: Single-select dropdown
- Options:
  - Ministry SaaS Prospect
  - Ads & Other Prospect
  - Current Leader (Customer)
  - Overlap (Multiple Segments)
  - Excluded

**Workflow Logic:**
```
IF Contact is in "Current Leaders - All" list:
  SET Database Segment = "Current Leader (Customer)"
ELSE IF Contact is in "Ads & Other - All Prospects" list:
  SET Database Segment = "Ads & Other Prospect"
ELSE IF Contact is in "Ministry SaaS - All Prospects" list:
  SET Database Segment = "Ministry SaaS Prospect"
ELSE:
  SET Database Segment = "Excluded"
```

### Nesting Structure

```
📁 All Contacts
├── 📁 Ministry SaaS Prospects
│   ├── 📋 By ICP Tier
│   │   ├── ICP 1 Prospects
│   │   ├── ICP 2 Prospects
│   │   ├── ICP 3 Prospects
│   │   └── IPP Prospects
│   ├── 📋 By Lifecycle Stage
│   │   ├── Subscribers (Ministry SaaS)
│   │   ├── Leads (Ministry SaaS)
│   │   ├── MQLs (Ministry SaaS)
│   │   └── SQLs/Opportunities
│   ├── 📋 By Lead Score
│   │   ├── Hot Prospects
│   │   ├── Warm Prospects
│   │   ├── Developing Prospects
│   │   └── Cold Prospects
│   └── 📋 By Engagement
│       ├── Highly Engaged
│       ├── Moderately Engaged
│       └── Dormant
├── 📁 Ads & Other Prospects
│   ├── Active Pipeline
│   ├── Past Customers
│   └── Qualified Prospects
├── 📁 Current Leaders (Customers)
│   ├── 📋 By Health
│   │   ├── Healthy Customers
│   │   ├── At-Risk Customers
│   │   └── New Customers
│   ├── 📋 By Opportunity
│   │   ├── Expansion Ready
│   │   ├── Cross-Sell Ready
│   │   └── Renewal Coming
│   └── 📋 Leaders
│       ├── Active Leaders
│       ├── High-Profile Leaders
│       └── Dormant Leaders
└── 📁 Excluded
    ├── Competitors
    ├── Vendors
    ├── Bounced/Invalid
    └── Unsubscribed
```

---

## Campaign Nurture Segments

### Ministry SaaS Nurture Campaigns

| Campaign | Target Segment | Goal | Enrollment Trigger |
|----------|---------------|------|-------------------|
| **Welcome Series** | New Subscribers | Introduce brand, educate | New contact created |
| **Lead Nurture** | Leads (not MQL) | Progress to MQL | Lead Score < 500 |
| **Accelerated Nurture** | Warm Leads (500-999) | Progress to SQL | Lead Score 500-999 |
| **Re-engagement** | Dormant (60+ days inactive) | Reactivate | No activity 60 days |
| **Event Follow-up** | Event Attendees | Convert to MQL | Attended event |
| **Content Nurture** | Downloaded content | Educate + qualify | Form submission |

### Ads & Other Nurture Campaigns

| Campaign | Target Segment | Goal | Enrollment Trigger |
|----------|---------------|------|-------------------|
| **Ads Introduction** | Ads-qualified, no deal | Create opportunity | Meets ads criteria |
| **Ads Renewal** | Past Ads customers | Renew contract | Contract ended 30+ days |
| **Ads Win-back** | Lost Ads opportunities | Re-engage | Closed Lost > 6 months |

### Customer Nurture Campaigns

| Campaign | Target Segment | Goal | Enrollment Trigger |
|----------|---------------|------|-------------------|
| **Onboarding** | New Customers | Activate, adopt | Closed Won |
| **Feature Adoption** | Customers not using feature X | Drive adoption | Usage data |
| **At-Risk Intervention** | At-Risk Customers | Prevent churn | Risk score threshold |
| **Renewal Campaign** | Renewal in 90 days | Secure renewal | Contract date - 90 days |
| **Expansion Outreach** | Expansion Ready | Upsell | Usage threshold |
| **Advocacy Program** | Healthy, Engaged | Generate referrals | NPS > 8 |

### Campaign Enrollment Rules

**Mutual Exclusion**: A contact can only be in ONE active nurture campaign at a time (priority-based).

**Priority Order:**
1. At-Risk / Churn Prevention (Customers)
2. Active Sales Cycle (SQL/Opportunity)
3. Renewal Campaigns
4. Accelerated Nurture (Warm Leads)
5. Standard Lead Nurture
6. Re-engagement
7. Welcome Series

**Suppression Lists:**
- Active deal in progress (handled by sales)
- Unsubscribed
- Hard bounced
- Competitor employees
- Recently contacted (<7 days)

---

## Active List Definitions

### Ministry SaaS Prospect Lists

#### MKT-001: Ministry SaaS - All Marketable Prospects
```
Criteria (AND):
  - Lifecycle Stage IS ANY OF: Subscriber, Lead, MQL
  - Email Status IS NOT: Bounced, Invalid
  - Unsubscribed from All Email IS: False
  - Database Segment IS: Ministry SaaS Prospect
```

#### MKT-002: Ministry SaaS - ICP 1 MQLs
```
Criteria (AND):
  - ICP Tier (from Company) IS: ICP 1
  - Lifecycle Stage IS: MQL
  - Database Segment IS: Ministry SaaS Prospect
```

#### MKT-003: Ministry SaaS - Hot Leads (Immediate)
```
Criteria (AND):
  - Lead Score IS GREATER THAN: 1000
  - Lifecycle Stage IS ANY OF: Lead, MQL
  - Database Segment IS: Ministry SaaS Prospect
  - Owner IS NOT known (unassigned)
```

#### MKT-004: Ministry SaaS - Event Follow-up
```
Criteria (AND):
  - First Conversion Event IS ANY OF: [Event Forms]
  - Conversion Date IS LESS THAN: 30 days ago
  - Lifecycle Stage IS ANY OF: Lead, MQL
  - NOT in Active Nurture Campaign
```

#### MKT-005: Ministry SaaS - Re-engagement Candidates
```
Criteria (AND):
  - Last Activity Date IS MORE THAN: 60 days ago
  - Lifecycle Stage IS ANY OF: Lead, MQL
  - Email Status IS: Valid
  - NOT in Active Nurture Campaign
```

### Ads & Other Lists

#### ADS-001: Ads - Active Pipeline Support
```
Criteria (AND):
  - [Associated Deal] Pipeline IS: Ads and Other
  - [Associated Deal] Deal Stage IS NOT ANY OF: Closed Won, Closed Lost
```

#### ADS-002: Ads - Cross-Sell from Ministry SaaS
```
Criteria (AND):
  - [Associated Company] Lifecycle Stage IS: Customer
  - Company Type IS ANY OF: Media Ministry, Podcast
  - Has NO [Associated Deal] in Pipeline: Ads and Other
```

### Customer/Leader Lists

#### CUS-001: Current Customers - All Active
```
Criteria (AND):
  - Lifecycle Stage IS: Customer
  - [Associated Company] Lifecycle Stage IS: Customer
```

#### CUS-002: Leaders - Active Platform Users
```
Criteria (AND):
  - [Associated Leader] Record ID IS known
  - Last Activity Date IS LESS THAN: 30 days ago
```

#### CUS-003: Customers - Renewal in 90 Days
```
Criteria (AND):
  - Lifecycle Stage IS: Customer
  - [Associated Deal] Close Date (renewal) IS LESS THAN: 90 days from now
  - NOT in Renewal Campaign already
```

#### CUS-004: Customers - At Risk
```
Criteria (OR):
  - [Support Tickets] Open Count IS GREATER THAN: 3
  - [Usage Property] IS LESS THAN: 50% of average
  - Payment Status IS: Delinquent
```

#### CUS-005: Customers - Expansion Ready
```
Criteria (AND):
  - Lifecycle Stage IS: Customer
  - [Usage Property] IS GREATER THAN: 80% of plan limit
  - [Associated Company] Number of Locations IS GREATER THAN: 1
  - NOT in Expansion Nurture already
```

---

## Segment Maintenance & Hygiene

### Weekly Maintenance Tasks

| Task | Owner | Process |
|------|-------|---------|
| Review unassigned hot leads | Marketing Ops | Assign or route |
| Check list growth/decline | Marketing Ops | Flag anomalies |
| Review bounce rates | Email Marketing | Clean lists |
| Check segment overlap | Data Ops | Resolve conflicts |

### Monthly Maintenance Tasks

| Task | Owner | Process |
|------|-------|---------|
| Segment size audit | Marketing Ops | Document counts |
| List hygiene review | Data Ops | Remove invalids |
| Re-engagement analysis | Demand Gen | Update dormant criteria |
| Customer health review | Customer Marketing | Update risk criteria |

### Quarterly Maintenance Tasks

| Task | Owner | Process |
|------|-------|---------|
| Full segment review | Marketing + Data Ops | Validate all criteria |
| ICP criteria review | Sales + Marketing | Update fit scoring |
| Lead score recalibration | Marketing Ops | Adjust thresholds |
| Churn analysis | Customer Success | Update risk factors |

### Data Quality Rules

| Rule | Action | Frequency |
|------|--------|-----------|
| Invalid email detected | Move to suppression | Real-time |
| Duplicate contact | Merge (keep most complete) | Weekly |
| Missing Company association | Flag for enrichment | Daily |
| Stale lifecycle stage | Review and update | Weekly |
| Incorrect ICP classification | Re-evaluate company | Monthly |

---

## Cross-Segment Rules

### Overlap Handling

When a contact qualifies for multiple master segments:

| Scenario | Resolution |
|----------|------------|
| Customer + Ministry SaaS Prospect | Classify as Customer (retention priority) |
| Customer + Ads Prospect | Allow overlap (cross-sell opportunity) |
| Ministry SaaS + Ads Prospect | Primary = Ministry SaaS, Secondary = Ads |
| Churned + New Interest | Re-evaluate lifecycle, may re-enter as prospect |

### Segment Transition Rules

| From Segment | To Segment | Trigger | Action |
|--------------|------------|---------|--------|
| Ministry SaaS Prospect | Customer | Deal Closed Won | Update lifecycle, move to Customer segment |
| Customer | Churned | Contract cancelled | Start win-back timeline |
| Churned | Ministry SaaS Prospect | Re-engaged after 12 months | Reset lifecycle to Lead |
| Ads Prospect | Ministry SaaS Prospect | Expressed interest in core product | Add to Ministry SaaS nurture |
| Ministry SaaS Prospect | Excluded | Unsubscribed/Bounced | Remove from marketing |

### Marketing Communication Rules

| Segment | Email Frequency Cap | SMS Allowed | Phone Allowed |
|---------|--------------------:|:-----------:|:-------------:|
| Ministry SaaS - Hot | 3/week | Yes | Yes |
| Ministry SaaS - Warm | 2/week | Yes | Yes |
| Ministry SaaS - Cold | 1/week | No | No |
| Ads Prospects | 1/week | No | Yes |
| Customers - Active | 2/week | Yes | Yes |
| Customers - At Risk | 3/week | Yes | Yes |
| Dormant/Disengaged | 1/2 weeks | No | No |

---

## Appendix: Segment Quick Reference

### Segment ID Reference Table

| Segment ID | Segment Name | Primary Property | Value |
|------------|--------------|------------------|-------|
| MSAAS-ALL | Ministry SaaS All Prospects | Database Segment | Ministry SaaS Prospect |
| MSAAS-ICP1 | Ministry SaaS ICP 1 | ICP Tier | ICP 1 |
| MSAAS-ICP2 | Ministry SaaS ICP 2 | ICP Tier | ICP 2 |
| MSAAS-ICP3 | Ministry SaaS ICP 3 | ICP Tier | ICP 3 |
| MSAAS-IPP | Ministry SaaS IPP | ICP Tier | IPP |
| MSAAS-HOT | Ministry SaaS Hot Leads | Lead Score | >= 1000 |
| MSAAS-WARM | Ministry SaaS Warm Leads | Lead Score | 500-999 |
| ADS-ALL | Ads All Prospects | Database Segment | Ads & Other Prospect |
| ADS-PIPE | Ads Active Pipeline | Deal Pipeline | Ads and Other |
| CUS-ALL | All Customers | Lifecycle Stage | Customer |
| CUS-LEAD | Customer Leaders | Contact Type | Leader |
| CUS-RISK | At-Risk Customers | Risk Score | High |
| CUS-EXP | Expansion Ready | Expansion Flag | True |
| EXC-ALL | Excluded Contacts | Database Segment | Excluded |

### Property Dependencies

| Segment Dimension | Required Properties | Source |
|-------------------|--------------------| -------|
| ICP Tier | icp_tier, company_type, annualrevenue | Company |
| Company Segment | company_segment, annualrevenue | Company |
| Lifecycle Stage | lifecyclestage | Contact/Company |
| Lead Score | lead_score, hs_lead_score | Contact |
| Deal Pipeline | pipeline, dealstage | Deal |
| Customer Status | closedate, hs_v2_date_entered_customer | Contact/Company |
| Leader Status | associated_leader_name, contact_type | Contact/Leader |

---

*Segmentation Strategy maintained by Marketing Operations and Data Operations. For segment changes, submit a request through Marketing Ops with business justification.*
