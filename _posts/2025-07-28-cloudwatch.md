---
layout: post
title: STEP 5- CloudWatch
---

Amazon CloudWatch is a monitoring and observability service that allows developers to collect, track, and analyze operational data in real time. In the context of securing an AWS Bedrock chatbot, CloudWatch can be used to monitor model activity and trigger alerts based on suspicious behaviors, such as an unusually high number of requests, suspected prompt injections, or attempts to bypass guardrails. This helps proactively detect security risks and take action before harm occurs.

Suppose someone gains access to your system and deletes a guardrail to access personal information, such as client addresses and bank balances. Implementing EventBridge would alert you to these events.

> CloudTrail vs. CloudWatch – What’s the Difference?

- CloudTrail focuses on auditing and accountability. It captures every API call and user activity within your AWS account. This allows you to track actions related to your chatbot, such as modifications to your KB or chnanges in IAM role.
- CloudWatch, on the other hand, is used for real-time monitoring. You can use it to capture specific events, such as when a prompt injection is suspected, by defining metric filters that scan your logs for those patterns. Once detected, CloudWatch can trigger alarms that notify developers by email (via Amazon SNS) or other channels. Instead of logging everything, we can configure CloudWatch to only log agent invocations, making it more efficient and focused on relevant activity.

#### Creating a Metric Filter to Detect Specific Events in AWS

This tutorial explains how to create a metric filter in CLoudWatch to detect specific API events, such as `InvokeModel`, which is helpful for monitoring and alerting on critical activity.

<video controls>
  <source src="{{ site.baseurl }}/assets/videos/creating-metric.mov" type="video/mp4">
</video>

1. In CloudWatch console, under "Log group", find the log group associated with your CloudTrail trail
2. Under the tab metric filter, create a metric filter

   - Pattern: e.g., { ($.eventName = "InvokeModel") }

3. Before creating the metric filter, ensure that it works. CloudWatch allows you to test the filter with existing log data or by creating your own

- Testing with your own log data
  - If you haven't invoked your model after creating the trail, invoke the model with a couple of prompts so that CloudTrail will log the model activity
  - Select the log data that contains the Invoke model and click "Test Pattern" to see if the filter matches any activity
- Testing with example data _(easier)_
  - In the json template, for each log where the trail logs the "eventName", change it to `InvokeModel`
  - Click "Test Pattern" and one match should show in the results

4. Configure metric details

- Name filters : e.g. "model-invocations"
- Configure details with descriptive names
  - For metric value, put `1`. This means that each time a matching log entry is found, the metric increases by 1.

5. "Create metric filter." Your metric will now appear in CloudWatch metrics and can be used to trigger alarms.

#### Creating an Alarm for InvokeModel

We will now create a CloudWatch Alarm using the SNS on this metric

<video controls>
  <source src="{{ site.baseurl }}/assets/videos/creating-metric.mov" type="video/mp4">
</video>

1. The metric filter you just created should now appear under the **"Metric filters"** tab in your selected log group. Make sure the **Filter Pattern** matches the one you defined earlier. To proceed, check the box next to the metric filter, then click **"Create alarm"** in the upper-right corner.

2. Set the alarm conditions:

   - **Threshold type**: `Static`
   - **Whenever**: `model-invocations` is `Greater than or equal to` `1`
   - A preview graph will show how often this event occurs over time. The x-axis represents time, and the y-axis reflects the number of matching log events.

3. In the **Actions** section, configure the alarm to send notifications:

   - Choose an existing Amazon SNS topic or create a new one.
   - This will send an email notification whenever the condition is met.

4. Fill in the alarm details:

   - Name your alarm (e.g., `ModelInvocationAlarm`)
   - Optionally, add a description for context

5. Click **"Create alarm"** to finish setup.

6. You’re done! When a model is invoked and the metric condition is met, AWS will send an alert email to your SNS subscription. This may take a few minutes depending on CloudTrail log delivery.

#### Task: Create Another Metric Filter

Try creating a second metric filter for another type of activity you’d like to monitor. For example, you could track when someone disables a guardrail or modifies your chatbot configuration.

**Screenshot: After creating your metric, show the notification email you received**

Example:
<img src="{{ site.baseurl }}/assets/images/alarm-email.png">
