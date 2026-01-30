# Ministry SaaS CRM

## HubSpot CRM Implementation for B2B SaaS Ministry Platform

This repository contains comprehensive HubSpot CRM documentation, configuration exports, and implementation guides for the Ministry SaaS platform targeting churches, parachurches, media ministries, and faith-based content creators.

---

## Documentation Index

### Core Documentation

| Document | Description |
|----------|-------------|
| [HubSpot CRM Documentation](hubspot_crm_documentation.md) | Comprehensive B2B SaaS CRM guide covering all aspects of the implementation |
| [Data Model Documentation](data_model_documentation.md) | Object relationships, schema, and data architecture |
| [Property Dictionary](property_dictionary.md) | Quick reference for key properties across all objects |
| [Lead Scoring Framework](lead_scoring_documentation.md) | Complete lead scoring model (-2,000 to +2,000 points) |
| [Lead Scoring AE Summary](lead_scoring_ae_summary.md) | Quick reference guide for Account Executives |

### Marketing & Segmentation Documentation

| Document | Description |
|----------|-------------|
| [Marketing Dashboards](marketing_dashboards.md) | Marketing mix dashboard framework with report specifications |
| [Database Segmentation Strategy](database_segmentation_strategy.md) | Master segments: Ministry SaaS prospects, Ads prospects, Current Leaders |
| [Campaign Nurture Playbook](campaign_nurture_playbook.md) | Complete nurture campaign framework with email sequences |

### HubSpot Exports

#### Property Exports (CSV)
| Object | File | Properties |
|--------|------|------------|
| Contact | [contact.csv](contact.csv) | 412 |
| Company | [company.csv](company.csv) | 296 |
| Deal | [deal.csv](deal.csv) | 597 |
| Lead | [lead.csv](lead.csv) | 187 |
| Leader (Custom) | [leader-2-41621067.csv](leader-2-41621067.csv) | 212 |

#### Activity & Marketing Exports
| Object | File |
|--------|------|
| Call | [call.csv](call.csv) |
| Meeting | [meeting.csv](meeting.csv) |
| Campaign | [campaign.csv](campaign.csv) |
| Marketing Event | [marketing-event.csv](marketing-event.csv) |
| Marketing Email | [marketing-email.csv](marketing-email.csv) |
| SMS Message | [sms-message.csv](sms-message.csv) |

#### Operational Exports
| Object | File |
|--------|------|
| Workflow | [workflow.csv](workflow.csv) |
| Project | [project.csv](project.csv) |
| Product | [product.csv](product.csv) |
| Line Item | [line-item.csv](line-item.csv) |
| Quote | [quote.csv](quote.csv) |
| Invoice | [invoice.csv](invoice.csv) |
| User | [user.csv](user.csv) |
| Segment List | [segment-list.csv](segment-list.csv) |

#### Workflow Documentation
| File | Description |
|------|-------------|
| [workflow.csv](workflow.csv) | Workflow properties export |
| [hubspot-listing-lib-exports-all-workflows-2026-01-30.xlsx](hubspot-listing-lib-exports-all-workflows-2026-01-30.xlsx) | Complete workflow export with details |

### Visual Documentation (Screenshots)
The repository includes 47 screenshot files documenting:
- Contact interface and record views
- Company interface and record views
- Deal management screens
- Lead tracking views
- Leader (custom object) tracking

---

## Quick Start Guide

### For Sales Team (AEs)
1. Start with [Lead Scoring AE Summary](lead_scoring_ae_summary.md) for quick reference
2. Review [Property Dictionary](property_dictionary.md) for key fields

### For Marketing Team
1. Read [Database Segmentation Strategy](database_segmentation_strategy.md) to understand the three master segments
2. Review [Campaign Nurture Playbook](campaign_nurture_playbook.md) for nurture campaign templates
3. Use [Marketing Dashboards](marketing_dashboards.md) to build performance reports

