# CST8917 – Serverless Applications

## Assignment 2 – Serverless Service Alternatives Report

**St: Olga Durham**

**St#: 040687883**

---

## 1. Required Azure Services to Compare

At a minimum, your report must include the following Azure services:

- **Azure Functions** (Triggers & Bindings)
- **Durable Functions** (Chaining, Orchestration, Fan-out/Fan-in)
- **Azure Logic Apps**
- **Azure Service Bus** (Queues & Topics)
- **Azure Event Grid**
- **Azure Event Hubs**

_(You may include additional Azure services from the course if relevant.)_

---

## 2. Identifying the closest AWS/GCP Equivalents

| Azure                                                       | AWS                                                                | GCP                                                                                   |
| :---------------------------------------------------------- | :----------------------------------------------------------------- | :------------------------------------------------------------------------------------ |
| Azure Functions (Triggers & Bindings)                       | AWS lambda                                                         | Cloud Run Functions                                                                   |
| Durable Functions (Chaining, Orchestration, Fan-out/Fan-in) | AWS Step Functions                                                 | Google Cloud Workflows                                                                |
| Azure Logic Apps                                            | AWS Step Functions (closest for workflow automation/orchestration) | Application Integration (closest low-code integration service)                        |
| Azure Service Bus (Queues & Topics)                         | Amazon SQS + Amazon SNS                                            | Pub/Sub                                                                               |
| Azure Event Grid                                            | Amazon EventBridge                                                 | Eventarc                                                                              |
| Azure Event Hubs                                            | Amazon Kinesis Data Streams                                        | Pub/Sub (or Pub/Sub Lite if you want to emphasize partitioned, high-volume streaming) |

---

## 3. Comparing the Services

For each service, include:

- **Overview** – brief description of each service
- **Core Features** – supported triggers, bindings, messaging/eventing capabilities
- **Integration Options** – how it works with other cloud services or CI/CD pipelines
- **Monitoring & Observability** – available tools/logging integrations
- **Pricing Model** – high-level cost considerations
- **Strengths & Weaknesses** – from a serverless architecture perspective

### Comparison Tables

---

#### Azure Functions vs AWS Lambda vs GCP Cloud Run functions

| Criteria          | Azure Functions                                           | AWS Lambda                                                | Cloud Run functions                                                |
| ----------------- | --------------------------------------------------------- | --------------------------------------------------------- | ------------------------------------------------------------------ |
| **Overview**      | Event-driven serverless compute using triggers & bindings | Event-driven compute tightly integrated with AWS services | Serverless functions running on Cloud Run with event/HTTP triggers |
| **Core Features** | Triggers + bindings simplify input/output handling        | Event source mappings and wide AWS integrations           | HTTP + event-driven (via Eventarc/Pub/Sub)                         |
| **Integration**   | Strong Azure integrations via bindings                    | Deep AWS ecosystem (S3, SQS, API Gateway)                 | Integrates with Cloud Run, Eventarc, Pub/Sub                       |
| **Monitoring**    | Azure Monitor + Application Insights                      | CloudWatch + X-Ray                                        | Cloud Logging + Monitoring                                         |
| **Pricing**       | Pay per execution + consumption                           | Pay per request + duration                                | Pay per use (Cloud Run-based)                                      |
| **Strengths**     | Easy integration, less boilerplate                        | Mature ecosystem, flexible                                | Modern event model, Cloud Run alignment                            |
| **Weaknesses**    | Azure-specific model                                      | Can require multiple services                             | Less unified, more setup across services                           |

**Narrative Analysis**

Azure Functions, AWS Lambda, and Cloud Run functions all provide serverless compute but differ in approach.

Azure Functions uses a **trigger and binding model**, simplifying integrations and reducing boilerplate, making it ideal for rapid Azure development. AWS Lambda is more **ecosystem-driven**, offering flexibility but requiring multiple services. Cloud Run functions is **modern and flexible**, but less centralized due to reliance on Cloud Run and Eventarc.

