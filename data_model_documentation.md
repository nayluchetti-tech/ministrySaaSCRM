# Ministry SaaS HubSpot Data Model Documentation

## Comprehensive Object & Relationship Guide

**Version:** 1.0
**Last Updated:** January 30, 2026
**Owner:** Data Operations

---

## Table of Contents

1. [Data Model Overview](#data-model-overview)
2. [Standard Objects](#standard-objects)
3. [Custom Objects](#custom-objects)
4. [Object Associations](#object-associations)
5. [Property Architecture](#property-architecture)
6. [Calculated Properties](#calculated-properties)
7. [Data Sync Patterns](#data-sync-patterns)
8. [Object Lifecycle](#object-lifecycle)

---

## Data Model Overview

### Entity-Relationship Diagram

```
                                    ┌─────────────────┐
                                    │     LEADER      │
                                    │  (Custom Object)│
                                    │  212 properties │
                                    └────────┬────────┘
                                             │
                                    Association: Leader to Company
                                    Association: Leader to Deal
                                             │
    ┌─────────────────┐            ┌────────┴────────┐            ┌─────────────────┐
    │     CONTACT     │◄──────────►│     COMPANY     │◄──────────►│      DEAL       │
    │  412 properties │            │  296 properties │            │  597 properties │
    └────────┬────────┘            └────────┬────────┘            └────────┬────────┘
             │                              │                              │
             │                              │                              │
             ▼                              ▼                              ▼
    ┌─────────────────┐            ┌─────────────────┐            ┌─────────────────┐
    │      LEAD       │            │    CAMPAIGN     │            │   LINE ITEM     │
    │  187 properties │            │   61 properties │            │   71 properties │
    └─────────────────┘            └─────────────────┘            └────────┬────────┘
                                                                          │
                                                                          ▼
                                                                 ┌─────────────────┐
                                                                 │     PRODUCT     │
                                                                 │   39 properties │
                                                                 └─────────────────┘

    ┌─────────────────┐     ┌─────────────────┐     ┌─────────────────┐
    │      CALL       │     │     MEETING     │     │   MARKETING     │
    │   41 properties │     │   45 properties │     │     EMAIL       │
    │                 │     │                 │     │   70 properties │
    └─────────────────┘     └─────────────────┘     └─────────────────┘
           │                       │                       │
           └───────────────────────┴───────────────────────┘
                                   │
                           Activity Timeline
                           (Contact, Company, Deal)
```

### Object Inventory Summary

| Object | Type | Property Count | Records (Est.) | Primary Use |
|--------|------|----------------|----------------|-------------|
| Contact | Standard | 412 | ~15,000+ | Person records |
| Company | Standard | 296 | ~8,000+ | Organization records |
| Deal | Standard | 597 | ~5,000+ | Sales opportunities |
| Lead | Standard | 187 | ~3,000+ | BDR/SDR prospecting |
| Leader | Custom | 212 | ~1,000+ | Decision-maker tracking |
| Call | Standard | 41 | ~10,000+ | Phone activity |
| Meeting | Standard | 45 | ~5,000+ | Calendar events |
| Campaign | Standard | 61 | ~100+ | Marketing campaigns |
| Marketing Event | Standard | 46 | ~50+ | Event management |
| Marketing Email | Standard | 70 | ~500+ | Email marketing |
| Workflow | Standard | 47 | 220+ | Automation |
| Project | Standard | 92 | ~500+ | Onboarding |
| Invoice | Standard | 79 | ~1,000+ | Billing |
| Quote | Standard | 73 | ~2,000+ | Proposals |
| Product | Standard | 39 | ~50+ | Product catalog |
| Line Item | Standard | 71 | ~5,000+ | Deal line items |

---

## Standard Objects

### Contact Object

The Contact object represents individual people who interact with Ministry SaaS.

#### Object Definition
| Attribute | Value |
|-----------|-------|
| Object Type | Standard |
| Object ID | `0-1` |
| Label | Contact |
| Property Groups | 15+ |
| Total Properties | 412 |

#### Key Property Groups

| Group Name | Internal Name | Description |
|------------|---------------|-------------|
| Core Info | `core_info` | Name, email, phone, address |
| Company Properties | `company_properties` | Synced company data |
| Analytics Information | `analyticsinformation` | Traffic and engagement |
| Lifecycle Stages | `contactlcs` | Pipeline progression |
| Conversion Information | `conversioninformation` | IP-based data |
| Ads & Other | `ads&other_information` | Advertising data |
| Discontinued | `discontinued` | Archived properties |

#### Critical Contact Properties

| Property | Internal Name | Type | Required | Unique |
|----------|---------------|------|----------|--------|
| Email | `email` | string | Yes | Yes |
| First Name | `firstname` | string | Yes | No |
| Last Name | `lastname` | string | Yes | No |
| Lifecycle Stage | `lifecyclestage` | enumeration | Yes | No |
| Contact Owner | `hubspot_owner_id` | enumeration | Yes | No |

---

### Company Object

The Company object represents organizations and ministries.

#### Object Definition
| Attribute | Value |
|-----------|-------|
| Object Type | Standard |
| Object ID | `0-2` |
| Label | Company |
| Property Groups | 12+ |
| Total Properties | 296 |

#### Key Property Groups

| Group Name | Internal Name | Description |
|------------|---------------|-------------|
| Core Info | `core_info` | Name, domain, address |
| Source & Attribution | `2_-_source_and_attribution` | Marketing attribution |
| Deal Information | `4_-_deal_information` | Revenue data |
| Company Information | `companyinformation` | Firmographics |
| Lifecycle Stages | `companylcs` | Pipeline progression |
| Company Signals | `company_signals` | Intent tracking |

#### Critical Company Properties

| Property | Internal Name | Type | Required | Unique |
|----------|---------------|------|----------|--------|
| Company Name | `name` | string | Yes | No |
| Website URL | `website` | string | Yes | Yes |
| Company Domain | `domain` | string | Yes | Yes |
| Company Type | `company_type` | enumeration | Yes | No |
| Company Owner | `hubspot_owner_id` | enumeration | Yes | No |

#### Ministry-Specific Properties

| Property | Internal Name | Options/Type |
|----------|---------------|--------------|
| Company Type | `company_type` | Church, Parachurch, Media Ministry, Podcast, Nonprofit, Agency, etc. |
| Company Segment | `company_segment` | Whale, Elephant, Deer, Rabbit, Mouse |
| ICP Tier | `icp_tier` | ICP 1, ICP 2, ICP 3, IPP |
| Church Size | `church_size_attendance` | Attendance ranges |
| Number of Locations | `number_of_locations` | Numeric |
| Distribution Channels | `distribution_channels` | Multi-select |
| Growth Priorities | `growth_priorities` | Multi-select |
| Primary Challenge | `primary_challenge` | Single-select |

---

### Deal Object

The Deal object represents sales opportunities and revenue.

#### Object Definition
| Attribute | Value |
|-----------|-------|
| Object Type | Standard |
| Object ID | `0-3` |
| Label | Deal |
| Property Groups | 20+ |
| Total Properties | 597 |
| Pipelines | 2 (Main, Ads) |

#### Key Property Groups

| Group Name | Internal Name | Description |
|------------|---------------|-------------|
| Revenue Information | `2_-_revenue_information` | Amount, ACV, TCV |
| Qualification | `4_-_qualification` | Stage, probability |
| Analytics Information | `analyticsinformation` | Attribution |
| Associations | `associations_` | Related records |
| Ads & Others | `ads&others` | Ads pipeline |

#### Deal Pipelines

**Pipeline 1: Main Sales (Pray Channel)**

| Stage | Stage ID | Probability | Category |
|-------|----------|-------------|----------|
| Qualifying & Discovery | `544674` | 10% | In Progress |
| Pitch | `544672` | 25% | In Progress |
| Proposal | `1558618` | 50% | In Progress |
| Contract Sent | `59159965` | 75% | In Progress |
| Closed Won | `544675` | 100% | Closed Won |
| Closed Lost | `544676` | 0% | Closed Lost |

**Pipeline 2: Ads and Other**

| Stage | Stage ID | Probability | Category |
|-------|----------|-------------|----------|
| Qualifying & Discovery | TBD | 10% | In Progress |
| Pitch | TBD | 25% | In Progress |
| Proposal | TBD | 50% | In Progress |
| Contract Sent | TBD | 75% | In Progress |
| Closed Won | TBD | 100% | Closed Won |
| Closed Lost | TBD | 0% | Closed Lost |

#### Critical Deal Properties

| Property | Internal Name | Type | Required |
|----------|---------------|------|----------|
| Deal Name | `dealname` | string | Yes |
| Amount | `amount` | number | Yes |
| Close Date | `closedate` | datetime | Yes |
| Pipeline | `pipeline` | enumeration | Yes |
| Deal Stage | `dealstage` | enumeration | Yes |
| Deal Owner | `hubspot_owner_id` | enumeration | Yes |

---

### Lead Object

The Lead object enables prospecting workflows for BDRs/SDRs.

#### Object Definition
| Attribute | Value |
|-----------|-------|
| Object Type | Standard |
| Object ID | `0-39` |
| Label | Lead |
| Property Groups | 3+ |
| Total Properties | 187 |

#### Lead Pipeline

| Stage | Category | Description |
|-------|----------|-------------|
| New | Not Started | Freshly created |
| Attempting | In Progress | Active outreach |
| Connected | In Progress | Contact made |
| Qualified | Qualified | Meets criteria, convert to deal |
| Disqualified | Unqualified | Does not meet criteria |

#### Critical Lead Properties

| Property | Internal Name | Type | Description |
|----------|---------------|------|-------------|
| Lead Name | `hs_lead_name` | string | Full name |
| Lead Label | `hs_lead_label` | enumeration | Hot, Warm, Cold |
| Lead Source | `hs_lead_source` | enumeration | Traffic source |
| Lead Stage | `hs_lead_pipeline_stage` | enumeration | Pipeline stage |
| Disqualification Reason | `hs_lead_disqualification_reason` | enumeration | Why disqualified |
| Call Count | `hs_lead_call_count` | number | Outreach calls |
| Email Count | `hs_lead_email_count` | number | Outreach emails |
| Meeting Count | `hs_lead_meeting_count` | number | Meetings booked |

---

## Custom Objects

### Leader Object

The Leader custom object tracks key decision-makers and influencers (content creators, pastors, etc.) separately from organizational contacts.

#### Object Definition
| Attribute | Value |
|-----------|-------|
| Object Type | Custom |
| Object ID | `2-41621067` |
| Label | Leader |
| Property Groups | 5+ |
| Total Properties | 212 |

#### Purpose

Leaders represent the "talent" or "artist" - the public-facing individual whose content is distributed through the platform. This differs from organizational contacts who may handle operations or billing.

#### Key Leader Properties

| Property | Internal Name | Type | Description |
|----------|---------------|------|-------------|
| Leader Name | `leader_name` | string | Full name |
| Leader Website | `leader_website` | string | Personal website |
| Leader Type | `leader_type` | enumeration | Type of leader |
| Social Following | Various | number | Social media metrics |
| Content Reach | Various | number | Audience metrics |

#### Leader Associations

| Associated Object | Association Label | Cardinality |
|-------------------|-------------------|-------------|
| Company | Leader to Company | Many-to-Many |
| Deal | Leader to Deal | Many-to-Many |
| Contact | Leader to Contact | One-to-Many |

---

## Object Associations

### Standard Associations

| Parent | Child | Cardinality | Association Label |
|--------|-------|-------------|-------------------|
| Company | Contact | 1:N | Company to Contact |
| Company | Deal | 1:N | Company to Deal |
| Contact | Deal | N:N | Contact to Deal |
| Deal | Line Item | 1:N | Deal to Line Item |
| Line Item | Product | N:1 | Line Item to Product |
| Contact | Lead | 1:1 | Contact to Lead |
| Company | Lead | 1:1 | Company to Lead |

### Custom Association Labels

#### Contact to Deal Labels
| Label | Purpose |
|-------|---------|
| Primary Contact | Main deal contact |
| Billing Contact | Handles invoicing |
| Key Manager | Internal champion |
| Decision Maker | Budget authority |

#### Company to Deal Labels
| Label | Purpose |
|-------|---------|
| Primary Company | Main organization |
| Agency | Partner agency |
| Child | Subsidiary organization |

#### Leader to Deal Labels
| Label | Purpose |
|-------|---------|
| Associated Leader | Content creator for this deal |

### Association-Based Properties

These properties auto-populate based on associations:

| Property | Object | Source | Description |
|----------|--------|--------|-------------|
| `associated_agency_company_name` | Deal | Company (Agency label) | Agency name |
| `associated_billing_contact_email` | Deal | Contact (Billing label) | Billing email |
| `associated_key_manager_email` | Deal | Contact (Key Manager label) | Champion email |
| `associated_leader_name` | Deal | Leader | Leader name |
| `company_segment` | Contact | Company | Revenue segment |
| `icp_tier__from_associated_company_` | Contact | Company | ICP tier |

---

## Property Architecture

### Property Types

| Type | Description | Example |
|------|-------------|---------|
| string | Text value | Company Name |
| number | Numeric value | Amount |
| datetime | Date and time | Close Date |
| enumeration | Single-select dropdown | Deal Stage |
| bool | True/False | Is Customer |
| phone_number | Formatted phone | Phone |

### Property Categories

| Category | Description | Editable |
|----------|-------------|----------|
| HubSpot Defined | System properties | No |
| Custom | User-created | Yes |
| Calculated | Computed values | Read-only |
| Rollup | Aggregated from associations | Read-only |

### Property Groups by Object

#### Contact Property Groups
```
├── core_info (35 properties)
├── company_properties (22 properties)
├── analyticsinformation (12 properties)
├── contactlcs (32 properties)
├── conversioninformation (6 properties)
├── ads&other_information (4 properties)
├── deals_and_revenue (2 properties)
├── contactscripted (1 property)
└── discontinued (50+ archived)
```

#### Company Property Groups
```
├── core_info (18 properties)
├── companyinformation (15 properties)
├── 2_-_source_and_attribution (18 properties)
├── 4_-_deal_information (4 properties)
├── companylcs (32 properties)
├── company_signals (4 properties)
├── avoma (1 property)
└── discontinued (30+ archived)
```

#### Deal Property Groups
```
├── 2_-_revenue_information (7 properties)
├── 4_-_qualification (18 properties)
├── analyticsinformation (20 properties)
├── associations_ (15 properties)
├── ads&others (28 properties)
└── [Pipeline-specific stage timing properties]
```

---

## Calculated Properties

### Contact Calculated Properties

| Property | Formula/Source | Description |
|----------|----------------|-------------|
| `associated_company_record_id` | Associated Company | Company ID sync |
| `company_segment` | Associated Company | Revenue segment |
| `icp_tier__from_associated_company_` | Associated Company | ICP tier |
| `lead_pipeline_stage` | Associated Lead | Lead stage |
| `associated_leader_name` | Associated Leader | Leader name |

### Company Calculated Properties

| Property | Formula/Source | Description |
|----------|----------------|-------------|
| `hs_total_deal_value` | Sum of Deal.amount | Total open deal value |
| `total_revenue` | Sum of closed-won deals | Lifetime revenue |
| `first_contact_createdate` | Min of Contact.createdate | First contact date |

### Deal Calculated Properties

| Property | Formula/Source | Description |
|----------|----------------|-------------|
| `amount_in_home_currency` | Amount * Exchange Rate | Normalized amount |
| `hs_acv` | Calculated | Annual contract value |
| `hs_tcv` | Calculated | Total contract value |
| `hs_forecast_amount` | Amount * Probability | Weighted amount |
| `days_to_close` | closedate - createdate | Sales cycle length |
| `associated_contact_record_id` | Primary Contact | Contact ID |

### Lead Calculated Properties

| Property | Formula/Source | Description |
|----------|----------------|-------------|
| `hs_lead_call_count` | Count of Calls | Total calls made |
| `hs_lead_email_count` | Count of Emails | Total emails sent |
| `hs_lead_meeting_count` | Count of Meetings | Meetings booked |
| `hs_lead_outreach_activity_count` | Sum of activities | Total outreach |

---

## Data Sync Patterns

### Cross-Object Property Sync

Properties that automatically sync between objects:

#### Company → Contact Sync
```
company_type         → company_type__from_associated_company_
company_segment      → company_segment
icp_tier             → icp_tier__from_associated_company_
primary_challenge    → primary_challenge__from_associated_company_
timeline_for_solution → timeline_for_a_solution__from_associated_company_
```

#### Contact → Deal Sync
```
lifecycle_stage      → lifecycle_stage (updates)
original_source      → hs_analytics_source
hubspot_owner_id     → deals inherit owner
```

#### Lead → Contact Sync
```
lead_pipeline_stage  → lead_pipeline_stage (on contact)
```

#### Company → Deal Sync
```
marketing_attribution → linear_touch_marketing_attribution
```

### Workflow-Based Sync Patterns

| Pattern | Trigger | Action |
|---------|---------|--------|
| Attribution Copy | Deal created | Copy contact source to deal |
| Segment Sync | Company segment changes | Update associated contacts |
| Leader Sync | Leader associated | Copy leader name to deal |
| Lifecycle Progression | Score threshold | Update lifecycle stage |

---

## Object Lifecycle

### Contact Lifecycle

```
                   ┌──────────────┐
                   │   Created    │
                   │  (Subscriber)│
                   └──────┬───────┘
                          │
                   ┌──────▼───────┐
                   │     Lead     │
                   │  (Scoring)   │
                   └──────┬───────┘
                          │
              ┌───────────┴───────────┐
              │                       │
       ┌──────▼───────┐        ┌──────▼───────┐
       │     MQL      │        │  Disqualified│
       │ (Qualified)  │        │              │
       └──────┬───────┘        └──────────────┘
              │
       ┌──────▼───────┐
       │     SQL      │
       │ (Sales Ready)│
       └──────┬───────┘
              │
       ┌──────▼───────┐
       │  Opportunity │
       │ (Deal Open)  │
       └──────┬───────┘
              │
       ┌──────┴───────┐
       │              │
┌──────▼───────┐ ┌────▼──────┐
│   Customer   │ │   Lost    │
│              │ │           │
└──────┬───────┘ └───────────┘
       │
┌──────▼───────┐
│   Churned    │
│              │
└──────────────┘
```

### Deal Lifecycle

```
┌─────────────────────────────────────────────────────────────────┐
│                        DEAL PIPELINE                            │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  ┌──────────┐   ┌──────────┐   ┌──────────┐   ┌──────────┐    │
│  │ Qualify  │──▶│  Pitch   │──▶│ Proposal │──▶│ Contract │    │
│  │ Discovery│   │          │   │          │   │   Sent   │    │
│  └──────────┘   └──────────┘   └──────────┘   └────┬─────┘    │
│                                                     │          │
│                                          ┌──────────┴────────┐ │
│                                          │                   │ │
│                                   ┌──────▼───────┐    ┌──────▼─┴────┐
│                                   │  Closed Won  │    │ Closed Lost │
│                                   │              │    │             │
│                                   └──────────────┘    └─────────────┘
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Lead Lifecycle

```
┌─────────────────────────────────────────────────────────────────┐
│                        LEAD PIPELINE                            │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  ┌──────────┐   ┌──────────┐   ┌──────────┐                   │
│  │   New    │──▶│Attempting│──▶│Connected │                   │
│  │          │   │          │   │          │                   │
│  └──────────┘   └──────────┘   └────┬─────┘                   │
│                                     │                          │
│                          ┌──────────┴────────┐                 │
│                          │                   │                 │
│                   ┌──────▼───────┐    ┌──────▼───────┐        │
│                   │  Qualified   │    │ Disqualified │        │
│                   │ (→ Deal)     │    │              │        │
│                   └──────────────┘    └──────────────┘        │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## Data Validation Requirements

### Required Associations by Stage

#### Deal: Contract Sent Stage
- [ ] Primary Company associated
- [ ] Primary Contact associated
- [ ] Billing Contact associated (label)
- [ ] Key Manager associated (label)
- [ ] Amount populated
- [ ] Close date set

#### Deal: Closed Won
- [ ] All Contract Sent requirements
- [ ] Closed Won Reason selected
- [ ] Amount confirmed

#### Deal: Closed Lost
- [ ] Closed Lost Reason selected
- [ ] Closed Lost detail (if Other)

### Data Quality Rules

| Rule | Object | Condition | Action |
|------|--------|-----------|--------|
| Valid Domain | Company | Website must be valid | Block save |
| Email Required | Contact | Email must exist | Block save |
| Amount Required | Deal | Amount > 0 | Block stage progression |
| Owner Required | All | Owner must be assigned | Auto-assign or block |

---

## Appendix: Object IDs Reference

| Object | Object ID | API Name |
|--------|-----------|----------|
| Contact | `0-1` | `contacts` |
| Company | `0-2` | `companies` |
| Deal | `0-3` | `deals` |
| Ticket | `0-5` | `tickets` |
| Call | `0-48` | `calls` |
| Email | `0-49` | `emails` |
| Meeting | `0-47` | `meetings` |
| Note | `0-46` | `notes` |
| Task | `0-27` | `tasks` |
| Product | `0-7` | `products` |
| Line Item | `0-8` | `line_items` |
| Quote | `0-14` | `quotes` |
| Lead | `0-39` | `leads` |
| Leader | `2-41621067` | Custom |

---

*Document maintained by Data Operations. Last reviewed: January 30, 2026*
