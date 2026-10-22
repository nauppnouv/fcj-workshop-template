---
title: "Blog 1 - Amazon SQS"
date: 2026-10-22
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# One SQS message: why can it send an email more than once?

- **Published:** October 22, 2026.
- **Original post:** [View the Facebook post](https://www.facebook.com/share/p/1CJMAYWQBf/).
- **Original post language:** Vietnamese. The article below is an English translation.

Moving email delivery tasks to Amazon SQS is one way to help an application respond faster. The backend sends a message to a queue, and a worker receives and processes it in the background.

However, if a message is processed more than once, the recipient may receive duplicate emails. One possible cause to check is the visibility timeout.

When a worker receives a message from SQS, the message has not yet been deleted from the queue. It is temporarily hidden from other workers for a period called the visibility timeout. The queue's default value is 30 seconds.

Consider an illustrative scenario using SQS Standard and a worker that receives, processes, and then deletes messages:

- At second 0, worker A receives the message and starts processing it.
- The task takes 45 seconds, but the visibility timeout is only 30 seconds.
- Around second 30, if the message has not been deleted or its timeout extended, it may become visible again.
- Worker B may receive the same message while worker A is still running.

If both workers send an email without controlling duplicate tasks, the customer may receive two emails from the same original request.

The visibility timeout should therefore match the processing time. A timeout that is too short increases the risk of overlapping processing; one that is too long makes a message wait longer before it can be retried when a worker fails.

For tasks with varying processing times, a worker can periodically call ChangeMessageVisibility to extend the timeout while it continues working.

However, increasing the timeout does not solve the entire problem. SQS Standard uses at-least-once delivery. A message may still be delivered again, so consumers need to be designed to handle this.

Some considerations include:

- Use a stable business identifier, such as notificationId, to identify the same delivery request.
- Store processing state durably and control cases where multiple workers receive the same request.
- Delete the message only after successful processing.
- Configure a dead-letter queue to separate messages that fail repeatedly.

For email delivery in particular, simply checking whether an email has been sent before sending it still leaves a gap: a worker may send it successfully but fail before saving the status. If the email provider supports idempotency keys, these can help reduce the risk of duplicate delivery.

The key takeaway: **visibility timeout helps limit concurrent processing; consumer design determines how repeated tasks affect users.**

Reference: [Amazon SQS — Visibility timeout](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-visibility-timeout.html)

![Timeline showing message receipt, processing, and deletion during the Amazon SQS visibility timeout.](/images/blogs/sqs-visibility-timeout.png)

Image source: [AWS Documentation](https://docs.aws.amazon.com/images/AWSSimpleQueueService/latest/SQSDeveloperGuide/images/sqs-visibility-timeout-diagram.png).

#AWS #AWSStudyGroup #FCAJ #AmazonSQS #MessageQueue