Overall, **Azure Functions favors simplicity, Lambda favors flexibility**, and **Cloud Run functions favors modern architecture**.

---

#### Durable Functions vs AWS Step Functions vs GCP Workflows

| Criteria          | Durable Functions                                                     | AWS Step Functions                                                      | Google Cloud Workflows                                              |
| ----------------- | --------------------------------------------------------------------- | ----------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **Overview**      | Extension of Azure Functions for stateful workflows and orchestration | Serverless workflow orchestration service for coordinating AWS services | Managed workflow orchestration service for GCP services and APIs    |
| **Core Features** | Orchestrations, chaining, fan-out/fan-in, state management            | Visual workflows, state machines, error handling, retries               | YAML/JSON-defined workflows, sequencing, retries, API orchestration |
| **Integration**   | Works with Azure Functions and other Azure services                   | Deep integration with AWS services (Lambda, SQS, SNS, etc.)             | Integrates with GCP services and REST APIs                          |
| **Monitoring**    | Application Insights + Azure Monitor                                  | CloudWatch + Step Functions visual monitoring                           | Cloud Logging + Monitoring                                          |
| **Pricing**       | Based on executions and resource usage                                | Based on state transitions                                              | Based on workflow steps and execution time                          |
| **Strengths**     | Code-first orchestration, tight Azure integration                     | Visual workflows, highly scalable, mature                               | Simple syntax, strong API orchestration                             |
| **Weaknesses**    | Tied to Azure Functions, less visual                                  | Can become complex with large workflows                                 | Less feature-rich than AWS/Azure                                    |

**Narrative Analysis**

Durable Functions, AWS Step Functions, and Google Cloud Workflows all enable serverless workflow orchestration but differ in approach.

Durable Functions is **code-first**, offering flexibility and built-in patterns like fan-out/fan-in, making it ideal for developer-driven solutions in Azure. AWS Step Functions is **visual and state-machine-based**, making workflows easier to manage at scale but sometimes complex. Google Cloud Workflows is **simpler and configuration-based**, best suited for API orchestration but less feature-rich.

Overall, **Durable Functions favors flexibility, Step Functions favors scalability and visibility**, and **Workflows favors simplicity**.

---

#### Azure Logic Apps vs AWS Step Functions vs GCP Application Integration

| Criteria          | Azure Logic Apps                                                       | AWS Step Functions                                     | GCP Application Integration                                                       |
| ----------------- | ---------------------------------------------------------------------- | ------------------------------------------------------ | --------------------------------------------------------------------------------- |
| **Overview**      | Low-code workflow automation service for integrating apps and services | Serverless workflow orchestration using state machines | Low-code integration service for connecting applications and automating workflows |
| **Core Features** | Prebuilt connectors, triggers, visual designer, automation workflows   | State machines, visual workflows, error handling       | Prebuilt connectors, visual flows, API-based integrations                         |
| **Integration**   | Strong integration with Microsoft services (Office 365, Azure, etc.)   | Deep AWS integrations (Lambda, SQS, SNS, etc.)         | Integrates with GCP services and external APIs                                    |
| **Monitoring**    | Azure Monitor + built-in run history                                   | CloudWatch + visual execution tracking                 | Cloud Logging + Monitoring                                                        |
| **Pricing**       | Pay per action/execution                                               | Pay per state transition                               | Pay per usage (executions and connectors)                                         |
| **Strengths**     | Easy to use, low-code, many connectors                                 | Powerful, scalable workflows                           | Simple integrations, API-focused                                                  |
| **Weaknesses**    | Less control than code-based solutions                                 | More complex for simple tasks                          | Fewer features and connectors than Azure                                          |

**Narrative Analysis**

Azure Logic Apps, AWS Step Functions, and GCP Application Integration all support workflow automation, but target different users.

Logic Apps is **low-code and connector-driven**, making it ideal for quickly integrating services with minimal development. AWS Step Functions is more **developer-oriented and scalable**, but less suited for simple integrations. GCP Application Integration is **lightweight and API-focused,** offering simplicity but fewer features.

