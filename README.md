# CST8917 – Serverless Applications

## Assignment 2 – Serverless Service Alternatives Report

**St: Olga Durham**

**St#: 040687883**

---

## 1. Azure Services to Compare

The report include the following Azure services:

- **Azure Functions** (Triggers & Bindings)
- **Durable Functions** (Chaining, Orchestration, Fan-out/Fan-in)
- **Azure Logic Apps**
- **Azure Service Bus** (Queues & Topics)
- **Azure Event Grid**
- **Azure Event Hubs**

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

For each service, included:

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

Azure Functions, AWS Lambda, and Cloud Run functions all provide serverless, event-driven compute, but they differ in how developers build and integrate applications.

Azure Functions uses a **trigger and binding model**, which simplifies development by reducing the need for boilerplate code when connecting to other services. This makes it especially effective for integration-heavy solutions and more approachable for developers working within the Azure ecosystem.

AWS Lambda follows a more **ecosystem-driven approach**, where functions are tightly integrated with other AWS services such as S3, SQS, and API Gateway. While this provides high flexibility and scalability, it often requires combining multiple services, which can increase architectural complexity.

Cloud Run functions takes a **modern, container-based approach**, relying on Cloud Run and Eventarc for execution and event routing. This provides flexibility and aligns with modern cloud standards, but can feel less centralized compared to Azure Functions.

Overall, Azure Functions is best suited for rapid development in Azure environments, AWS Lambda for complex and scalable AWS architectures, and Cloud Run functions for flexible, modern GCP-based solutions.

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

Durable Functions, AWS Step Functions, and Google Cloud Workflows all provide serverless workflow orchestration, but they differ in how workflows are defined and managed.

Durable Functions follows a **code-first approach**, where workflows are written using programming languages within Azure Functions. It supports advanced patterns such as chaining, fan-out/fan-in, and long-running processes with built-in state management. This gives developers strong flexibility and control, especially for complex application logic.

AWS Step Functions uses a **visual, state machine-based model**, allowing workflows to be defined as a series of states. This makes it easier to design, monitor, and debug workflows, particularly in large-scale systems. However, as workflows grow, they can become complex to manage.

Google Cloud Workflows takes a more **configuration-based approach**, using YAML or JSON to define sequences of tasks. It is well-suited for orchestrating APIs and simple workflows but offers fewer advanced orchestration patterns.

Overall, Durable Functions is ideal for developer-driven orchestration in Azure, Step Functions for scalable and visual workflow management, and Cloud Workflows for simpler orchestration scenarios.

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

Azure Logic Apps, AWS Step Functions, and GCP Application Integration all enable workflow automation, but they are designed for different types of users and use cases.

Azure Logic Apps is a **low-code, connector-based service** that allows users to build workflows using a visual designer. It provides a large library of prebuilt connectors for Microsoft and third-party services, making it especially useful for quickly integrating systems without extensive coding. This makes it ideal for business processes and integration scenarios.

AWS Step Functions, in contrast, is more **developer-focused**, using a state machine model to define workflows. While it offers greater control and scalability, it is less suited for simple integrations and requires more technical expertise.

GCP Application Integration is also **low-code and API-focused**, enabling users to connect services through visual flows. However, it generally offers fewer connectors and features compared to Azure Logic Apps.

Overall, Azure Logic Apps is best for rapid, low-code integrations, Step Functions for complex and scalable workflows, and Application Integration for lightweight API orchestration.

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

Azure Service Bus, Amazon SQS/SNS, and GCP Pub/Sub all provide messaging capabilities for distributed systems, but they differ in complexity and design approach.

Azure Service Bus is a **fully featured messaging service** that supports queues and topics within a single platform. It includes advanced capabilities such as message ordering, dead-lettering, and publish/subscribe patterns, making it well-suited for enterprise applications that require reliable and controlled message handling.

AWS separates messaging into **SQS (queues) and SNS (pub/sub)**, which provides flexibility but requires combining multiple services to achieve similar functionality. This modular approach works well in AWS environments but can increase architectural complexity.

