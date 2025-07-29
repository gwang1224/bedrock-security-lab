---
layout: post
title: STEP 4- EventBridge & SNS
---

EventBridge is an application that receives events from AWS services and routes them to a target based on defined rules. When creating a chatbot, we want EventBridge to notify us when there are certain security threat events occurring, such as updating or deleting a guardrail. Suppose someone hacks into your system and deletes a guardrail to access personal information, such as client addresses and bank balances. Implementing EventBridge would alert you to these events.

#### Create an SNS Topic

1. Navigate to SNS Dashboard
2. Create a new Topic
   - Click the “Topics” link in the left-hand sidebar.
   - Click the “Create topic” button.
3. Configure the Topic Settings
   - Topic type: Choose Standard.
   - Name: Enter a unique name like security-alerts-topic.
   - Leave other defaults unless needed.
   - Click “Create topic”.
4. Add a Subscription
   - On the topic details page, click “Create subscription”.
   - Protocol: Choose Email.
   - Endpoint: Enter the email address that should receive notifications.
   - Click “Create subscription”.
5. Confirm Email Subscription
   - Check your email inbox.
   - Click the confirmation link in the message from AWS to activate the subscription.
6. Test the Topic
   - In the SNS topic page, click “Publish message”.
   - Enter a subject and message body, then click “Publish” to test if the email is received.

<video controls>
  <source src="{{ site.baseurl }}/assets/videos/create-sns-topic.mov" type="video/mp4">
</video>

This is what the subscription confirmation should look like
<img src="{{ site.baseurl }}/assets/images/sns.png">

#### Creating an EventBridge rule

1. Navigate to the EventBridge Dashboard

2. Create a New Rule

   - Click the **"Rules"** link in the left-hand sidebar.
   - Click the **"Create rule"** button.

3. Configure the Rule Details

   - **Name**: Enter a unique name like `agent-security-alert`.
   - **Description**: Optionally add a description.
   - **Event bus**: Choose `default` (unless you're using a custom event bus).
   - Click **Next**.

4. Define the Event Pattern

   - Select Use pattern form for pattern
   - **Event source**: Choose `AWS services`.
   - **Service name**: Select `Bedrock`.
   - Look through these actions supported by Bedrock: [Actions](https://docs.aws.amazon.com/bedrock/latest/APIReference/API_Operations.html). What are some that would be useful to be notified of?
   - **Event type**: Choose events like `UpdateGuardrail`
   - Click **Next**.

5. Add a Target

   - **Target type**: Select `SNS topic`.
   - **Topic**: Choose the SNS topic you created (e.g., `security-alerts-topic`).
   - _(Optional)_ Add input transformation to customize the notification message.
   - Click **Next**.

6. Review and Create the Rule
   - Review all your settings.
   - Click **Create rule** to finalize.
