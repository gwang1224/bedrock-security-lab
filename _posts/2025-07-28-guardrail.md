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

#### 🔧 Instructions:

1. **Open your AWS Bedrock console** and navigate to your agent.
2. **Go to the “Guardrails” tab** of your agent configuration.
3. Enable or configure guardrails to block:
   - **Prompt Injection:** Prevent users from overriding the system's intended behavior.
   - **Sensitive Information Disclosure:** Block sharing of personal identifiers like SSNs, addresses, and bank balances.
   - **Excessive Agency:** Stop the model from giving commands, making transactions, or acting autonomously beyond its scope.
   - **Misinformation:** Prevent hallucinated facts or unsupported claims.
4. Save your configuration and test by prompting the chatbot with edge cases to validate protection.

> 💡 Tip: Combine keyword blocking with Bedrock’s built-in sensitive data detection to increase reliability.

In the next step, you’ll learn how to **test and audit** your chatbot’s behavior to ensure these protections are working as expected.
