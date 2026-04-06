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

### Comparison Table

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

#### Narrative Analysis (Shortened)

Azure Functions, AWS Lambda, and Cloud Run functions all provide serverless, event-driven compute, but they differ in how developers interact with them.

Azure Functions stands out for its **trigger and binding model**, which reduces boilerplate code and simplifies integration with other Azure services. This makes it especially beginner-friendly and efficient for Azure-based applications.

AWS Lambda offers similar functionality but is more **ecosystem-driven**, requiring integration with multiple AWS services like S3, SQS, and API Gateway. While this increases flexibility and power, it can also make architectures more complex.

Cloud Run functions takes a more **modern and flexible approach**, relying on Cloud Run and Eventarc for event handling. However, this separation can make it feel less centralized compared to Azure Functions.

Overall, **Azure Functions is best for rapid development in Azure, AWS Lambda is strongest within complex AWS architectures,** and **Cloud Run functions is a flexible but slightly less unified GCP alternative**.

---

## 4. Organize in Markdown

- Create a `README.md` file in your GitHub repository containing your report
- Use **headings**, **tables**, and **bullet points** for clarity
- Include a **comparison table** for each service, followed by a **narrative analysis**

---