Overall, **Logic Apps is best for rapid, low-code integrations**, **Step Functions for complex workflows**, and **Application Integration for simple API orchestration**.

---

#### Azure Service Bus vs Amazon SQS/SNS vs GCP Pub/Sub

| Criteria          | Azure Service Bus                                                | Amazon SQS + SNS                                   | GCP Pub/Sub                                              |
| ----------------- | ---------------------------------------------------------------- | -------------------------------------------------- | -------------------------------------------------------- |
| **Overview**      | Managed messaging service supporting queues and topics (pub/sub) | SQS (queues) + SNS (pub/sub messaging)             | Fully managed messaging and event ingestion service      |
| **Core Features** | Queues, topics, subscriptions, message ordering, dead-lettering  | SQS for queues, SNS for pub/sub, message filtering | Pub/sub messaging, push/pull delivery, message retention |
| **Integration**   | Integrates with Azure services and Functions                     | Deep AWS integration (Lambda, S3, etc.)            | Integrates with GCP services and Dataflow                |
| **Monitoring**    | Azure Monitor                                                    | CloudWatch                                         | Cloud Monitoring + Logging                               |
| **Pricing**       | Based on operations and messaging units                          | SQS (requests) + SNS (requests/delivery)           | Based on data volume and operations                      |
| **Strengths**     | Advanced messaging features, reliable delivery                   | Simple, scalable, flexible separation of services  | High throughput, global scalability                      |
| **Weaknesses**    | More complex setup                                               | Requires combining two services                    | Less advanced queue features than Service Bus            |

**Narrative Analysis**

Azure Service Bus, Amazon SQS/SNS, and GCP Pub/Sub all provide messaging for distributed systems but differ in design.

Azure Service Bus offers **advanced messaging features** like topics, ordering, and dead-lettering in a single service, making it suitable for enterprise applications. AWS separates concerns using **SQS (queues) and SNS (pub/sub)**, which increases flexibility but requires more setup. GCP Pub/Sub is **highly scalable and simple**, but lacks some advanced messaging controls.

Overall, **Service Bus is best for complex messaging scenarios, SQS/SNS for flexible AWS architectures**, and **Pub/Sub for high-throughput event streaming**.

---

#### Azure Event Grid vs Amazon EventBridge vs GCP Eventarc

| Criteria          | Azure Event Grid                                               | Amazon EventBridge                                           | GCP Eventarc                                             |
| ----------------- | -------------------------------------------------------------- | ------------------------------------------------------------ | -------------------------------------------------------- |
| **Overview**      | Event routing service for reactive, event-driven architectures | Serverless event bus for routing events between AWS services | Event routing service for GCP services using CloudEvents |
| **Core Features** | Event subscriptions, filtering, push delivery                  | Event buses, rules, filtering, scheduling                    | Event routing, filtering, CloudEvents support            |
| **Integration**   | Integrates with Azure services and custom topics               | Deep AWS integration + SaaS event sources                    | Integrates with Cloud Run, Pub/Sub, and GCP services     |
| **Monitoring**    | Azure Monitor                                                  | CloudWatch                                                   | Cloud Logging + Monitoring                               |
| **Pricing**       | Based on number of operations/events                           | Based on events published and matched                        | Based on event delivery and usage                        |
| **Strengths**     | Simple, low-latency event routing                              | Flexible, supports many event sources                        | Standardized CloudEvents, modern design                  |
| **Weaknesses**    | Less complex routing than EventBridge                          | Can be complex to configure                                  | Depends on other services (Eventarc + Pub/Sub)           |

**Narrative Analysis**

Azure Event Grid, Amazon EventBridge, and GCP Eventarc all provide event routing but differ in flexibility and design.

Event Grid is **simple and efficient**, designed for low-latency event delivery in Azure. EventBridge is more **feature-rich and flexible**, supporting advanced routing and multiple event sources. Eventarc follows a **modern, CloudEvents-based approach**, but depends on other GCP services.

Overall, **Event Grid favors simplicity, EventBridge favors flexibility**, and **Eventarc favors standardization**.

---
