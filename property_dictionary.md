# Ministry SaaS HubSpot Property Dictionary

## Quick Reference Guide for Key Properties

**Version:** 1.0
**Last Updated:** January 30, 2026
**Owner:** Data Operations

---

## Table of Contents

1. [Contact Properties](#contact-properties)
2. [Company Properties](#company-properties)
3. [Deal Properties](#deal-properties)
4. [Lead Properties](#lead-properties)
5. [Ministry-Specific Properties](#ministry-specific-properties)
6. [Attribution Properties](#attribution-properties)
7. [Scoring Properties](#scoring-properties)

---

## Contact Properties

### Identification & Core

| Display Name | Internal Name | Type | Description | Form Field |
|--------------|---------------|------|-------------|------------|
| Email | `email` | string | Primary email address | Yes |
| First Name | `firstname` | string | Contact first name | Yes |
| Last Name | `lastname` | string | Contact last name | Yes |
| Phone Number | `phone` | string | Primary phone | Yes |
| Mobile Phone Number | `mobilephone` | string | Mobile number | Yes |
| Company Name | `company` | string | Company name (separate from association) | Yes |
| Website URL | `website` | string | Contact's company website | Yes |
| Job Title | `jobtitle` | string | Free-text job title | Yes |
| Job Title (dropdown) | `job_title____` | enumeration | Standardized job role | Yes |

### Job Title Dropdown Options
```
- Senior Pastor/Lead Pastor
- Executive Leadership (Executive/Associate Pastor, C-Suite)
- Communications/Media Director
- Content Creator/Host/Speaker
- Operations/Admin Leadership
- Other Ministry Staff
- Other - Government
```

### Location

| Display Name | Internal Name | Type | Description |
|--------------|---------------|------|-------------|
| Street Address | `address` | string | Full street address |
| City | `city` | string | City of residence |
| State/Region | `state` | string | State or region |
| Country/Region | `country` | string | Country |
| Postal Code | `zip` | string | ZIP/postal code |
| Time Zone | `hs_timezone` | enumeration | Contact timezone |

### Contact Classification

| Display Name | Internal Name | Type | Options |
|--------------|---------------|------|---------|
| Contact Type | `contact_type` | enumeration | Leader, Investor, Partner, Vendor, Supporter, Organization, Press, Evangelist |
| Lifecycle Stage | `lifecyclestage` | enumeration | Subscriber, Lead, MQL, SQL, Opportunity, Customer, Other |

### Analytics (Auto-populated)

| Display Name | Internal Name | Type | Description |
|--------------|---------------|------|-------------|
| Original Source Type | `hs_analytics_source` | enumeration | First traffic source |
| Original Source Data 1 | `hs_analytics_source_data_1` | string | Source detail |
| Original Source Data 2 | `hs_analytics_source_data_2` | string | Additional detail |
| First Page Seen | `hs_analytics_first_url` | string | First URL visited |
| Time First Seen | `hs_analytics_first_timestamp` | datetime | First website visit |
| Average Pageviews | `hs_analytics_average_page_views` | number | Avg pages per session |

### Company Sync Properties (Calculated)

| Display Name | Internal Name | Source | Description |
|--------------|---------------|--------|-------------|
| Company Segment | `company_segment` | Company | Whale, Elephant, Deer, Rabbit, Mouse |
| Company Type | `company_type__from_associated_company_` | Company | Organization type |
| ICP Tier | `icp_tier__from_associated_company_` | Company | ICP classification |
| Lead Pipeline Stage | `lead_pipeline_stage` | Lead | Current lead stage |
| Associated Company Record ID | `associated_company_record_id` | Company | Company ID |

---

## Company Properties

### Identification & Core

| Display Name | Internal Name | Type | Required | Unique |
|--------------|---------------|------|----------|--------|
| Company Name | `name` | string | Yes | No |
| Company Domain Name | `domain` | string | Yes | Yes |
| Website URL | `website` | string | Yes | Yes |
| Phone Number | `phone` | string | No | No |

### Location

| Display Name | Internal Name | Type | Description |
|--------------|---------------|------|-------------|
| Street Address | `address` | string | Primary address |
| Street Address 2 | `address2` | string | Additional address |
| City | `city` | string | City location |
| State/Region | `state` | string | State or region |
| Country/Region | `country` | string | Country |
| Postal Code | `zip` | string | ZIP/postal code |
| Time Zone | `timezone` | string | Company timezone |

### Classification

| Display Name | Internal Name | Type | Options |
|--------------|---------------|------|---------|
| Company Type | `company_type` | enumeration | Church (Mega Church), Parachurch organization, Media Ministry, Podcast (Podcaster), Nonprofit, Agency, Competitor, Media Channel, Broadcasting platform, Social Network, Ads Agency, Other |
| Company Segment | `company_segment` | enumeration | Whale, Elephant, Deer, Rabbit, Mouse, Unknown |
| ICP Tier | `icp_tier` | enumeration | ICP 1, ICP 2, ICP 3, IPP |
| Industry | `industry` | enumeration | Standard HubSpot industries |

### Firmographics

| Display Name | Internal Name | Type | Description |
|--------------|---------------|------|-------------|
| Annual Revenue | `annualrevenue` | number | Estimated annual revenue |
| Revenue Range | `hs_revenue_range` | string | Revenue bracket |
| Number of Employees | `numberofemployees` | number | Employee count |
| Is Public | `is_public` | boolean | Publicly traded |
| Total Open Deal Value | `hs_total_deal_value` | number | Sum of open deals |
| Total Revenue | `total_revenue` | number | Lifetime closed-won |

### Ministry-Specific (Company)

| Display Name | Internal Name | Type | Description |
|--------------|---------------|------|-------------|
| Church Size (Attendance) | `church_size_attendance` | enumeration | Congregation size |
| Number of Locations | `number_of_locations` | number | Campus count |
| Distribution Channels | `distribution_channels` | enumeration | Content distribution methods |
| Growth Priorities | `growth_priorities` | enumeration | Strategic priorities |
| Primary Challenge | `primary_challenge` | enumeration | Key pain point |
| Timeline for Solution | `timeline_for_a_solution` | enumeration | Purchase timeline |
| Data Mining Complete | `data_mining_complete` | boolean | Research completed |

---

## Deal Properties

### Revenue Information

| Display Name | Internal Name | Type | Description |
|--------------|---------------|------|-------------|
| Amount | `amount` | number | Total deal value |
| Amount in Company Currency | `amount_in_home_currency` | number | Converted amount |
| Annual Contract Value | `hs_acv` | number | Yearly value |
| Total Contract Value | `hs_tcv` | number | Full contract value |
| Exchange Rate | `hs_exchange_rate` | number | Currency conversion |

### Qualification

| Display Name | Internal Name | Type | Description |
|--------------|---------------|------|-------------|
| Deal Name | `dealname` | string | Deal title |
| Pipeline | `pipeline` | enumeration | Sales pipeline |
| Deal Stage | `dealstage` | enumeration | Current stage |
| Close Date | `closedate` | datetime | Expected close |
| Deal Probability | `hs_deal_stage_probability` | number | Close probability |
| Forecast Amount | `hs_forecast_amount` | number | Weighted amount |
| Forecast Category | `hs_manual_forecast_category` | enumeration | Pipeline, Best Case, Commit |
| Days to Close | `days_to_close` | number | Sales cycle length |

### Closed Reasons

| Display Name | Internal Name | Options |
|--------------|---------------|---------|
| Closed Won Reason | `closed_won_reason__dropdown_` | Actionable Insights, Competitive Pricing, Content Preservation, Digital Legacy, FOMO, Global Reach, Limitless Accessibility, Local Focus, Ongoing Account Management, Standard of Excellence, Donors |
| Closed Lost Reason | `closed_lost_reason__dropdown_` | Not Qualified, Went Dark, Timing, Budget, Feature Gap, Lost to Competitor, Cancelled Evaluation, BDR - No Show, Other, No Local Focus |
| Closed Lost - Budget | `closed_lost___budget` | Not ICP, Spending elsewhere, Too expensive, Lack of Belief |

### Associations (Calculated)

| Display Name | Internal Name | Source | Description |
|--------------|---------------|--------|-------------|
| Associated Agency Company | `associated_agency_company_name` | Company (Agency label) | Partner agency |
| Associated Billing Contact | `associated_billing_contact_email` | Contact (Billing label) | Billing email |
| Associated Key Manager | `associated_key_manager_email` | Contact (Key Manager label) | Champion |
| Associated Leader Name | `associated_leader_name` | Leader | Content creator |
| Associated Contact Record ID | `associated_contact_record_id` | Contact | Primary contact ID |

### Source Tracking

| Display Name | Internal Name | Type | Description |
|--------------|---------------|------|-------------|
| Pray Source | `pray_source` | enumeration | Lead source (Conference, Referral, Agency, etc.) |
| Channel Attribution | `channel_attribution` | enumeration | Marketing vs. Sales |
| Marketing Attribution | `first_touch_marketing_attribution` | enumeration | First conversion type |
| Marketing Attribution Drill-Down | `first_touch_marketing_attribution_drill_down` | enumeration | Specific event/source |
| Linear Touch Attribution | `linear_touch_marketing_attribution` | enumeration | Ongoing attribution |

---

## Lead Properties

### Identification

| Display Name | Internal Name | Type | Description |
|--------------|---------------|------|-------------|
| Lead Name | `hs_lead_name` | string | Full lead name |
| Lead Label | `hs_lead_label` | enumeration | Hot, Warm, Cold |
| Lead Source | `hs_lead_source` | enumeration | Traffic source |
| Company Domain | `company_domain` | string | Associated domain |
| Associated Contact Email | `associated_contact_email` | string | Contact email |
| Associated Contact Phone | `associated_contact_phone_number` | string | Contact phone |

### Pipeline Stage

| Display Name | Internal Name | Options |
|--------------|---------------|---------|
| Pipeline Stage | `hs_lead_pipeline_stage` | New, Attempting, Connected, Qualified, Disqualified |

### Disqualification

| Display Name | Internal Name | Options |
|--------------|---------------|---------|
| Disqualification Reason | `hs_lead_disqualification_reason` | Bad Timing, Budget Constraints, No Decision-making Power, Competitor Preference, Not a Good Fit, No Commercial Interest, Prior Negative Experience, Technical Limitations, Wrong Data, No Response, Smaller than Deer |
| Disqualification Note | `hs_lead_disqualification_note` | Free-text explanation |

### Activity Metrics (Calculated)

| Display Name | Internal Name | Type | Description |
|--------------|---------------|------|-------------|
| Call Count | `hs_lead_call_count` | number | Total calls made |
| Email Count | `hs_lead_email_count` | number | Total emails sent |
| Meeting Count | `hs_lead_meeting_count` | number | Meetings booked |
| Message Thread Count | `hs_lead_communication_count` | number | SMS, LinkedIn, WhatsApp |
| Outreach Activity Count | `hs_lead_outreach_activity_count` | number | Total outreach |
| First Outreach Date | `hs_lead_first_outreach_date` | datetime | Initial contact |

### Associated Data (Calculated)

| Display Name | Internal Name | Type | Description |
|--------------|---------------|------|-------------|
| Associated Deals Count | `hs_lead_associated_deals_count` | number | Number of deals |
| Open Deal Amount | `hs_lead_pipeline_value` | number | Open deal value |
| Closed Won Deal Amount | `hs_lead_closed_won_deals_amount` | number | Won deal value |
| Company Name | `hs_associated_company_name` | string | Company name |

---

## Ministry-Specific Properties

### Distribution Channels

| Property | Object | Options |
|----------|--------|---------|
| Distribution Channels | Company/Contact | Christian TV networks, Christian radio networks, Custom mobile app, Email marketing platform, Podcast hosting/distribution, Satellite radio, Streaming TV platforms, Church website with video, YouTube advertising, Just getting started, Free platforms only |

### Content Metrics

| Property | Object | Type | Description |
|----------|--------|------|-------------|
| Monthly Listeners/Viewers | Company | enumeration | Audience reach brackets |
| Content Production Volume | Company | enumeration | Daily, Weekly, Monthly, Occasional |
| Podcast Presence | Company | boolean | Has active podcast |
| Instagram Followers | Company | number | Social following |

### Growth Priorities Options
```
- Reaching more people beyond our current audience
- Expanding to new platforms
- Going global with translated content
- Automating content workflows and reducing manual work
- Consolidating multiple tools into one platform
- Getting our team out of admin tasks and back to ministry
- Improving member and donor engagement
- Building or improving our mobile app
- Creating recurring touchpoints with our audience
- Growing our donor base and recurring giving
- Proving ROI on our content and media spend
- Monetizing our content or audience
- Understanding who's watching/listening and how they engage
- Tracking content performance across all platforms
- Connecting media exposure to attendance and giving
- Pricing and partnership options
- Not actively growing right now, just staying informed
```

### Primary Challenge Options
```
- Limited reach beyond the local congregation
- Manual content distribution is taking too much time
- Lack of audience insights and analytics
- Difficulty monetizing digital content
- Need better donor engagement tools
- Want to reach a younger/global audience
```

---

## Attribution Properties

### Original Source (First Touch)

| Display Name | Internal Name | Object | Options |
|--------------|---------------|--------|---------|
| Original Source Type | `hs_analytics_source` | Contact, Company, Deal | Organic Search, Paid Search, Email Marketing, Organic Social, Referrals, Other Campaigns, Direct Traffic, Offline Sources, Paid Social |
| Original Source Data 1 | `hs_analytics_source_data_1` | Contact, Company, Deal | Varies by source |
| Original Source Data 2 | `hs_analytics_source_data_2` | Contact, Company, Deal | Varies by source |

### Latest Source

| Display Name | Internal Name | Object | Description |
|--------------|---------------|--------|-------------|
| Latest Source | `hs_analytics_latest_source` | Contact, Company, Deal | Most recent traffic source |
| Latest Source Data 1 | `hs_analytics_latest_source_data_1` | Contact, Company, Deal | Latest source detail |
| Latest Source Data 2 | `hs_analytics_latest_source_data_2` | Contact, Company, Deal | Additional detail |

### Marketing Attribution (Custom)

| Display Name | Internal Name | Object | Description |
|--------------|---------------|--------|-------------|
| Marketing Attribution | `linear_touch_marketing_attribution` | Company | Initial marketing channel |
| First Touch Marketing Attribution | `first_touch_marketing_attribution` | Deal | First conversion source |
| Marketing Attribution Drill-Down | `first_touch_marketing_attribution_drill_down` | Deal | Specific event/campaign |
| Channel Attribution | `channel_attribution` | Deal | Marketing vs. Sales |

### Event Attribution Drill-Down Options
```
Digital Outreach:
- 1:1 Instagram Outreach

Live Events:
- NRB 2024, NRB 2025
- C3 Conference 2024, C3 Conference 2025
- Exponential 2024, Exponential 2025
- Dunham Summit 2024, Dunham Summit 2025
- Spire 2024, Spire 2025
- SBC 2024, SBC 2025
- RightNow Media Conference 2024, 2025
- Pastor Retreats (Multiple dates)
- Golf Events
- Amen Conference
- BCI (Black Christian Influencers)
- Christian Mental Health Summit
- For Others Event
- And more...

Paid Advertising:
- LinkedIn
- Meta
- Search

Website Organic:
- Search, Direct, Email, Referrals, Social
```

---

## Scoring Properties

### HubSpot Score Properties

| Display Name | Internal Name | Object | Description |
|--------------|---------------|--------|-------------|
| Product Market Fit (Total) | `combined_score_*_total` | Company | Combined fit + engagement |
| Size and Growth Signals (Fit) | `combined_score_*_fit` | Company | Firmographic score |
| Buying Intent (Engagement) | `combined_score_*_engagement` | Company | Behavioral score |
| Product Market Fit Thresholds | `combined_score_*_threshold` | Company | A1-C3 matrix position |

### Score Threshold Matrix

| Threshold | Fit Score | Engagement Score | Interpretation |
|-----------|-----------|------------------|----------------|
| A1 | High | High | Best fit, highly engaged |
| A2 | High | Medium | Best fit, moderate engagement |
| A3 | High | Low | Best fit, needs nurturing |
| B1 | Medium | High | Good fit, highly engaged |
| B2 | Medium | Medium | Good fit, moderate engagement |
| B3 | Medium | Low | Good fit, needs nurturing |
| C1 | Low | High | Poor fit, highly engaged |
| C2 | Low | Medium | Poor fit, moderate engagement |
| C3 | Low | Low | Poor fit, low engagement |

### Lead Scoring Categories

See `lead_scoring_documentation.md` for complete scoring criteria.

| Category | Points Range | Properties Evaluated |
|----------|--------------|---------------------|
| Firmographics | -50 to +50 | Company type, revenue, employees, locations, church size |
| Contact Quality | 0 to +25 | Job title, verification status |
| Growth Signals | -20 to +70 | Distribution, social, podcast, content, technology |
| Buying Intent | -55 to +100+ | Forms, email, calls, meetings, events |
| Sales Qualification | -85 to +200+ | Timeline, budget, decision-maker, urgency, fit |

---

## Property Naming Conventions

### Standard Prefixes

| Prefix | Meaning | Example |
|--------|---------|---------|
| `hs_` | HubSpot system property | `hs_analytics_source` |
| `associated_` | Calculated from association | `associated_leader_name` |
| `hs_v2_` | Lifecycle stage tracking | `hs_v2_date_entered_lead` |

### Standard Suffixes

| Suffix | Meaning | Example |
|--------|---------|---------|
| `__from_associated_company_` | Synced from company | `icp_tier__from_associated_company_` |
| `_dropdown_` | Standardized dropdown | `closed_won_reason__dropdown_` |
| `_drill_down` | Detailed attribution | `first_touch_marketing_attribution_drill_down` |
| `_timestamp` | Date/time value | `hs_analytics_first_timestamp` |
| `_count` | Numeric count | `hs_lead_call_count` |

---

## Property Export Files

For complete property lists, refer to the CSV exports:

| Object | File | Property Count |
|--------|------|----------------|
| Contact | `contact.csv` | 412 |
| Company | `company.csv` | 296 |
| Deal | `deal.csv` | 597 |
| Lead | `lead.csv` | 187 |
| Leader | `leader-2-41621067.csv` | 212 |
| Workflow | `workflow.csv` | 47 |

---

*Property Dictionary maintained by Data Operations. For additions or changes, submit a CRM change request.*
