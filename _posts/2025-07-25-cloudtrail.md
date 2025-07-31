---
layout: post
title: STEP 3- Cloudtrail
---

**[CloudTrail](https://docs.aws.amazon.com/bedrock/latest/userguide/logging-using-cloudtrail.html)** captures every API call and user activity within your AWS account. This allows you to track actions related to your chatbot, such as modifications to your knowledge base data in S3 or changes to IAM roles that grant access to the model. These trails can indicate any anomalies that might indicate an LLM attack. CloudTrail provides transparency showing who accessed the LLM, when, and from where. This enhances accountability and monitors user behavior, enabling authorized users to identify potential threats from attackers.

First, we must enable CloudTrail so that it logs all management actions, which include DeleteGuardrail, UpdateGuardrail, getAgent, etc.

#### Enabling CloudTrail

<video controls>
  <source src="{{ site.baseurl }}/assets/videos/cloudtrail.mov" type="video/mp4">
</video>

1. Go to CloudTrail Console
2. In the sidebar, click “Trails”, then click “Create trail”
3. Name your trail, e.g., bedrock-management-events
4. Select "Create new S3 bucket" as storage location and name the bucket
5. Create and name a new KMS key, e.g. alias/cloudtrail-logs
   - This is used to provide a further layer of protection for the encryption of your log files, providing an extra layer of security for your sensitive log data.
6. Enable CloudWatch Logs
   - Create a new log group
   - Name log group, e.g. bedrock-events
   - Name a new IAM role
7. Enable management events (this includes DeleteGuardrail)
   - Set “Read/Write events” to “All” or at least “Write-only”
8. Keep the rest of the settings as default
9. Click “Create trail”
