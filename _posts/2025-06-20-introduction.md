---
layout: post
title: Introduction
---

test

The use of **Generative AI** is rapidly increasing across various sectors due to its ability to perform a wide range of tasks, including automation, problem-solving, and content creation. Common chatbot applications, such as ChatGPT and Microsoft Copilot, utilize **large language models (LLMs)** to respond to user prompts and generate human-like responses. Because of the accessibility and relative accuracy of these chatbots, many businesses incorporate AI to fulfill roles in customer service, sales, marketing, and internal support processes.

<br>

### OWASP Top 10

**[OWASP (Open Web Application Security Project)](https://owasp.org/www-project-top-ten/)** is a non-profit organization dedicated to improving software security. One of its most influential projects is the OWASP Top 10, a regularly updated list of the most pressing security risks facing web applications. The list helps developers create safer sofware by outlining a standard set of security risks affecting web applications. In each new edition, OWASP highlights emerging threats and evolving best practices.

With the increasing use of AI and emerging security challenges, OWASP developed a new set of guidelines in 2023 to address unique security concerns posed by AI applications. Currently, OWASP has released the latest version of Top 10 for LLMs detailing standards for working securely with AI.

<br>

### Summary of OWASP Top 10 for Large Language Models

<table>
  <thead>
    <tr>
      <th>Security Risk</th>
      <th>Description / Facts</th>
      <th>Common Mitigation Strategies</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Prompt Injection</td>
      <td>Adversaries craft inputs that override system instructions, causing unauthorized data exposure or actions. Still the top threat in 2025.</td>
      <td>Use strong input validation, system message separation, and Bedrock guardrails.</td>
    </tr>
    <tr>
      <td>Sensitive Information Disclosure</td>
      <td>LLMs may unintentionally leak PII, credentials, or proprietary data through training sets.</td>
      <td>Avoid training on sensitive data, implement response filtering, use context redaction.</td>
    </tr>
    <tr>
      <td>Supply Chain Vulnerabilities</td>
      <td>Risks arise from tampered third-party models, adapters, datasets, or libraries.</td>
      <td>Verify sources, use trusted registries, and monitor supply chain components regularly.</td>
    </tr>
    <tr>
      <td>Data and Model Poisoning</td>
      <td>Polluted training or embedding data can trigger backdoors or skew outputs.</td>
      <td>Use curated training datasets, implement anomaly detection on outputs.</td>
    </tr>
    <tr>
      <td>Improper Output Handling</td>
      <td>Model outputs are used without validation, leading to unsafe actions or leaks.</td>
      <td>Apply output sanitization, enforce output review, and avoid executing outputs blindly.</td>
    </tr>
    <tr>
      <td>Excessive Agency</td>
      <td>Overly autonomous LLMs may take unintended or harmful actions.</td>
      <td>Limit action scope, require user confirmation, implement role-based access control.</td>
    </tr>
    <tr>
      <td>System Prompt Leakage</td>
      <td>Internal system prompts leak to users, revealing logic or intentions.</td>
      <td>Use prompt obfuscation, scope-limited agents, and guardrail filters.</td>
    </tr>
    <tr>
      <td>Vector and Embedding Weaknesses</td>
      <td>Embeddings can be reverse-engineered or manipulated to leak or influence outputs.</td>
      <td>Encrypt embedding stores, apply vector sanitization, use robust similarity metrics.</td>
    </tr>
    <tr>
      <td>Misinformation</td>
      <td>Hallucinations or false outputs pose risks, especially when users blindly trust LLM content.</td>
      <td>Add disclaimers, human-in-the-loop review, cross-reference with trusted sources.</td>
    </tr>
    <tr>
      <td>Unbounded Consumption</td>
      <td>Excessive resource usage can lead to denial-of-service, inflated costs, and operational issues.</td>
      <td>Apply rate limiting, monitor usage metrics, use cost control tools in AWS.</td>
    </tr>
  </tbody>
</table>

Resource: [OWASP Website](https://genai.owasp.org/resource/owasp-top-10-for-llm-applications-2025/)

<br>

## Lab Objective

You are a software developer for a bank and are tasked with improving customer service by integrating a secure chatbot onto their website. Your goal is to build a chatbot to answer common customer questions while witholding personal information.

In this lab, you will build an AI-powered chatbot using AWS Bedrock. You will identify potential security risks based on the OWASP Top 10 for LLMs and implement mitigation strategies to ensure secure usage of the AI application.
