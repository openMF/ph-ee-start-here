# payment-hub-ee

![ Payment Hub - EE](/docs/payment-hub-ee.png) 
[![DPG Badge](https://img.shields.io/badge/Verified-DPG-3333AB?logo=data:image/svg%2bxml;base64,PHN2ZyB3aWR0aD0iMzEiIGhlaWdodD0iMzMiIHZpZXdCb3g9IjAgMCAzMSAzMyIgZmlsbD0ibm9uZSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KPHBhdGggZD0iTTE0LjIwMDggMjEuMzY3OEwxMC4xNzM2IDE4LjAxMjRMMTEuNTIxOSAxNi40MDAzTDEzLjk5MjggMTguNDU5TDE5LjYyNjkgMTIuMjExMUwyMS4xOTA5IDEzLjYxNkwxNC4yMDA4IDIxLjM2NzhaTTI0LjYyNDEgOS4zNTEyN0wyNC44MDcxIDMuMDcyOTdMMTguODgxIDUuMTg2NjJMMTUuMzMxNCAtMi4zMzA4MmUtMDVMMTEuNzgyMSA1LjE4NjYyTDUuODU2MDEgMy4wNzI5N0w2LjAzOTA2IDkuMzUxMjdMMCAxMS4xMTc3TDMuODQ1MjEgMTYuMDg5NUwwIDIxLjA2MTJMNi4wMzkwNiAyMi44Mjc3TDUuODU2MDEgMjkuMTA2TDExLjc4MjEgMjYuOTkyM0wxNS4zMzE0IDMyLjE3OUwxOC44ODEgMjYuOTkyM0wyNC44MDcxIDI5LjEwNkwyNC42MjQxIDIyLjgyNzdMMzAuNjYzMSAyMS4wNjEyTDI2LjgxNzYgMTYuMDg5NUwzMC42NjMxIDExLjExNzdMMjQuNjI0MSA5LjM1MTI3WiIgZmlsbD0id2hpdGUiLz4KPC9zdmc+Cg==)](https://digitalpublicgoods.net/r/mifos-payment-hub-ee-ph-ee)

Payment Hub Enterprise Edition middleware and Payments Orchestration Engine for integration to real-time payment systems. 
Orchestrate & Streamline bulk G2P & P2G payements. Enable seamless participation of DFSPs into payments.

Payment Hub EE supports both DFSP and Government Functions (v1.13.0 awarded GovStack Level 1 Compliance) [ GovStack PH EE Compliance Statement](https://testing.govstack.global/requirements/details/Payment%20Hub%20Enterprise%20Edition%20(PH-EE)).

![ PH EE within the financial ecosystem ](/docs/phee-dpi.png) 

- Connectorised approach allowing for easy payment rail and systems integration.
- BPMN Workflows supported.
- 2 Workflow Engines supported Zeebe or Netflix Conductor (DPG core)

The solution is a multi repo approach supporting modularity.

![ PH EE key features ](/docs/phee-overview.png) 

> **_v2.0 coming soon_** will further workflow abstraction, reduce the number of repos whilst maintaining modularity and update dependencies. Note for v2.0 the following repo naming will be used: `paymenthub-ee-*` to differentiate the major version.

---

## Repository Structure for Modularity

### Core / Orchestration

[ph-ee-start-here](https://github.com/openMF/ph-ee-start-here) – Landing/meta repo with the overview docs for the whole multi-repo solution (this repo).  
[ph-ee-dpg-core](https://github.com/openMF/ph-ee-dpg-core)– DPG-compliant orchestration engine built on Netflix Conductor (alternative to the Zeebe-based flow).  
[ph-ee-dpg-template](https://github.com/openMF/ph-ee-dpg-template) – Starter template for building components on the Conductor/DPG-core architecture.  
[ph-ee-exporter](https://github.com/openMF/ph-ee-exporter) – Zeebe exporter that streams workflow engine events into Kafka.  
[ph-ee-zeebe-ops](https://github.com/openMF/ph-ee-zeebe-ops) – Microservice for fetching, modifying, and starting Zeebe BPMN process instances.  
[ph-ee-k8s-operators](https://github.com/openMF/ph-ee-k8s-operators) – Kubernetes Operators for deploying/managing PH-EE components.  

### Connectors (integration to payment rails, core banking, AMS)

[ph-ee-connector-common](https://github.com/openMF/ph-ee-connector-common) – Shared code/artifacts reused across the Java connectors.  
[ph-ee-connector-channel](https://github.com/openMF/ph-ee-connector-channel) – Front-door connector that receives requests from client channels.  
[ph-ee-connector-bulk](https://github.com/openMF/ph-ee-connector-bulk) – Closed-loop bulk payment connector.  
[ph-ee-connector-mojaloop-java](https://github.com/openMF/ph-ee-connector-mojaloop-java) – Connector to the Mojaloop Switch scheme.  
[ph-ee-connector-gsma-mm](https://github.com/openMF/ph-ee-connector-gsma-mm)– Connector for the GSMA Mobile Money API.  
[ph-ee-connector-gsma-mm-dpg](https://github.com/openMF/ph-ee-connector-gsma-mm-dpg) – DPGA-compliant variant of the GSMA MM connector using Netflix Conductor workflow.  
[ph-ee-connector-mpesa](https://github.com/openMF/ph-ee-connector-mpesa) – Connector for Safaricom M-Pesa.  
[ph-ee-connector-mccbs](https://github.com/openMF/ph-ee-connector-mccbs) – Connector to Mastercard Cross-Border Services (currently demo/non-production).  
[ph-ee-connector-slcb](https://github.com/openMF/ph-ee-connector-slcb) – Connector integrating with SLCB.  
[ph-ee-connector-pch-java](https://github.com/openMF/ph-ee-connector-pch-java) – Connector for a Payment Clearing House integration (gRPC based).  
[ph-ee-connector-crm](https://github.com/openMF/ph-ee-connector-crm) – CRM-facing connector microservice.  
[ph-ee-connector-mock-payment-schema](https://github.com/openMF/ph-ee-connector-mock-payment-schema) – Mock payment-scheme connector for testing transfers without a real rail.  
[ph-ee-connector-ams-mifos](https://github.com/openMF/ph-ee-connector-ams-mifos) – Account Management System (AMS) connector for MifosX core banking.  
[ph-ee-connector-ams-pesa](https://github.com/openMF/ph-ee-connector-ams-pesa) – AMS connector for a Pesa-type core banking system.  
[ph-ee-connector-ams-paygops](https://github.com/openMF/ph-ee-connector-ams-paygops)  – AMS connector for the PayGOps platform.  

### Operations, UI & Monitoring

[ph-ee-operations-app](https://github.com/openMF/ph-ee-operations-app) – Operations web app backend for monitoring/managing transactions and workflows.  
[ph-ee-operations-web](https://github.com/openMF/ph-ee-operations-web) – Front-end for the Operations web app (original in Angular).  
[ph-ee-operations-web-react](https://github.com/openMF/ph-ee-operations-web-react) – React-based front-end for Operations (modernized replacement in React ShadCN).  
[ph-ee-operations-g2p-service](https://github.com/openMF/ph-ee-operations-g2p-service) – Spring Boot service supporting Government-to-Person (G2P) operations API endpoints and configuration of programs.  

### Data pipeline / Importers

[ph-ee-importer-es](https://github.com/openMF/ph-ee-importer-es) – Consumes Kafka events and indexes Zeebe workflow data into Elasticsearch.  
[ph-ee-importer-rdbms](https://github.com/openMF/ph-ee-importer-rdbms) – Consumes Kafka events and writes business data to an off-site RDBMS.  
[ph-ee-nats-importer-rdbms](https://github.com/openMF/ph-ee-nats-importer-rdbms) – Same as above but consuming from NATS instead of Kafka.  

### Identity & Account Mapping

[ph-ee-identity-account-mapper](https://github.com/openMF/ph-ee-identity-account-mapper) – Maps external identities to account details for payment routing.  
[ph-ee-id-account-validator-impl](https://github.com/openMF/ph-ee-id-account-validator-impl) – Account validator implementations used by the identity mapper.  
[ph-ee-identity-provider](https://github.com/openMF/ph-ee-identity-provider) – Identity/auth provider service for PH-EE.  

### Supporting services

[ph-ee-notifications](https://github.com/openMF/ph-ee-notifications) – Notification delivery, works with the separate message-gateway project.  
[ph-ee-vouchers](https://github.com/openMF/ph-ee-vouchers) – Voucher management/issuance system.  
[ph-ee-bill-pay](https://github.com/openMF/ph-ee-bill-pay) – Bill payment processing microservice (P2G).  
[ph-ee-bulk-processor](https://github.com/openMF/ph-ee-bulk-processor)  – Bulk/batch transaction processing microservice (G2P).  
[ph-ee-acknowledgement](https://github.com/openMF/ph-ee-acknowledgement) – Placeholder repo for an acknowledgement service (README only, no code yet).  

### Testing & QA

[ph-ee-testing-toolkit](https://github.com/openMF/ph-ee-testing-toolkit) – Functional testing toolkit for PH-EE development/QA.  
[ph-ee-testing-toolkit-ui](https://github.com/openMF/ph-ee-testing-toolkit-ui) – Experimental UI for the testing toolkit.  
[ph-ee-integration-test](https://github.com/openMF/ph-ee-integration-test) – Integration-test microservice for end-to-end flows.  
[ph-ee-ai-arch-test](https://github.com/openMF/ph-ee-ai-arch-test) – Experimental AI-driven architecture testing.  

### Environment / Deployment

[ph-ee-env-template](https://github.com/openMF/ph-ee-env-template) – Template environment/deployment configs.  
[ph-ee-env-labs](https://github.com/openMF/ph-ee-env-labs) – Actual lab environment configs — BPMN flows and Helm charts for a live lab deployment.  

For detailed documentation check the documentation: https://app.gitbook.com/@mifos/s/docs/payment-hub-ee/overview