GCP Pub/Sub offers a **simple and highly scalable messaging model**, designed for high-throughput event distribution. While it is easy to use and scales automatically, it lacks some of the advanced messaging features found in Azure Service Bus.

Overall, Azure Service Bus is ideal for complex, enterprise messaging scenarios, SQS/SNS for flexible AWS-based architectures, and Pub/Sub for scalable and straightforward messaging.

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

Azure Event Grid, Amazon EventBridge, and GCP Eventarc all provide event routing for event-driven architectures, but they differ in flexibility and level of abstraction.

Azure Event Grid is designed for **simple and low-latency event routing**, enabling systems to react quickly to events generated by Azure services or custom sources. Its publish/subscribe model is easy to configure, making it a strong choice for reactive applications that require minimal overhead.

Amazon EventBridge offers a more **feature-rich and flexible event bus**, supporting advanced filtering, multiple event sources (including SaaS integrations), and event scheduling. This makes it powerful for complex event-driven systems, but also more complex to configure and manage.

GCP Eventarc follows a **modern, CloudEvents-based approach**, providing standardized event routing across Google Cloud services. It integrates well with Cloud Run and other GCP tools, but often depends on additional services, which can make the architecture less centralized.

Overall, Azure Event Grid is best for simple and efficient event routing, EventBridge for flexible and feature-rich event management, and Eventarc for standardized, modern event-driven solutions.

---

#### Azure Event Hubs vs Amazon Kinesis Data Streams vs GCP Pub/Sub

| Criteria          | Azure Event Hubs                                            | Amazon Kinesis Data Streams                                | GCP Pub/Sub                                              |
| ----------------- | ----------------------------------------------------------- | ---------------------------------------------------------- | -------------------------------------------------------- |
| **Overview**      | Big data streaming platform for event ingestion at scale    | Real-time data streaming service for large-scale ingestion | Messaging and event streaming service for real-time data |
| **Core Features** | Partitioned streams, high throughput, event retention       | Shards, real-time processing, data retention               | Pub/sub messaging, push/pull delivery, scaling           |
| **Integration**   | Integrates with Azure Analytics (Stream Analytics, Synapse) | Integrates with AWS analytics (Lambda, Kinesis Analytics)  | Integrates with Dataflow, BigQuery                       |
| **Monitoring**    | Azure Monitor                                               | CloudWatch                                                 | Cloud Monitoring + Logging                               |
| **Pricing**       | Based on throughput units and retention                     | Based on shards and data volume                            | Based on data volume and operations                      |
| **Strengths**     | High throughput, strong analytics integration               | Fine-grained control over streams                          | Fully managed, easy scaling                              |
| **Weaknesses**    | Requires configuration of partitions/units                  | Can be complex to manage shards                            | Less control over streaming internals                    |

**Narrative Analysis**

Azure Event Hubs, Amazon Kinesis Data Streams, and GCP Pub/Sub all support real-time event ingestion and streaming, but they differ in how much control and specialization they provide.

Azure Event Hubs is designed for **high-throughput event ingestion** and works especially well in analytics and telemetry scenarios. It is tightly integrated with Azure data services such as Stream Analytics and Synapse, making it a strong choice for building large-scale data pipelines and processing streams of events in near real time.

Amazon Kinesis Data Streams provides similar streaming capabilities but offers more **fine-grained control** over stream structure and processing through shards. This makes it powerful for custom streaming architectures, although it also introduces more operational complexity compared to a more fully managed approach.

GCP Pub/Sub provides a **fully managed and highly scalable model** for event streaming and messaging. It is simple to use and integrates well with services like Dataflow and BigQuery, but it offers less control over the underlying streaming mechanics than Event Hubs or Kinesis.

Overall, Azure Event Hubs is best for large-scale Azure data streaming, Kinesis for controlled and customizable stream processing, and Pub/Sub for simple, scalable event delivery.

---
