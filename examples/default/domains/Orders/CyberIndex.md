---
# id: GDD-5011 - DataGovernance
## name: Data Governance Event Base Architecture
## version: 0.1.0
owners:
  - Cyber Team
  - GRI Team
  - PACSI Project Team
  - Infra Team
  - governance-team
  - compliance-department
services:
  - id: DataCatalogService
    version: 1.0.0
  - id: DataQualityService
    version: 1.0.0
  - id: DataPrivacyService
    version: 1.0.0
badges:
  - content: New governance process
    backgroundColor: green
    textColor: white
---

import Footer from '@catalog/components/footer.astro';

## Overview

:::warning
Please ensure all services adhere to the latest data governance policies and standards.
:::

The Data Governance process ensures that data is managed properly, compliant with relevant regulations, and of high quality. This documentation provides an overview of the policies, roles, and services involved in the Data Governance process, helping ensure that data is reliable and secure.

<Tiles>
    <Tile icon="ShieldCheckIcon" href="/docs/teams/governance-team" title="Contact the team" description="Any questions? Feel free to contact the governance team" />
    <Tile icon="DatabaseIcon" href={`/visualiser/domains/${frontmatter.id}/${frontmatter.version}`} title={`${frontmatter.services.length} services are involved in this process`} description="These services ensure data governance compliance" />
</Tiles>

## Bounded context

<NodeGraph />

### Data Governance Workflow (sequence diagram)

```mermaid
sequenceDiagram
    participant DataOwner
    participant DataCatalogService
    participant DataQualityService
    participant DataPrivacyService

    DataOwner->>DataCatalogService: Submit Data
    DataCatalogService->>DataQualityService: Validate Data Quality
    DataQualityService-->>DataCatalogService: Data Quality Approved
    DataCatalogService->>DataPrivacyService: Ensure Data Privacy Compliance
    DataPrivacyService-->>DataCatalogService: Privacy Compliance Approved
    DataCatalogService->>DataOwner: Data Submission Successful
    DataCatalogService->>DataRepository: Store Data
