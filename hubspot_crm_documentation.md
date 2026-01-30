# Ministry SaaS HubSpot CRM Documentation

## B2B SaaS CRM Implementation Guide

**Version:** 2.0
**Last Updated:** January 30, 2026
**Owner:** Growth Operations

---

## Table of Contents

1. [Executive Summary](#executive-summary)
2. [CRM Architecture Overview](#crm-architecture-overview)
3. [Object Data Model](#object-data-model)
4. [Ideal Customer Profile (ICP)](#ideal-customer-profile-icp)
5. [Lifecycle Stages & Pipeline Management](#lifecycle-stages--pipeline-management)
6. [Lead Scoring Framework](#lead-scoring-framework)
7. [Contact Management](#contact-management)
8. [Company Management](#company-management)
9. [Deal Management](#deal-management)
10. [Lead Object Management](#lead-object-management)
11. [Attribution & Source Tracking](#attribution--source-tracking)
12. [Workflows & Automation](#workflows--automation)
13. [Segmentation Strategy](#segmentation-strategy)
14. [Reporting & Analytics](#reporting--analytics)
15. [Data Governance](#data-governance)
16. [Integration Guidelines](#integration-guidelines)
17. [Glossary](#glossary)

---

## Executive Summary

This document provides comprehensive documentation for the Ministry SaaS HubSpot CRM implementation. Our CRM is designed to support a B2B SaaS go-to-market strategy targeting religious organizations, churches, parachurches, media ministries, and faith-based content creators.

### Key CRM Capabilities

- **18 Object Types**: Contact, Company, Deal, Lead, Call, Meeting, Campaign, and more
- **2,500+ Custom Properties**: Tailored fields across all objects
- **Multi-Touch Attribution**: First-touch and linear attribution tracking
- **Advanced Lead Scoring**: -2,000 to +2,000 point scoring model
- **Automated Workflows**: 47+ active automation flows
- **Revenue Segmentation**: 5-tier company classification (Whale to Mouse)

### Target Market Overview

| Segment | Description | Revenue Range |
|---------|-------------|---------------|
| Primary ICP | Churches, Parachurches, Media Ministries | $5M - $25M |
| Secondary ICP | Podcasters, Nonprofits, Agencies | $1M - $5M |
| Strategic Partners | Networks, Platforms, Multipliers | Variable |

---

## CRM Architecture Overview

### System Architecture

```
                    +------------------+
                    |    HubSpot CRM   |
                    +--------+---------+
                             |
        +--------------------+--------------------+
        |                    |                    |
+-------v-------+   +--------v--------+   +------v------+
|   Marketing   |   |      Sales      |   |   Service   |
|     Hub       |   |       Hub       |   |     Hub     |
+---------------+   +-----------------+   +-------------+
        |                    |                    |
        +--------------------+--------------------+
                             |
                    +--------v---------+
                    |  Data Objects    |
                    +------------------+
                    | - Contacts       |
                    | - Companies      |
                    | - Deals          |
                    | - Leads          |
                    | - Leaders        |
                    | - Activities     |
                    +------------------+
```

### Object Relationships

```
                        +-------------+
                        |   Leader    |
                        | (Custom Obj)|
                        +------+------+
                               |
                               v
+-------------+         +------+------+         +-------------+
|   Contact   +-------->|   Company   |<--------+    Deal     |
+------+------+         +------+------+         +------+------+
       |                       |                       |
       |                       |                       |
       v                       v                       v
+------+------+         +------+------+         +------+------+
|    Lead     |         |  Campaign   |         | Line Items  |
+-------------+         +-------------+         +-------------+
```

### HubSpot Objects Inventory

| Object | Properties | Purpose |
|--------|------------|---------|
| Contact | 412 | Individual person records |
| Company | 296 | Organization records |
| Deal | 597 | Sales opportunities |
| Lead | 187 | Prospecting pipeline |
| Leader | 212 | Key decision-maker tracking |
| Call | 41 | Phone activity logging |
| Meeting | 45 | Meeting tracking |
| Campaign | 61 | Marketing campaign management |
| Marketing Email | 70 | Email performance |
| Marketing Event | 46 | Event management |
| Workflow | 47 | Automation tracking |
| Project | 92 | Customer onboarding |
| Invoice | 79 | Billing records |
| Quote | 73 | Proposal management |
| Product | 39 | Product catalog |
| Line Item | 71 | Deal product associations |

---

## Object Data Model

### Core Objects Diagram

```
+------------------+     1:N     +------------------+
|     COMPANY      |------------>|     CONTACT      |
|------------------|             |------------------|
| company_type     |             | job_title        |
| company_segment  |             | contact_type     |
| icp_tier         |             | lead_score       |
| lifecycle_stage  |             | lifecycle_stage  |
| website          |             | email            |
+------------------+             +------------------+
        |                                |
        | 1:N                            | 1:1
        v                                v
+------------------+             +------------------+
|      DEAL        |             |      LEAD        |
|------------------|             |------------------|
| deal_stage       |             | lead_stage       |
| amount           |             | disqualification |
| close_date       |             | lead_label       |
| pipeline         |             | lead_source      |
+------------------+             +------------------+
        |
        | N:N
        v
+------------------+
|     LEADER       |
|------------------|
| leader_name      |
| leader_website   |
| leader_type      |
+------------------+
```

### Object Property Groups

#### Contact Property Groups
- **Core Info**: Name, email, phone, address
- **Company Properties**: Associated company data synced to contact
- **Analytics Information**: Traffic source, page views, sessions
- **Lifecycle Stages**: Pipeline stage tracking and timing
- **Lead Scoring**: Fit and engagement scores
- **Conversion Information**: IP-based location data
- **Ads & Other Information**: Advertising engagement data

#### Company Property Groups
- **Core Info**: Name, website, domain, address
- **Source & Attribution**: Traffic and marketing attribution
- **Deal Information**: Revenue and deal data
- **Company Signals**: Intent tracking
- **Lifecycle Stages**: Company pipeline progression
- **Firmographics**: Company characteristics

#### Deal Property Groups
- **Revenue Information**: Amount, ACV, TCV
- **Qualification**: Stage, probability, forecast
- **Analytics Information**: Attribution and source tracking
- **Associations**: Related records
- **Pipeline-Specific**: Stage timing and progression

---

## Ideal Customer Profile (ICP)

### ICP Tier Definitions

| Tier | Description | Characteristics |
|------|-------------|-----------------|
| **ICP 1** | Mega-church / Church Media Ministries / Parachurch | 1,100+ attendance, $5M+ revenue, multi-campus |
| **ICP 2** | Media Ministries & Faith-based Shows | Active content production, 25K+ monthly reach |
| **ICP 3** | Growth-Stage, Digital-Forward Churches | 400-1,099 attendance, expanding digital presence |
| **IPP** | Agency/Network Multipliers | Partner organizations serving multiple clients |

### Company Type Classification

**High-Value Targets (+10 points each)**
- Church (Mega Church)
- Parachurch organization
- Media Ministry

**Medium-Value Targets (+5 points each)**
- Podcast (Podcaster)
- Nonprofit
- Agency

**Disqualified (-5 points each)**
- Competitor
- Media Channel
- Broadcasting platform
- Social Network
- Ads Agency

### Company Segmentation (Revenue-Based)

| Segment | Internal Name | Revenue Range | Deal Priority |
|---------|---------------|---------------|---------------|
| Whale | #1 Whale | Over $5 million | Highest |
| Elephant | #2 Elephant | $3M - $5M | High |
| Deer | #3 Deer | $1M - $3M | Medium-High |
| Rabbit | #4 Rabbit | $500K - $1M | Medium |
| Mouse | #5 Mouse | Under $500K | Lower |

---

## Lifecycle Stages & Pipeline Management

### Lifecycle Stage Pipeline

```
+------------+    +--------+    +--------+    +--------+    +-------------+    +----------+    +---------+
| Subscriber |--->|  Lead  |--->|  MQL   |--->|  SQL   |--->| Opportunity |--->| Customer |--->| Churned |
+------------+    +--------+    +--------+    +--------+    +-------------+    +----------+    +---------+
```

| Stage | Description | Exit Criteria |
|-------|-------------|---------------|
| **Subscriber** | Initial opt-in, newsletter signup | Demonstrates engagement beyond subscription |
| **Lead** | Basic qualification met | Meets MQL threshold score |
| **MQL** (Marketing Qualified Lead) | Marketing-qualified based on fit + engagement | Accepts sales outreach |
| **SQL** (Sales Qualified Lead) | Sales-qualified with budget/authority | Enters active sales cycle |
| **Opportunity** | Active sales negotiation | Deal closes won or lost |
| **Customer** | Closed-won, active customer | Contract ends or churns |
| **Churned** | Former customer, contract ended | Re-engagement or archival |

### Deal Pipelines

#### 1. Main Sales Pipeline (Pray Channel)

| Stage | Probability | Description |
|-------|-------------|-------------|
| Qualifying & Discovery | 10% | Initial qualification and needs assessment |
| Pitch | 25% | Product demonstration and value presentation |
| Proposal | 50% | Formal proposal submitted |
| Contract Sent | 75% | Agreement sent for signature |
| Closed Won | 100% | Deal successfully closed |
| Closed Lost | 0% | Deal not won |

#### 2. Ads and Other Pipeline

| Stage | Probability | Description |
|-------|-------------|-------------|
| Qualifying & Discovery | 10% | Initial assessment |
| Pitch | 25% | Presenting advertising solutions |
| Proposal | 50% | Media proposal submitted |
| Contract Sent | 75% | IO/Agreement sent |
| Closed Won | 100% | Campaign booked |
| Closed Lost | 0% | Opportunity lost |

### Lead Pipeline (BDR/SDR)

| Stage | Category | Description |
|-------|----------|-------------|
| New | Not Started | Freshly created lead |
| Attempting | In Progress | Active outreach attempts |
| Connected | In Progress | Successful contact made |
| Qualified | Qualified | Meets qualification criteria |
| Disqualified | Unqualified | Does not meet criteria |

---

## Lead Scoring Framework

> **Reference Document**: See `lead_scoring_documentation.md` for complete scoring details.

### Score Range Overview

**Total Score Range**: -2,000 to +2,000 points

| Score Band | Classification | Action |
|------------|----------------|--------|
| 1,000 - 2,000 | Hot Lead | Immediate AE assignment |
| 500 - 999 | Warm Lead | Outreach within 24-48 hours |
| 100 - 499 | Developing Lead | Nurture campaign enrollment |
| 0 - 99 | Cold Lead | Long-term nurture |
| -2,000 to -1 | Disqualified | Remove from active campaigns |

### Scoring Categories

#### 1. Firmographics (Fit Score)
- Company Type: -5 to +10 points
- Estimated Revenue: -5 to +10 points
- Employee Range: -5 to +10 points
- Number of Locations: +10 points (5+ locations)
- Church Attendance: -10 to +10 points
- Domain Quality: -50 to +5 points

#### 2. Contact Information Quality
- Job Title/Role: +3 to +10 points
- Contact Verification: +5 points per verified field

#### 3. Growth Signals
- Distribution Channels: -10 to +10 points
- Social Media Presence: +10 points (400K+ followers)
- Podcast Presence: +10 points
- Content Production Volume: -10 to +10 points
- Content Reach: -10 to +10 points
- Technology Adoption: +5 to +10 points
- Ad Spend: +5 to +10 points

#### 4. Buying Intent Signals (Engagement Score)
- Form Submissions: +5 to +10 points
- Email Engagement: -5 to +10 points
- Call Activity: +10 points
- Meeting Activity: +5 to +50 points
- Event Attendance: +50 points
- SMS/Social Engagement: +5 to +10 points
- Sales Email Activity: +5 to +15 points

#### 5. Sales Qualification Signals
- Growth Priority: +5 to +20 points
- Timeline for Solution: -25 to +50 points
- Annual Operating Budget: -10 to +20 points
- Decision Urgency: +10 to +50 points
- Decision-Maker Involvement: -50 to +50 points
- Product-Market Fit: -50 to +50 points
- Purchase Intent Level: -50 to +50 points

---

## Contact Management

### Key Contact Properties

#### Identification Properties
| Property | Internal Name | Type | Description |
|----------|---------------|------|-------------|
| Email | `email` | String | Primary email address |
| First Name | `firstname` | String | Contact first name |
| Last Name | `lastname` | String | Contact last name |
| Phone Number | `phone` | String | Primary phone |
| Mobile Phone | `mobilephone` | String | Mobile number |

#### Role & Title Properties
| Property | Internal Name | Options |
|----------|---------------|---------|
| Job Title (Dropdown) | `job_title____` | Senior Pastor/Lead Pastor, Executive Leadership, Communications/Media Director, Content Creator/Host/Speaker, Operations/Admin Leadership, Other Ministry Staff, Other - Government |
| Contact Type | `contact_type` | Leader, Investor, Partner, Vendor, Supporter, Organization, Press, Evangelist |

#### Company Sync Properties
| Property | Internal Name | Description |
|----------|---------------|-------------|
| Company Segment | `company_segment` | Whale, Elephant, Deer, Rabbit, Mouse, Unknown |
| Company Type | `company_type__from_associated_company_` | Synced from associated company |
| ICP Tier | `icp_tier__from_associated_company_` | ICP 1, ICP 2, ICP 3, IPP |
| Lead Pipeline Stage | `lead_pipeline_stage` | Synced from lead object |

#### Analytics Properties
| Property | Internal Name | Description |
|----------|---------------|-------------|
| Original Source | `hs_analytics_source` | First traffic source |
| Latest Source | `hs_analytics_latest_source` | Most recent traffic source |
| First Conversion | `hs_analytics_first_url` | First page viewed |
| Time First Seen | `hs_analytics_first_timestamp` | First website visit |

---

## Company Management

### Key Company Properties

#### Core Identification
| Property | Internal Name | Type | Description |
|----------|---------------|------|-------------|
| Company Name | `name` | String | Organization name |
| Website URL | `website` | String | Primary website (unique identifier) |
| Company Domain | `domain` | String | Domain for deduplication |
| Phone Number | `phone` | String | Company phone |

#### Classification Properties
| Property | Internal Name | Options |
|----------|---------------|---------|
| Company Type | `company_type` | Church, Parachurch, Media Ministry, Podcast, Nonprofit, Agency, Competitor, Media Channel, Broadcasting platform, Social Network, Ads Agency, Other |
| ICP Tier | `icp_tier` | ICP 1, ICP 2, ICP 3, IPP |
| Company Segment | `company_segment` | Whale, Elephant, Deer, Rabbit, Mouse |

#### Ministry-Specific Properties
| Property | Internal Name | Description |
|----------|---------------|-------------|
| Church Size (Attendance) | `church_size_attendance` | Congregation size |
| Number of Locations | `number_of_locations` | Multi-campus count |
| Distribution Channels | `distribution_channels` | Content distribution methods |
| Content Production Volume | `content_production_volume` | Production frequency |
| Monthly Listeners/Viewers | `monthly_listeners_viewers` | Audience reach |
| Primary Challenge | `primary_challenge` | Key pain point |
| Growth Priorities | `growth_priorities` | Strategic priorities |

#### Revenue & Firmographic Properties
| Property | Internal Name | Description |
|----------|---------------|-------------|
| Annual Revenue | `annualrevenue` | Estimated annual revenue |
| Revenue Range | `hs_revenue_range` | Revenue bracket |
| Number of Employees | `numberofemployees` | Employee count |
| Industry | `industry` | Business sector |

---

## Deal Management

### Key Deal Properties

#### Revenue Properties
| Property | Internal Name | Type | Description |
|----------|---------------|------|-------------|
| Amount | `amount` | Number | Total deal value |
| ACV | `hs_acv` | Number | Annual contract value |
| TCV | `hs_tcv` | Number | Total contract value |
| Exchange Rate | `hs_exchange_rate` | Number | Currency conversion |

#### Qualification Properties
| Property | Internal Name | Description |
|----------|---------------|-------------|
| Deal Stage | `dealstage` | Current pipeline stage |
| Deal Probability | `hs_deal_stage_probability` | Close probability |
| Forecast Amount | `hs_forecast_amount` | Weighted revenue forecast |
| Forecast Category | `hs_manual_forecast_category` | Pipeline, Best Case, Commit |
| Days to Close | `days_to_close` | Sales cycle length |

#### Closed Won/Lost Properties
| Property | Internal Name | Options |
|----------|---------------|---------|
| Closed Won Reason | `closed_won_reason__dropdown_` | Actionable Insights, Competitive Pricing, Content Preservation, Digital Legacy, FOMO, Global Reach, Limitless Accessibility, Local Focus, Ongoing Account Management, Standard of Excellence, Donors |
| Closed Lost Reason | `closed_lost_reason__dropdown_` | Not Qualified, Went Dark, Timing, Budget, Feature Gap, Lost to Competitor, Cancelled Evaluation, BDR - No Show, Other, No Local Focus |

#### Association Properties
| Property | Internal Name | Description |
|----------|---------------|-------------|
| Associated Agency | `associated_agency_company_name` | Agency partner |
| Associated Leader | `associated_leader_name` | Key influencer/decision-maker |
| Billing Contact | `associated_billing_contact_email` | Billing contact email |
| Key Manager | `associated_key_manager_email` | Champion contact |

---

## Lead Object Management

### Lead Object Overview

The Lead object in HubSpot serves as a prospecting pipeline for BDRs/SDRs to qualify contacts before creating deals.

### Key Lead Properties

| Property | Internal Name | Description |
|----------|---------------|-------------|
| Lead Name | `hs_lead_name` | Full name of the lead |
| Lead Label | `hs_lead_label` | Hot, Warm, Cold |
| Lead Source | `hs_lead_source` | Origin traffic source |
| Disqualification Reason | `hs_lead_disqualification_reason` | Why lead was disqualified |
| Call Count | `hs_lead_call_count` | Outreach calls made |
| Email Count | `hs_lead_email_count` | Outreach emails sent |
| Meeting Count | `hs_lead_meeting_count` | Meetings booked |
| First Outreach Date | `hs_lead_first_outreach_date` | Initial outreach timestamp |
| Associated Deals | `hs_lead_associated_deals_count` | Number of related deals |

### Lead Disqualification Reasons

| Reason | Description |
|--------|-------------|
| Bad Timing | Not ready to buy now |
| Budget Constraints | Cannot afford solution |
| No Decision-making Power | Not authorized to purchase |
| Competitor Preference | Chose competitor |
| Not a Good Fit | Product doesn't meet needs |
| No Commercial Interest | Not interested |
| Prior Negative Experience | Past issues with company |
| Technical Limitations | Feature gaps |
| Wrong Data | Incorrect contact information |
| No Response | Unable to reach |
| Smaller than Deer | Revenue below threshold |

---

## Attribution & Source Tracking

### Attribution Models

#### First-Touch Attribution
Captures the initial touchpoint that brought a contact into the system.

| Property | Object | Description |
|----------|--------|-------------|
| Original Source | Contact/Company/Deal | First traffic source type |
| Original Source Data 1 | Contact/Company/Deal | First source detail |
| Original Source Data 2 | Contact/Company/Deal | Additional first source detail |
| First Touch Converting Campaign | Contact/Company | First marketing campaign |

#### Linear-Touch Attribution
Tracks all touchpoints throughout the customer journey.

| Property | Object | Description |
|----------|--------|-------------|
| Marketing Attribution | Company/Deal | Initial conversion type |
| Linear Touch Marketing Attribution | Deal | Ongoing engagement tracking |
| Channel Attribution | Deal | Marketing vs. Sales channel |

### Attribution Categories

| Category | Description | Examples |
|----------|-------------|----------|
| Digital Outreach | Online organic engagement | Website forms, organic search |
| Live Events | In-person event attendance | NRB, C3, Exponential, Retreats |
| Outbound | Direct sales outreach | Cold calls, LinkedIn outreach |
| Paid Advertising | Paid media channels | Meta, LinkedIn, Search ads |
| Website Organic | Organic website traffic | SEO, direct traffic, referrals |

### Marketing Event Tracking

**Tracked Events Include:**
- NRB (National Religious Broadcasters)
- C3 Conference
- Exponential
- Dunham Summit
- Spire
- Pastor Retreats (quarterly)
- Golf Events
- Partner conferences

---

## Workflows & Automation

### Workflow Categories

| Category | Purpose | Examples |
|----------|---------|----------|
| MKT - SEO | Search engine optimization | Content optimization triggers |
| MKT - Social Media | Social engagement | Social interaction responses |
| MKT - Events | Event management | Event registration, follow-up |
| MKT - BOFU Forms | Bottom-funnel forms | Demo request handling |
| MKT - Lead Outreach | Marketing lead nurture | Email sequences |
| SALES - First Contract | Initial sale process | Deal stage automation |
| LS - Onboarding | Customer onboarding | Project creation, task assignment |
| LS - Retention | Customer retention | Health score monitoring |
| LS - Renewal | Contract renewal | Renewal reminders |
| DATA OPS - Hygiene | Data quality | Duplicate management, validation |
| DATA OPS - Sync | Property synchronization | Cross-object data sync |

### Key Automation Patterns

#### Lead Scoring Automation
```
Trigger: Contact property change
Action: Recalculate lead score
Output: Update lead label (Hot/Warm/Cold)
```

#### Lifecycle Stage Progression
```
Trigger: Score threshold reached
Action: Update lifecycle stage
Output: Notify assigned owner
```

#### Deal Stage Notifications
```
Trigger: Deal moves to Contract Sent
Action: Validate required associations
Output: Alert if missing Billing Contact or Key Manager
```

#### Attribution Sync
```
Trigger: Deal created
Action: Copy contact/company attribution to deal
Output: Populate marketing attribution fields
```

### Workflow Monitoring Properties

| Property | Description |
|----------|-------------|
| On/Off Status | Whether workflow is active |
| Enrolled Last 7 Days | Recent enrollment count |
| Total Enrolled | Lifetime enrollment count |
| Currently Enrolled | Records currently in workflow |
| Current Issue Count | Active errors/issues |
| Last Action Execution | Most recent action timestamp |

---

## Segmentation Strategy

### Contact Segmentation

#### By Job Role
- **Senior Leadership**: Senior Pastor, Executive Leadership, C-Suite
- **Communications**: Communications/Media Director
- **Content**: Content Creator, Host, Speaker
- **Operations**: Operations/Admin Leadership
- **Other**: Ministry Staff, Government

#### By Engagement Level
- **Highly Engaged**: Multiple form submissions, meeting booked, event attended
- **Engaged**: Email opens, clicks, website visits
- **Passive**: Subscriber, minimal engagement
- **Disengaged**: No activity in 90+ days

### Company Segmentation

#### By Revenue (Company Segment)
| Segment | Criteria | Approach |
|---------|----------|----------|
| Whale | >$5M revenue | White-glove, executive engagement |
| Elephant | $3M-$5M | High-touch sales |
| Deer | $1M-$3M | Standard sales process |
| Rabbit | $500K-$1M | Efficient qualification |
| Mouse | <$500K | Product-led or nurture |

#### By ICP Tier
| Tier | Characteristics | Priority |
|------|-----------------|----------|
| ICP 1 | Mega-church, multi-campus, established media | Highest |
| ICP 2 | Media ministries, active content production | High |
| ICP 3 | Growth-stage, digital-forward | Medium |
| IPP | Agencies, networks, multipliers | Partnership |

### Deal Segmentation

#### By Source
- **Marketing-Sourced**: Digital outreach, events, paid advertising
- **Sales-Sourced**: Outbound prospecting, referrals

#### By Pipeline
- **Pray Channel**: Main product sales
- **Ads and Other**: Advertising and ancillary revenue

---

## Reporting & Analytics

### Key Performance Metrics

#### Marketing Metrics
| Metric | Description | Target |
|--------|-------------|--------|
| Lead Volume | New leads created | Growth trending |
| MQL Rate | Leads to MQL conversion | >25% |
| Lead Score Distribution | Hot/Warm/Cold breakdown | >20% Hot |
| Attribution Mix | Channel contribution | Balanced portfolio |

#### Sales Metrics
| Metric | Description | Target |
|--------|-------------|--------|
| SQL Conversion | MQL to SQL rate | >40% |
| Win Rate | Deals won / total closed | >30% |
| Sales Cycle | Average days to close | <90 days |
| Average Deal Size | Mean closed-won amount | Segment-specific |
| Pipeline Coverage | Pipeline / quota | >3x |

#### Customer Metrics
| Metric | Description | Target |
|--------|-------------|--------|
| Customer Count | Active customers | Growth trending |
| TCV | Total contract value | Increasing |
| Churn Rate | Customers lost | <10% annually |
| Expansion Revenue | Upsell/cross-sell | >20% of new revenue |

### Dashboard Recommendations

#### Executive Dashboard
- Total pipeline value
- Won vs. lost deals (monthly)
- Revenue by segment
- Attribution breakdown
- Forecast vs. actual

#### Sales Manager Dashboard
- Team pipeline by stage
- Individual rep performance
- Deal aging analysis
- Activity metrics (calls, emails, meetings)
- Win/loss analysis

#### Marketing Dashboard
- Lead source performance
- Campaign ROI
- Event attendance and conversion
- Content engagement
- Website analytics

#### BDR/SDR Dashboard
- Lead assignment queue
- Outreach activity
- Meeting booking rate
- Lead-to-opportunity conversion
- Lead scoring distribution

---

## Data Governance

### Data Quality Standards

#### Required Fields by Object

**Contacts (Required)**
- Email address
- First name
- Last name
- Company association

**Companies (Required)**
- Company name
- Website/domain
- Company type
- Owner assignment

**Deals (Required)**
- Deal name
- Amount
- Close date
- Pipeline and stage
- Company association
- Contact association

#### Data Validation Rules

| Rule | Object | Validation |
|------|--------|------------|
| Valid Domain | Company | Website must be valid URL |
| Email Format | Contact | Email must match email pattern |
| Required Associations | Deal | Must have company and contact |
| Amount Required | Deal | Amount must be >0 |

### Data Hygiene Practices

#### Duplicate Management
- Company: Deduplicate by domain
- Contact: Deduplicate by email
- Weekly duplicate review process

#### Data Enrichment
- HubSpot Insights for company data
- Third-party enrichment for contacts
- Manual data mining validation

#### Archival Policies
- Inactive contacts: Review after 24 months
- Lost deals: Archive after 12 months
- Churned customers: Maintain for re-engagement

### GDPR & Privacy Compliance

#### Consent Management
- Email subscription status tracking
- Marketing opt-in/opt-out
- Communication preferences

#### Data Subject Rights
- Right to access (data export)
- Right to erasure (GDPR delete)
- Right to rectification (data correction)

---

## Integration Guidelines

### Native Integrations

| Integration | Purpose | Data Flow |
|-------------|---------|-----------|
| Gmail/Outlook | Email tracking | Bidirectional |
| LinkedIn Sales Navigator | Social selling | Import |
| Zoom | Meeting sync | Bidirectional |
| Slack | Notifications | Export |
| Stripe | Payment data | Import |

### API Integration Standards

#### Authentication
- Use OAuth 2.0 for secure access
- Rotate API keys quarterly
- Limit scope to required permissions

#### Rate Limits
- Respect HubSpot API rate limits
- Implement exponential backoff
- Use bulk APIs for large operations

#### Data Sync Best Practices
- Use webhooks for real-time sync
- Implement idempotency
- Log all sync operations
- Handle errors gracefully

---

## Glossary

| Term | Definition |
|------|------------|
| **ACV** | Annual Contract Value - yearly value of a subscription deal |
| **AE** | Account Executive - sales representative who closes deals |
| **BDR/SDR** | Business/Sales Development Representative - prospecting role |
| **BOFU** | Bottom of Funnel - late-stage buying intent |
| **Churned** | Customer who has cancelled or not renewed |
| **ICP** | Ideal Customer Profile - characteristics of best-fit customers |
| **Lead Score** | Numeric value representing lead quality and engagement |
| **Lifecycle Stage** | Current status in the buyer journey |
| **MQL** | Marketing Qualified Lead - meets marketing criteria |
| **Opportunity** | Active sales deal in negotiation |
| **SQL** | Sales Qualified Lead - meets sales criteria |
| **TCV** | Total Contract Value - full value of a multi-year deal |
| **TOFU** | Top of Funnel - early-stage awareness |
| **Whale** | Largest revenue segment (>$5M) |

---

## Appendix

### Related Documentation

| Document | Description | Location |
|----------|-------------|----------|
| Lead Scoring Framework | Complete scoring model | `lead_scoring_documentation.md` |
| Lead Scoring AE Summary | Quick reference for sales | `lead_scoring_ae_summary.md` |
| Contact Properties Export | Full contact property list | `contact.csv` |
| Company Properties Export | Full company property list | `company.csv` |
| Deal Properties Export | Full deal property list | `deal.csv` |
| Lead Properties Export | Full lead property list | `lead.csv` |
| Workflow Export | Active workflow list | `workflow.csv` |

### Version History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | Jan 29, 2026 | Growth Ops | Initial documentation |
| 2.0 | Jan 30, 2026 | Growth Ops | Comprehensive B2B SaaS guide |

---

*This documentation is maintained by the Growth Operations team. For questions or updates, contact the CRM administrator.*
