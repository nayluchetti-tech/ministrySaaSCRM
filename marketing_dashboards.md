# Marketing Mix Dashboards & Reporting

## HubSpot Dashboard Framework for Ministry SaaS

**Version:** 1.0
**Last Updated:** January 30, 2026
**Owner:** Marketing Operations

---

## Table of Contents

1. [Dashboard Strategy Overview](#dashboard-strategy-overview)
2. [Executive Marketing Dashboard](#executive-marketing-dashboard)
3. [Marketing Mix Performance Dashboard](#marketing-mix-performance-dashboard)
4. [Channel Attribution Dashboard](#channel-attribution-dashboard)
5. [Campaign Performance Dashboard](#campaign-performance-dashboard)
6. [Event Marketing Dashboard](#event-marketing-dashboard)
7. [Digital Marketing Dashboard](#digital-marketing-dashboard)
8. [Content & Engagement Dashboard](#content--engagement-dashboard)
9. [Lead Generation Dashboard](#lead-generation-dashboard)
10. [Customer Lifecycle Dashboard](#customer-lifecycle-dashboard)
11. [Report Specifications](#report-specifications)
12. [Implementation Guide](#implementation-guide)

---

## Dashboard Strategy Overview

### Dashboard Architecture

```
                              ┌──────────────────────────────┐
                              │   EXECUTIVE MARKETING        │
                              │   DASHBOARD                  │
                              │   (C-Suite View)             │
                              └───────────────┬──────────────┘
                                              │
                  ┌───────────────────────────┼───────────────────────────┐
                  │                           │                           │
    ┌─────────────▼─────────────┐ ┌──────────▼──────────┐ ┌──────────────▼─────────────┐
    │   MARKETING MIX           │ │  CHANNEL            │ │   CAMPAIGN                 │
    │   PERFORMANCE             │ │  ATTRIBUTION        │ │   PERFORMANCE              │
    │   (Marketing Leadership)  │ │  (Analytics)        │ │   (Campaign Managers)      │
    └─────────────┬─────────────┘ └──────────┬──────────┘ └──────────────┬─────────────┘
                  │                           │                           │
    ┌─────────────┼─────────────┬─────────────┼─────────────┬─────────────┤
    │             │             │             │             │             │
┌───▼───┐   ┌─────▼─────┐  ┌────▼────┐  ┌────▼────┐  ┌─────▼─────┐  ┌────▼────┐
│ EVENT │   │  DIGITAL  │  │ CONTENT │  │  LEAD   │  │ CUSTOMER  │  │ SEGMENT │
│ MKTG  │   │  MKTG     │  │ & ENGMT │  │  GEN    │  │ LIFECYCLE │  │ ANALYSIS│
└───────┘   └───────────┘  └─────────┘  └─────────┘  └───────────┘  └─────────┘
```

### Dashboard Access by Role

| Role | Primary Dashboards | Refresh Frequency |
|------|-------------------|-------------------|
| CMO/VP Marketing | Executive Marketing, Marketing Mix | Daily |
| Marketing Director | Marketing Mix, Channel Attribution, Campaign | Daily |
| Campaign Manager | Campaign Performance, Event Marketing | Real-time |
| Digital Marketing | Digital Marketing, Content & Engagement | Real-time |
| Marketing Ops | All Dashboards, Lead Generation | Daily |
| Demand Gen | Lead Generation, Channel Attribution | Real-time |
| Customer Marketing | Customer Lifecycle | Weekly |

---

## Executive Marketing Dashboard

### Purpose
High-level view of marketing performance, pipeline contribution, and ROI for executive leadership.

### Key Metrics (KPIs)

| Metric | Calculation | Target | Visualization |
|--------|-------------|--------|---------------|
| Marketing-Sourced Pipeline | Sum of Deal Amount WHERE Channel Attribution = "Marketing" | Growth trending | Number + trend |
| Marketing-Influenced Pipeline | Sum of Deal Amount WHERE Linear Touch Marketing Attribution IS NOT NULL | Growth trending | Number + trend |
| MQL Volume | Count of Contacts WHERE Lifecycle Stage = "MQL" (This Period) | Per quota | Number + trend |
| MQL → SQL Conversion Rate | (SQL Count / MQL Count) × 100 | >40% | Percentage gauge |
| Marketing-Sourced Win Rate | Closed Won Marketing / Total Closed Marketing × 100 | >30% | Percentage |
| CAC (Customer Acquisition Cost) | Marketing Spend / New Customers | Decreasing | Currency |
| Pipeline Coverage Ratio | Marketing Pipeline / Revenue Target | >3x | Ratio |

### Report Specifications

#### 1. Marketing Pipeline Value (Monthly)
```
Object: Deal
Filter:
  - Channel Attribution = "Marketing"
  - Deal Stage NOT IN ("Closed Won", "Closed Lost")
  - Close Date = This Quarter
Measure: Sum of Amount
Breakdown: By Month (Create Date)
Visualization: Bar chart with trend line
```

#### 2. Marketing vs. Sales Sourced Pipeline
```
Object: Deal
Filter:
  - Deal Stage NOT IN ("Closed Won", "Closed Lost")
Measure: Sum of Amount
Breakdown: Channel Attribution (Marketing, Sales, No Data)
Visualization: Stacked bar chart by month
```

#### 3. Funnel Progression
```
Object: Contact
Measure: Count
Breakdown: Lifecycle Stage
Filter: Date entered [Stage] = This Month
Visualization: Funnel chart
```

#### 4. Revenue Attribution
```
Object: Deal
Filter:
  - Deal Stage = "Closed Won"
  - Close Date = This Quarter
Measure: Sum of Amount
Breakdown: First Touch Marketing Attribution
Visualization: Pie chart
```

---

## Marketing Mix Performance Dashboard

### Purpose
Analyze performance across all marketing channels and initiatives to optimize budget allocation.

### Marketing Mix Categories

| Category | Attribution Values | Budget Allocation |
|----------|-------------------|-------------------|
| Live Events | Event Attendance, Conference | 35% |
| Digital Outreach | Organic BOFU Form | 25% |
| Paid Advertising | Paid - Meta, Paid - LinkedIn, Paid - Search | 20% |
| Website Organic | Organic Search, Direct, Email, Referrals, Social | 15% |
| Outbound | Offline Sources | 5% |

### Key Reports

#### 1. Marketing Mix Funnel by Channel
```
Object: Deal
Filters: Create Date = This Quarter
Measures:
  - Count of Deals (Volume)
  - Sum of Amount (Value)
  - Win Rate (Closed Won / Total Closed)
Breakdown: First Touch Marketing Attribution
  - Digital Outreach
  - Live Events
  - Outbound
  - Paid Advertising
  - Website Organic
  - No Data
Visualization: Table with funnel metrics per channel
```

#### 2. Channel Velocity Report
```
Object: Deal
Filter: Deal Stage = "Closed Won" AND Close Date = This Quarter
Measures:
  - Average Days to Close
  - Average Deal Size
  - Count of Deals
Breakdown: First Touch Marketing Attribution
Visualization: Scatter plot (Days to Close vs. Deal Size, bubble = Count)
```

#### 3. Marketing Mix ROI
```
Object: Custom (requires Marketing Spend data)
Measures:
  - Marketing Spend (by channel)
  - Revenue Generated (Sum of Closed Won Amount)
  - ROI = (Revenue - Spend) / Spend × 100
Breakdown: Marketing Attribution Category
Visualization: Bar chart with ROI line overlay
```

#### 4. Pipeline by Marketing Initiative
```
Object: Deal
Filter:
  - Deal Stage NOT IN ("Closed Won", "Closed Lost")
Measure: Sum of Amount
Breakdown: First Touch Marketing Attribution Drill-Down 1
Visualization: Horizontal bar chart (top 20)
```

### Event Marketing Sub-Reports

#### 5. Event Performance Comparison
```
Object: Deal
Filter: First Touch Marketing Attribution = "Live Events"
Measures:
  - Deal Count
  - Pipeline Value
  - Won Revenue
  - Conversion Rate
Breakdown: First Touch Marketing Attribution Drill-Down 1
  (Shows specific events: NRB, C3, Exponential, etc.)
Visualization: Table sorted by Pipeline Value
```

#### 6. Event ROI Calculator
```
Object: Custom calculation
Inputs:
  - Event Cost (Sponsorship + Travel + Materials)
  - Deals Sourced (by event drill-down)
  - Pipeline Value
  - Won Revenue
Outputs:
  - Cost per Lead
  - Cost per Opportunity
  - Event ROI
Visualization: Table with conditional formatting
```

---

## Channel Attribution Dashboard

### Purpose
Deep-dive into attribution models to understand the customer journey and optimize touchpoints.

### Attribution Models

| Model | Property | Use Case |
|-------|----------|----------|
| First-Touch | `first_touch_marketing_attribution` | Lead source credit |
| Linear-Touch | `linear_touch_marketing_attribution` | Multi-touch journey |
| Traffic Source | `hs_analytics_source` | Website behavior |
| Latest Source | `hs_analytics_latest_source` | Recent engagement |

### Key Reports

#### 1. First-Touch Attribution Analysis
```
Object: Deal
Filter: Deal Stage = "Closed Won" AND Close Date = This Year
Measures:
  - Count of Deals
  - Sum of Amount
  - Win Rate
Breakdown: First Touch Marketing Attribution
Visualization: Pie chart + data table
```

#### 2. Multi-Touch Journey Analysis
```
Object: Company
Measures:
  - Count of Companies with First Touch Attribution
  - Count of Companies with Linear Touch Attribution
  - % with Multiple Touchpoints
Breakdown: Lifecycle Stage
Visualization: Sankey diagram or flow chart
```

#### 3. Channel Conversion Paths
```
Object: Deal
Filter: Close Date = This Quarter
Measures:
  - Count of Deals
Breakdown:
  - Row: First Touch Marketing Attribution
  - Column: Linear Touch Marketing Attribution
Visualization: Heat map matrix
```

#### 4. Traffic Source to Pipeline
```
Object: Deal
Measures:
  - Count of Deals
  - Sum of Amount
Breakdown: Original Traffic Source (hs_analytics_source)
  - Organic Search
  - Paid Search
  - Email Marketing
  - Organic Social
  - Referrals
  - Other Campaigns
  - Direct Traffic
  - Offline Sources
  - Paid Social
Visualization: Horizontal bar chart
```

#### 5. Source Drill-Down Analysis
```
Object: Deal
Filter: Original Traffic Source = [Selected]
Measures:
  - Count of Deals
  - Pipeline Value
Breakdown: Original Traffic Source Drill-Down 1
Visualization: Treemap
```

---

## Campaign Performance Dashboard

### Purpose
Track individual campaign performance, engagement, and contribution to pipeline.

### Campaign Types Tracked

| Campaign Type | Tracking Method | Key Metrics |
|---------------|-----------------|-------------|
| Email Campaigns | Marketing Email Object | Opens, Clicks, Conversions |
| Events | Marketing Event Object | Registrations, Attendance |
| Webinars | Marketing Event Object | Registrations, Attendance, Pipeline |
| Content Campaigns | Form Submissions | Downloads, MQLs |
| Paid Campaigns | UTM Parameters | Impressions, Clicks, Conversions |

### Key Reports

#### 1. Campaign Pipeline Contribution
```
Object: Deal
Measures:
  - Count of Deals
  - Sum of Amount
  - Average Deal Size
Breakdown: First Touch Converting Campaign (hs_analytics_first_touch_converting_campaign)
Visualization: Table with sparklines
```

#### 2. Email Campaign Performance
```
Object: Marketing Email
Measures:
  - Send Count
  - Open Rate
  - Click Rate
  - Unsubscribe Rate
  - Contacts Influenced
Breakdown: Campaign Name
Filter: Send Date = This Quarter
Visualization: Table with conditional formatting
```

#### 3. Campaign Funnel Analysis
```
Object: Contact
Filter: First Touch Converting Campaign = [Selected Campaign]
Measures:
  - Count at each stage
  - Conversion rate between stages
Breakdown: Lifecycle Stage
Visualization: Funnel chart
```

#### 4. Campaign Velocity
```
Object: Deal
Filter: First Touch Converting Campaign IS NOT NULL
Measures:
  - Average Days from Campaign Touch to MQL
  - Average Days from MQL to SQL
  - Average Days from SQL to Close
Breakdown: Campaign Name (top 10)
Visualization: Stacked bar chart
```

---

## Event Marketing Dashboard

### Purpose
Track live event performance, ROI, and pipeline impact from conferences, retreats, and sponsored events.

### Events Tracked (2024-2026)

| Event Category | Examples |
|----------------|----------|
| Major Conferences | NRB, C3, Exponential, Spire, SBC |
| Industry Events | RightNow Media, Dunham Summit, BCI |
| Hosted Events | Pastor Retreats, Golf Events, PRAY Events |
| Regional Events | Mega Metro Conferences, Young Guns |

### Key Reports

#### 1. Event Pipeline Summary
```
Object: Deal
Filter: First Touch Marketing Attribution = "Live Events"
Measures:
  - Total Deals
  - Total Pipeline Value
  - Closed Won Amount
  - Win Rate
Breakdown: First Touch Marketing Attribution Drill-Down 1 (Event Name)
Time: This Year vs. Last Year
Visualization: Table with YoY comparison
```

#### 2. Event Funnel by Event
```
Object: Deal
Filter: First Touch Marketing Attribution Drill-Down 1 = [Event Name]
Measures:
  - Leads Generated
  - MQLs Created
  - Opportunities Created
  - Deals Won
Visualization: Funnel chart
```

#### 3. Event Lead Quality
```
Object: Contact
Filter: First Conversion = [Event Form]
Measures:
  - Count of Contacts
  - Average Lead Score
  - % MQL Conversion
  - % SQL Conversion
Breakdown: Event Name
Visualization: Scatter plot (Lead Count vs. MQL Rate)
```

#### 4. Event ROI Table
```
Measures (Manual + Calculated):
| Event | Cost | Leads | MQLs | Opps | Won Rev | ROI |
|-------|------|-------|------|------|---------|-----|
| NRB 2025 | $X | n | n | n | $Y | Z% |
| C3 2025 | $X | n | n | n | $Y | Z% |
...
Visualization: Table with conditional ROI highlighting
```

#### 5. Event Attendance Tracking
```
Object: Marketing Event
Measures:
  - Registered Count
  - Attended Count
  - Attendance Rate
  - No-Show Rate
Breakdown: Event Name
Visualization: Bar chart with attendance rate line
```

---

## Digital Marketing Dashboard

### Purpose
Track digital channel performance including paid advertising, SEO, social media, and email.

### Digital Channels

| Channel | Source Property Value | Key Metrics |
|---------|----------------------|-------------|
| Paid Search | PAID_SEARCH | CPC, Conversions, ROAS |
| Paid Social (Meta) | PAID_SOCIAL + "Meta" | Impressions, Clicks, CPL |
| Paid Social (LinkedIn) | PAID_SOCIAL + "LinkedIn" | Impressions, Clicks, CPL |
| Organic Search | ORGANIC_SEARCH | Rankings, Traffic, Conversions |
| Organic Social | SOCIAL_MEDIA | Reach, Engagement, Conversions |
| Email Marketing | EMAIL_MARKETING | Opens, Clicks, Conversions |
| Referrals | REFERRALS | Traffic, Conversions |

### Key Reports

#### 1. Digital Channel Performance
```
Object: Contact
Filter: Create Date = This Month
Measures:
  - Contact Count
  - MQL Conversion Rate
  - Pipeline Influenced
Breakdown: Original Traffic Source
Visualization: Horizontal bar chart
```

#### 2. Paid Advertising Performance
```
Object: Deal
Filter: Original Traffic Source IN (PAID_SEARCH, PAID_SOCIAL)
Measures:
  - Deal Count
  - Pipeline Value
  - Won Revenue
  - Cost (from Ads platform)
  - ROAS = Revenue / Cost
Breakdown: Original Traffic Source Drill-Down 1
Visualization: Table with ROAS highlighting
```

#### 3. Organic Traffic Trends
```
Object: Contact
Filter: Original Traffic Source IN (ORGANIC_SEARCH, DIRECT_TRAFFIC, REFERRALS)
Measures:
  - Contact Count (weekly)
  - MQL Count
  - Conversion Rate
Breakdown: Original Traffic Source
Time: Last 12 months
Visualization: Multi-line chart
```

#### 4. Email Marketing Funnel
```
Object: Marketing Email
Measures:
  - Emails Sent
  - Emails Delivered
  - Emails Opened
  - Links Clicked
  - Conversions
Visualization: Funnel with conversion rates
```

#### 5. Social Media Lead Generation
```
Object: Contact
Filter: Original Traffic Source = "Organic Social" OR Original Traffic Source Drill-Down 1 CONTAINS "Instagram|Facebook|LinkedIn"
Measures:
  - Lead Count
  - MQL Rate
  - Pipeline Generated
Breakdown: Original Traffic Source Drill-Down 1
Visualization: Bar chart
```

---

## Content & Engagement Dashboard

### Purpose
Track content performance and engagement metrics to optimize content strategy.

### Key Reports

#### 1. Form Conversion Analysis
```
Object: Contact
Measures:
  - Form Submissions (Count)
  - Unique Submitters
  - MQL Conversion Rate
Breakdown: First Conversion (Form Name)
Visualization: Table sorted by submissions
```

#### 2. Content Engagement by Lifecycle Stage
```
Object: Contact
Measures:
  - Average Page Views
  - Average Sessions
  - Average Time on Site
Breakdown: Lifecycle Stage
Visualization: Bar chart
```

#### 3. High-Intent Content Performance
```
Object: Contact
Filter: First Conversion CONTAINS ("Demo", "Pricing", "Contact", "Quote")
Measures:
  - Submission Count
  - SQL Conversion Rate
  - Pipeline Generated
Breakdown: First Conversion
Visualization: Table with SQL rate highlighting
```

#### 4. Content to Pipeline Attribution
```
Object: Deal
Measures:
  - Pipeline Value
  - Won Revenue
Breakdown: First Touch Converting Campaign
Filter: Campaign Type = Content
Visualization: Horizontal bar chart
```

---

## Lead Generation Dashboard

### Purpose
Track lead volume, quality, and conversion across the funnel.

### Key Metrics

| Metric | Property | Target |
|--------|----------|--------|
| Total Leads | Lifecycle Stage = Lead | Growth |
| MQL Volume | Lifecycle Stage = MQL | Per quota |
| SQL Volume | Lifecycle Stage = SQL | Per quota |
| Lead Velocity | Week-over-week growth | Positive |
| Lead Score Distribution | Lead Score ranges | Right-skewed |

### Key Reports

#### 1. Lead Volume Trend
```
Object: Contact
Measures: Count
Filter: Lifecycle Stage IN (Lead, MQL, SQL)
Breakdown:
  - Row: Week/Month
  - Column: Lifecycle Stage
Visualization: Stacked area chart
```

#### 2. Lead Quality Distribution
```
Object: Contact
Filter: Lifecycle Stage IN (Lead, MQL)
Measures: Count
Breakdown: Lead Score Ranges
  - Hot (1000-2000)
  - Warm (500-999)
  - Developing (100-499)
  - Cold (0-99)
  - Disqualified (<0)
Visualization: Pie chart
```

#### 3. Lead Conversion Funnel
```
Object: Contact
Measures:
  - Subscriber → Lead Rate
  - Lead → MQL Rate
  - MQL → SQL Rate
  - SQL → Opportunity Rate
  - Opportunity → Customer Rate
Visualization: Funnel with conversion rates
```

#### 4. Lead Source Quality
```
Object: Contact
Filter: Lifecycle Stage IN (Lead, MQL, SQL)
Measures:
  - Lead Count
  - MQL Rate
  - SQL Rate
  - Average Lead Score
Breakdown: Original Traffic Source
Visualization: Table sorted by SQL Rate
```

#### 5. Lead by ICP Tier
```
Object: Contact
Measures:
  - Contact Count
  - MQL Count
  - Pipeline Value
Breakdown: ICP Tier (from associated company)
Visualization: Stacked bar chart
```

#### 6. Lead by Company Segment
```
Object: Contact
Measures:
  - Contact Count
  - MQL Rate
  - Average Deal Size
Breakdown: Company Segment
  - Whale
  - Elephant
  - Deer
  - Rabbit
  - Mouse
Visualization: Horizontal bar chart
```

---

## Customer Lifecycle Dashboard

### Purpose
Track customer health, expansion opportunities, and retention/churn metrics for the Leader segment.

### Key Reports

#### 1. Customer Acquisition Trend
```
Object: Company
Filter: Lifecycle Stage = Customer
Measures:
  - New Customers (Date entered Customer = This Period)
  - Total Customers
  - Net New (New - Churned)
Breakdown: Month
Visualization: Bar chart with net new line
```

#### 2. Customer by Segment
```
Object: Company
Filter: Lifecycle Stage = Customer
Measures:
  - Customer Count
  - Total Revenue
  - Average Contract Value
Breakdown: Company Segment
Visualization: Donut chart with table
```

#### 3. Churn Analysis
```
Object: Company
Filter: Lifecycle Stage = Churned
Measures:
  - Churned Customer Count
  - Lost Revenue (Sum of Amount from Closed Lost renewal deals)
Breakdown: Month
Visualization: Bar chart with trend line
```

#### 4. Retention Cohort Analysis
```
Object: Company
Measures:
  - Starting Customers (by acquisition month)
  - Active Customers (by month since acquisition)
  - Retention Rate
Breakdown: Acquisition Cohort (Month)
Visualization: Cohort retention table
```

#### 5. Customer Health Score Distribution
```
Object: Company
Filter: Lifecycle Stage = Customer
Measures: Count
Breakdown: Customer Health Score (if implemented)
  - Healthy
  - At Risk
  - Critical
Visualization: Gauge or pie chart
```

#### 6. Expansion Pipeline
```
Object: Deal
Filter:
  - Associated Company Lifecycle Stage = Customer
  - Deal Type = Expansion/Upsell
Measures:
  - Deal Count
  - Pipeline Value
  - Win Rate
Breakdown: Company Segment
Visualization: Table
```

---

## Report Specifications

### Standard Report Parameters

| Parameter | Options |
|-----------|---------|
| Date Range | This Week, This Month, This Quarter, This Year, Last X Days, Custom |
| Comparison | Previous Period, Previous Year, None |
| Filters | Lifecycle Stage, Company Segment, ICP Tier, Attribution, Owner |
| Breakdown | By Time, By Property, By Owner |

### Calculated Properties for Reporting

| Property Name | Calculation | Used In |
|---------------|-------------|---------|
| Days in Stage | Current Date - Date Entered Stage | Velocity reports |
| Lead Age | Current Date - Create Date | Lead aging |
| Time to MQL | Date Entered MQL - Create Date | Conversion velocity |
| Time to SQL | Date Entered SQL - Date Entered MQL | Sales handoff speed |
| Time to Close | Close Date - Date Entered Opportunity | Sales cycle |

### Custom Report Formulas

#### MQL Rate
```
Count(Contacts WHERE Lifecycle Stage = MQL AND Date Entered MQL = This Period)
÷
Count(Contacts WHERE Lifecycle Stage WAS Lead AND Date Entered Lead = Previous Period)
× 100
```

#### Pipeline Velocity
```
(Count of Opportunities × Average Deal Size × Win Rate)
÷
Average Sales Cycle Days
```

#### Marketing Contribution %
```
Sum(Deal Amount WHERE Channel Attribution = Marketing AND Close Date = This Period)
÷
Sum(All Deal Amount WHERE Close Date = This Period)
× 100
```

---

## Implementation Guide

### Dashboard Creation Steps

1. **Create Report Folder Structure**
   ```
   Reports/
   ├── Marketing/
   │   ├── Executive/
   │   ├── Marketing Mix/
   │   ├── Channel Attribution/
   │   ├── Campaigns/
   │   ├── Events/
   │   ├── Digital/
   │   ├── Content/
   │   ├── Lead Generation/
   │   └── Customer Lifecycle/
   └── Dashboard/
       └── [Dashboard files]
   ```

2. **Build Core Reports First**
   - Pipeline by Attribution
   - Lifecycle Stage Funnel
   - Lead Volume Trend
   - Conversion Rate Table

3. **Create Calculated Properties**
   - Ensure all calculated properties exist
   - Verify sync properties are working

4. **Build Dashboards**
   - Add reports in logical groupings
   - Set appropriate date ranges
   - Configure filters and drill-downs

5. **Set Permissions**
   - Assign dashboard ownership
   - Configure view/edit permissions by team

### Refresh Schedule

| Dashboard | Refresh | Delivery |
|-----------|---------|----------|
| Executive | Daily 6 AM | Email to CMO, VP |
| Marketing Mix | Daily 8 AM | Email to Directors |
| Channel Attribution | Weekly Monday | Email to Marketing Ops |
| Campaign | Real-time | On-demand |
| Lead Generation | Daily 8 AM | Email to Demand Gen |
| Customer Lifecycle | Weekly Monday | Email to Customer Marketing |

### Alert Configuration

| Alert | Trigger | Recipients |
|-------|---------|------------|
| MQL Spike | >150% of daily average | Demand Gen, Marketing Ops |
| Pipeline Drop | <50% of weekly target | CMO, VP Marketing |
| Churn Warning | >3 churns in a week | Customer Marketing, CS |
| Event Lead Surge | >50 leads from single event | Event Marketing |

---

*Dashboard documentation maintained by Marketing Operations. For additions or modifications, submit a request through Marketing Ops.*
