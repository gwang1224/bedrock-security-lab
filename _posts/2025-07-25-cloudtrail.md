---
layout: post
title: STEP 3- Cloudtrail
---

**[CloudTrail](https://docs.aws.amazon.com/bedrock/latest/userguide/logging-using-cloudtrail.html)** captures every API call and user activity within your AWS account. This allows you to track actions related to your chatbot, such as modifications to your knowledge base data in S3 or changes to IAM roles that grant access to the model. These trails can indicate any anomalies that might indicate an LLM attack. CloudTrail provides transparency showing who accessed the LLM, when, and from where. This enhances accountability and monitors user behavior, enabling authorized users to identify potential threats from attackers.

First, we must enable CloudTrail so that it logs all management actions, which include DeleteGuardrail, UpdateGuardrail, getAgent, etc.

#### Enabling CloudTrail

1. Go to CloudTrail Console
2. In the sidebar, click “Trails” → then click “Create trail”
3. Name your trail, e.g., bedrock-audit-trail
4. Choose “Apply trail to all regions”
5. Enable management events (this includes DeleteGuardrail)
   • Set “Read/Write events” to “All” or at least “Write-only”
6. Choose a new or existing S3 bucket to store logs
7. (Optional) Enable CloudWatch Logs integration to trigger alarms
   • Enable integration and provide a log group
8. Click “Create trail”
