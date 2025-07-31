---
layout: post
title: STEP 4- Implementing CloudTrail
---

Amazon CloudWatch is a monitoring and observability service that allows developers to collect, track, and analyze operational data in real time. In the context of securing an AWS Bedrock chatbot, CloudWatch can be used to monitor model activity and trigger alerts based on suspicious behaviors—such as an unusually high number of requests, suspected prompt injections, or attempts to bypass guardrails. This helps proactively detect security risks and take action before harm occurs.

Suppose someone gains access to your system and deletes a guardrail to access personal information, such as client addresses and bank balances. Implementing EventBridge would alert you to these events.

> CloudTrail vs. CloudWatch – What’s the Difference?

- CloudTrail focuses on auditing and accountability. It captures every API call and user activity within your AWS account. This allows you to track actions related to your chatbot, such as modifications to your KB or chnanges in IAM role.
- CloudWatch, on the other hand, is used for real-time monitoring. You can use it to capture specific events, such as when a prompt injection is suspected, by defining metric filters that scan your logs for those patterns. Once detected, CloudWatch can trigger alarms that notify developers by email (via Amazon SNS) or other channels. Instead of logging everything, we can configure CloudWatch to only log agent invocations, making it more efficient and focused on relevant activity.

#### 1. Enabling Model Invocationn Logging

- Nagivate to settings in the side bar
- Enable model invocation logging

<img src="{{ site.baseurl }}/assets/images/model-logging.png">

Where to see your logs?

<video controls>
  <source src="{{ site.baseurl }}/assets/videos/model-logging.mov" type="video/mp4">
</video>
