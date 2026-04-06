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

Azure Functions, AWS Lambda, and Cloud Run functions all provide serverless, event-driven compute, but they differ in how developers interact with them.

Azure Functions stands out for its **trigger and binding model**, which reduces boilerplate code and simplifies integration with other Azure services. This makes it especially beginner-friendly and efficient for Azure-based applications.

AWS Lambda offers similar functionality but is more **ecosystem-driven**, requiring integration with multiple AWS services like S3, SQS, and API Gateway. While this increases flexibility and power, it can also make architectures more complex.

Cloud Run functions takes a more **modern and flexible approach**, relying on Cloud Run and Eventarc for event handling. However, this separation can make it feel less centralized compared to Azure Functions.

Overall, **Azure Functions is best for rapid development in Azure, AWS Lambda is strongest within complex AWS architectures,** and **Cloud Run functions is a flexible but slightly less unified GCP alternative**.

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

Durable Functions, AWS Step Functions, and Google Cloud Workflows all provide **workflow orchestration**, but they differ significantly in how workflows are defined and managed.

Durable Functions follows a **code-first approach**, where workflows are written in programming languages using Azure Functions. It supports patterns like chaining, fan-out/fan-in, and long-running workflows with built-in state management. This makes it flexible for developers but less visual.

AWS Step Functions uses a **visual**, **state-machine-based approach,** making workflows easier to design, debug, and monitor. It is highly scalable and integrates deeply with AWS services, but complex workflows can become harder to manage.

Google Cloud Workflows takes a **simpler**, **configuration-based approach**, using YAML or JSON to define workflows. It is particularly strong for orchestrating APIs and lightweight processes but lacks some advanced features compared to AWS and Azure.

Overall, **Durable Functions is best for developer-driven orchestration in Azure**, **AWS Step Functions is ideal for visual and large-scale workflows**, and **Google Cloud Workflows is best for simple orchestration and API integration**.

---

## 4. Organize in Markdown

- Create a `README.md` file in your GitHub repository containing your report
- Use **headings**, **tables**, and **bullet points** for clarity
- Include a **comparison table** for each service, followed by a **narrative analysis**

---
