---
title: "AWS Cloud and AI Day Hanoi 2026 — HCMC Watch Party"
date: 2026-09-29
weight: 1
chapter: false
pre: " <b> 4.2. </b> "
---

### Event information

| Item | Details |
| --- | --- |
| **Event** | AWS Cloud and AI Day Hanoi 2026 |
| **Date** | September 29, 2026 |
| **Time** | 8:00 a.m.–5:00 p.m. (ICT, UTC+7), per the watch party schedule |
| **Format** | Ho Chi Minh City watch party following the program streamed from Hanoi |
| **Watch party venue** | 26th floor, Bitexco Financial Tower, 2 Hai Trieu Street, Saigon Ward, Ho Chi Minh City |
| **My role** | Attendee |
| **Event links** | [AWS Cloud and AI Day Hanoi](https://aws.amazon.com/events/cloud-day-hanoi/) · [Watch party information](https://apj.awsevents.com/sites/aws-cloud-day-hanoi-watch-party-attendee) |

On September 29, 2026, I attended the AWS Cloud and AI Day Hanoi watch party in Ho Chi Minh City and followed the keynote streamed from Hanoi. The presentations explored how organizations are applying cloud and AI, the engineering foundations behind reliable services, and the need to validate software as AI takes on a larger role in development. These topics helped me connect new technologies with practical concerns such as security, reliability, and engineering accountability.

AWS promoted more than 30 sessions at the Hanoi event on agentic AI, data and analytics, application modernization, and industry solutions, alongside an expo and workshops. The watch party page listed the keynote and sessions from the Builders x AI track. This report focuses on the keynote, which is the portion covered by the transcript I provided.

### Event objectives

- Learn how organizations in Vietnam are bringing cloud and AI into business processes.
- Understand the platform, security, and governance foundations needed to move AI beyond experimentation.
- Explore how AI-assisted development should be supported by testing, evidence, and accountable release decisions.
- Identify cloud and AI topics to study further through personal projects.

### Keynote speakers

| Order | Speaker | Title | Main topic |
| --- | --- | --- | --- |
| 1 | Hoang Minh | Deputy Minister of Science and Technology | Digital infrastructure, compute capacity, and Vietnam’s cloud and AI ecosystem. |
| 2 | Jennifer Wicks | U.S. Ambassador to Vietnam | Technology cooperation and cloud’s role in digital transformation. |
| 3 | Eric Yeo | Country General Manager Malaysia, Vietnam, Indochina, AWS | Cloud and AI in Vietnam, customer examples, infrastructure, and skills development. |
| 4 | Dr. Jens Lottner | Chief Executive Officer, Techcombank | Integrating AI into enterprise workflows and developing staff capabilities. |
| 5 | Dr. Werner Vogels | Chief Technology Officer, Amazon.com | Invisible engineering, cloud foundations, and system design decisions. |
| 6 | Mai Le | Director of Product Management, Katalon | Software quality validation as AI accelerates development. |

AWS lists all six as keynote speakers. The transcript contains very little of Deputy Minister Hoang Minh’s opening remarks, so that part is supplemented by the [Ministry of Science and Technology’s event report](https://mst.gov.vn/ai-viet-nam-tu-mo-rong-ha-tang-den-bai-toan-bien-cong-nghe-thanh-gia-tri-19726093007364899.htm). The times below refer to the supplied keynote transcript.

### Key highlights

#### 1. Digital infrastructure and Vietnam’s cloud and AI ecosystem

The opening remarks placed AI in a broader context: creating value from technology calls for digital infrastructure, compute capacity, skilled people, and collaboration. Deputy Minister Hoang Minh emphasized an ecosystem in which businesses, government, universities, and research organizations contribute to developing technology. Ambassador Jennifer Wicks spoke about cloud’s role in innovation, competitiveness, and technology cooperation between Vietnam and the United States. Source for the Deputy Minister’s remarks: [Ministry of Science and Technology](https://mst.gov.vn/ai-viet-nam-tu-mo-rong-ha-tang-den-bai-toan-bien-cong-nghe-thanh-gia-tri-19726093007364899.htm).

#### 2. Cloud and AI applications tied to customer needs

Eric Yeo presented customer examples showing how AI can support concrete activities, including healthcare information analysis, in-store product display monitoring, and agricultural operations. My takeaway is to start with the problem to solve, then consider the data, cloud services, and measures needed to evaluate the result. He also discussed the Hanoi AWS Local Zone as an infrastructure option closer to local users. AWS had announced the Local Zone’s availability in June 2026, before this event.

#### 3. Techcombank: integrating AI into workflows

Dr. Jens Lottner described AI as a way to change how work is organized, rather than simply add a standalone tool. Examples included coordinating software requirements, development, and testing; using an agent to connect operations and customer service when resolving incidents; and helping frontline staff prepare information for customers.

The presentation also highlighted orchestration platforms, access governance, model selection, staff training, and outcome measurement. The name of one software development tool is unclear in the transcript, so I have described its role without assigning an unverified product name. These examples and any reported improvements belong to the speaker’s presentation; they are not systems I implemented.

#### 4. Werner Vogels: the invisible engineering behind services

Dr. Werner Vogels used database and infrastructure stories to explain the engineering decisions that end users often do not see. One lesson was to understand how an application accesses data before choosing an architecture. Sound design starts with real requirements and access patterns.

Cloud examples illustrated several layers of this work: the AWS Nitro System supports infrastructure operations; Lambda and Firecracker illustrate event-driven workloads in isolated environments; and Lambda SnapStart uses snapshots of initialized environments to improve startup performance for supported runtimes. The discussion of the Amazon Time Sync Service and ClockBound extended the topic to time in distributed systems: timestamps need uncertainty information so applications can reason about event ordering. [AWS Lambda SnapStart documentation](https://docs.aws.amazon.com/lambda/latest/dg/snapstart.html) · [AWS ClockBound](https://github.com/aws/clock-bound).

This session helped me see how cloud services depend on engineering choices involving performance, isolation, time, and reliability. Understanding these foundations helps engineers select solutions based on system requirements instead of relying on service names alone.

#### 5. Katalon: validation must keep pace with software development

Mai Le described the validation gap between AI-assisted development speed and the ability to test software. When code and changes are produced faster than they can be assessed, risk can reach users. An AI agent therefore needs connected context from requirements, code changes, test cases, defects, and operational data to determine what should be tested.

In Katalon’s platform example, the speaker mentioned Amazon EKS, Amazon RDS, Amazon S3, and Amazon Kinesis as the foundation for its application, data, and telemetry; Amazon Bedrock for governed model access; and Amazon Bedrock AgentCore Runtime as an isolated environment for agents and approved tools. The key point was that a confident AI answer does not prove that software works. Teams need test results, logs, screenshots, videos, and telemetry. People still define risk boundaries, review exceptions, and decide whether to release. References: [Katalon True Platform](https://docs.katalon.com/katalon-platform/security-and-privacy-faq) · [AWS AgentCore Runtime](https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/agents-tools-runtime.html).

#### 6. Validation debt and engineering accountability

In the closing remarks, Werner Vogels returned to validation debt: the work that accumulates when software changes are produced faster than they can be verified. I took away the need to pair development speed with disciplined testing, traceable evidence, and clear responsibility. Foundation work may be invisible to users, but it contributes to more dependable software.

### Key takeaways

- **Start with the problem:** define the workflow, users, and intended outcome before choosing an AI model or service.
- **Design governance into the architecture:** agents need appropriate permissions, defined tools, and observable activity.
- **Validate output with evidence:** tests, logs, and telemetry help teams assess what actually happened.
- **Understand engineering trade-offs:** performance, isolation, cost, and reliability all matter when designing a system.
- **Keep people accountable:** AI can assist with development and testing, while engineers remain responsible for evaluating risk and release decisions.

### Next steps

I plan to choose a small use case for practicing an AI-assisted workflow. Before testing it, I will define its inputs and outputs, set limits on tool access, write validation criteria, and retain logs and results for review. This is a future learning plan, not hands-on work completed at the watch party.

### Watch party experience

I attended the AWS Cloud and AI Day through the Ho Chi Minh City watch party and followed the keynote streamed from Hanoi. It gave me a way to learn from AWS, business leaders, and product specialists alongside the local builder community. The keynote is the portion I can document from the supplied transcript; other sessions and hands-on activities are not included in my personal event recap.

### References

- [AWS Cloud and AI Day Hanoi — event and speaker information](https://aws.amazon.com/events/cloud-day-hanoi/)
- [AWS Cloud Day Hanoi — Ho Chi Minh City watch party](https://apj.awsevents.com/sites/aws-cloud-day-hanoi-watch-party-attendee)
- [Vietnam Ministry of Science and Technology — Deputy Minister Hoang Minh’s remarks](https://mst.gov.vn/ai-viet-nam-tu-mo-rong-ha-tang-den-bai-toan-bien-cong-nghe-thanh-gia-tri-19726093007364899.htm)
- [Kha Van on AWS Builder Center — community perspective on cloud and AI in Hanoi](https://builder.aws.com/content/3KMpKxUhRFeSlclpmwu5ZxBQBYL/aws-cloud-and-ai-day-hanoi-2026-building-for-the-next-phase-of-cloud-and-ai)