### For Operations/Admin
1. Read [HubSpot CRM Documentation](hubspot_crm_documentation.md) for full overview
2. Review [Data Model Documentation](data_model_documentation.md) for relationships

### For Data/Technical Team
1. Study [Data Model Documentation](data_model_documentation.md) for schema details
2. Reference CSV exports for complete property lists
3. Review [Property Dictionary](property_dictionary.md) for naming conventions

---

## CRM Architecture Overview

```
+------------------+     +------------------+     +------------------+
|     CONTACT      |<--->|     COMPANY      |<--->|      DEAL        |
|   412 properties |     |   296 properties |     |   597 properties |
+--------+---------+     +--------+---------+     +--------+---------+
         |                        |                        |
         v                        v                        v
+--------+---------+     +--------+---------+     +--------+---------+
|       LEAD       |     |     LEADER       |     |    LINE ITEM     |
|   187 properties |     |   212 properties |     |    71 properties |
+------------------+     +------------------+     +------------------+
```

---

## Key CRM Features

### Ideal Customer Profile (ICP)
- **ICP 1**: Mega-churches, Multi-campus, Media Ministries
- **ICP 2**: Media Ministries, Faith-based Shows
- **ICP 3**: Growth-Stage, Digital-Forward Churches
- **IPP**: Agency/Network Partners

### Company Segmentation
| Segment | Revenue Range |
|---------|---------------|
| Whale | >$5 million |
| Elephant | $3M - $5M |
| Deer | $1M - $3M |
| Rabbit | $500K - $1M |
| Mouse | <$500K |

### Lead Scoring Range
- **Hot Leads**: 1,000 - 2,000 points
- **Warm Leads**: 500 - 999 points
- **Developing**: 100 - 499 points
- **Cold**: 0 - 99 points
- **Disqualified**: -2,000 to -1 points

### Lifecycle Stages
```
Subscriber → Lead → MQL → SQL → Opportunity → Customer → Churned
```

---

## Repository Structure

```
ministrySaaSCRM/
├── README.md                           # This file
├── hubspot_crm_documentation.md        # Main CRM documentation
├── data_model_documentation.md         # Data model & relationships
├── property_dictionary.md              # Property quick reference
├── lead_scoring_documentation.md       # Lead scoring framework
├── lead_scoring_ae_summary.md          # AE quick reference
├── marketing_dashboards.md             # Marketing mix dashboards
├── database_segmentation_strategy.md   # Master segment definitions
├── campaign_nurture_playbook.md        # Nurture campaign templates
├── *.csv                               # HubSpot property exports
├── *.xlsx                              # Workflow exports
├── *.png                               # Interface screenshots
└── MARK-*.pdf                          # Internal documentation PDFs
```

---

## PDF Documentation Reference

| Document | Description |
|----------|-------------|
| MARK-Hubspot Fields Documentation | Detailed field definitions |
| MARK-CRM Structure Guidelines | CRM architecture and best practices |
| MARK-Data Model & Enablement | Data schema and team enablement |
| MARK-Lead Qualification Framework | Qualification criteria |
| MARK-Acquisition Journey Matrix | Customer acquisition paths |
| MARK-Data Governance | Data policies and compliance |
| MARK-Data Enrichment | Data enrichment strategies |
| MARK-Onboarding | Customer onboarding processes |
| MARK-Contact Marketing Status and GDPR | Marketing compliance |

---

## Maintenance

| Item | Frequency | Owner |
|------|-----------|-------|
| Property exports refresh | Monthly | Data Ops |
| Lead scoring review | Quarterly | Growth Ops |
| Documentation updates | As needed | CRM Admin |
| Workflow audit | Quarterly | Data Ops |

---

## Contact

For questions about this CRM implementation:
- **CRM Administrator**: Growth Operations Team
- **Data Operations**: Data Ops Team
- **Sales Operations**: Rev Ops Team

---

*Last Updated: January 30, 2026*
