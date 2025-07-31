---
layout: post
title: STEP 2- Implementing Guardrails
---

**[Guardrails](https://aws.amazon.com/bedrock/guardrails/)** are a Bedrock feature designed to ensure that AI systems operate safely and ethically. They allow developers to define boundaries for generative AI, preventing the output of harmful, misleading, or sensitive content. By implementing guardrails, we can block responses that include information such as user addresses, bank balances, and inappropriate or unauthorized actions.

Guardrails help mitigate multiple OWASP Top 10 security risks for LLMs, such as:

- **Prompt Injection**
- **Sensitive Information Disclosure**
- **Excessive Agency**
- **Misinformation**

<br>

#### Secure the Chatbot Using Guardrails

Your goal in this step is to implement guardrails that prevent the chatbot from engaging in risky behaviors.

1. In the sidebar of Bedrock, navigate to "Guardrail" under "Build" section
2. Create guardrail
3. Configure guardrails to block:
   - **Prompt Injection:** Prevent users from overriding the system's intended behavior.
   - **Sensitive Information Disclosure:** Block sharing of personal identifiers like SSNs, addresses, and bank balances.
   - **Excessive Agency:** Stop the model from giving commands, making transactions, or acting autonomously beyond its scope.
   - **Misinformation:** Prevent hallucinated facts or unsupported claims.

<details>
<summary>Need extra help?</summary>
<br>
<table>
  <thead>
    <tr>
      <th>OWASP Risk</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>Prompt Injection</strong></td>
      <td>In <strong>Step 2</strong>, be sure to enable the <strong>"Prompt attacks"</strong> filter under Bedrock Guardrails. This helps block users from injecting system-level prompts.</td>
    </tr>
    <tr>
      <td><strong>Sensitive Information Disclosure</strong></td>
      <td>For default type of personal information, block name, phone, email, etc in <strong>Step 5</strong>.
      <br>
      To block account number and bank balance, try using <strong>denied topics (Step 3)</strong>.
      <em>Hint:</em> Add several phrases like... "Your bank balance is $5000.", "You have $2942 in your savings account", "Your current account holds", "You have $2000 in your account". Play around with this and test to see if this information is blocked when queried.</td>
    </tr>
    <tr>
      <td><strong>Excessive Agency</strong></td>
      <td>Add <strong>denied topics</strong> to stop the AI from pretending to take unauthorized actions (e.g., "I've updated your account" or "Money has been transferred"). The AI should not simulate authority.</td>
    </tr>
    <tr>
      <td><strong>Misinformation</strong></td>
      <td>Add a <strong>"Relevance filter"</strong> under guardrail settings.<br>
      <em>Hint:</em> This ensures the AI's response is grounded in the knowledge base, helping prevent hallucinations or confident falsehoods.</td>
    </tr>
  </tbody>
</table>
</details>

To test, go back to Agent. Edit the agent in agent builder and add guardrails in the guardrail section and "Prepare" to test.

<img src="{{ site.baseurl }}/assets/images/guardrail.png">

Test out your chatbot the same way you did in Step 1. Is your chatbot more secure?

<br>

**Screenshot: After adding your guardrail, show your chatbot agent blocking a prompt**

Example:
<img src="{{ site.baseurl }}/assets/images/s2_example.png">
