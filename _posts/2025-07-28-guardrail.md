---
layout: post
title: STEP 2- Implementing Guardrails
---

Guardrails are a Bedrock feature designed to ensure that AI systems operate safely and ethically. They allow developers to define boundaries for generative AI, preventing the output of harmful, misleading, or sensitive content. By implementing guardrails, we can block responses that include information such as user addresses, bank balances, and inappropriate or unauthorized actions.

Guardrails help mitigate multiple OWASP Top 10 security risks for Large Language Models (LLMs), such as:

- **Prompt Injection**
- **Sensitive Information Disclosure**
- **Excessive Agency**
- **Misinformation**

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
<summary>Extra help?</summary>
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
      <td>In <strong>Step 5</strong>, use <strong>denied topics</strong> to block terms like <em>account number</em> or <em>bank balance</em>.<br>
      <em>Hint:</em> When adding a guardrail for "bank balance," restrict <strong>only user input</strong> to avoid false positives. Look for the toggle that applies rules to inputs only.</td>
    </tr>
    <tr>
      <td><strong>Excessive Agency</strong></td>
      <td>Add <strong>denied output phrases</strong> to stop the AI from pretending to take unauthorized actions (e.g., “I’ve updated your account” or “Money has been transferred”). The AI should not simulate authority.</td>
    </tr>
    <tr>
      <td><strong>Misinformation</strong></td>
      <td>Add a <strong>"Relevance filter"</strong> under guardrail settings.<br>
      <em>Hint:</em> This ensures the AI’s response is grounded in the knowledge base, helping prevent hallucinations or confident falsehoods.</td>
    </tr>
  </tbody>
</table>
</details>

To test, go back to Agent. Edit the agent and add guardrails in the guardrail section.

<img src="{{ site.baseurl }}/assets/images/guardrail.png">

Test out your chatbot the same way you did in Step 1. Is your chatbot more secure?
