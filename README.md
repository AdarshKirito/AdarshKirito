### I build LLM agents that are reliable, safe and cost-efficient in production.

Software Engineer, AI Platform at **Notion**, working on shared LLM services and agent tooling for Notion AI and the hosted Notion MCP server. Before that, I built PyTorch document AI for bank trade finance at **Intellect Design Arena**.

I care about agents that pick the right tool, evals that block regressions before release, guardrails against prompt injection and data leaks, and inference cost that holds up at scale.

[LinkedIn](https://www.linkedin.com/in/adarshv-av/) · [av.adarshvaranasi@gmail.com](mailto:av.adarshvaranasi@gmail.com)

## Featured: [crmroute](https://github.com/AdarshKirito/crm-agent-routing), a guarded, cost-routed CRM agent

A Salesforce CRM agent on Google ADK and Gemini with two MCP servers, a three-layer data guard and a model router. Evaluated on [CRMArena-Pro](https://github.com/SalesforceAIResearch/CRMArena) against the benchmark's own ReAct agent on the same model, with a held-out test set run once after all tuning:

| Held-out test, 194 tasks per system | Benchmark's ReAct agent | crmroute |
|---|---:|---:|
| Business tasks solved, single-turn (n=114) | 56.1% | **71.1%** |
| Business tasks solved, multi-turn (n=38) | 28.9% | **47.4%** |
| Confidential requests refused (n=42) | 0% | **92.9%** |
| Cost per task (list price) | $0.075 | **$0.028** |

- **Three-layer guard:** screens requests (Prompt Guard 2, Presidio, an LLM policy check), blocks unsafe tool calls, and scrubs PII from answers.
- **Bounded tools and routing:** capped tool output roughly halves tokens per task (103K vs 212K); a nearest-neighbour router sends 47% of business tasks to Gemini Flash-Lite with no measurable loss in success.
- **Measured carefully:** tuned on dev only, paired bootstrap confidence intervals, and a regression eval gate in CI.

[Results and methodology →](https://github.com/AdarshKirito/crm-agent-routing#results-on-the-held-out-test-set)

## Toolbox

- **LLM and agents:** MCP, tool calling, context engineering, RAG, hybrid search, prompt caching
- **Evals and safety:** LLM-as-judge, Braintrust, A/B testing, OpenTelemetry, red teaming, guardrails
- **ML and MLOps:** PyTorch, fine-tuning, LayoutLM, OCR, Docker, Kubernetes, MLflow, CI/CD
- **Languages and platforms:** Python, TypeScript, AWS, Azure, Google Cloud (Vertex AI)
