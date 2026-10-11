### I build LLM agents that are reliable, safe and cost-efficient in production.

Software Engineer, AI Platform at **Notion**, working on shared LLM services and agent tooling for Notion AI and the hosted Notion MCP server. Before that, I built PyTorch document AI for bank trade finance at **Intellect Design Arena**.

I care about agents that pick the right tool, evals that block regressions before release, guardrails against prompt injection and data leaks, and inference cost that holds up at scale.

[LinkedIn](https://www.linkedin.com/in/adarshv-av/) · [av.adarshvaranasi@gmail.com](mailto:av.adarshvaranasi@gmail.com)

## Featured: [crmroute](https://github.com/AdarshKirito/crm-agent-routing), a guarded, cost-routed CRM agent

A research prototype: a Salesforce CRM agent on Google ADK and Gemini with two MCP servers, a data guard and a model router. I evaluated it on [CRMArena-Pro](https://github.com/SalesforceAIResearch/CRMArena) against the benchmark's own ReAct agent on the same model (Gemini 3.8 Flash), with a held-out test set run once after tuning on dev. It has had no real users; every number comes from the benchmark's templated tasks.

| Held-out test, 194 tasks per system | ReAct | ReAct + privacy prompt | crmroute |
|---|---:|---:|---:|
| Business tasks solved, single-turn (n=114) | 56.1% | 50.0% | 71.1% |
| Business tasks solved, multi-turn (n=38) | 28.9% | 21.1% | 47.4% |
| Confidential requests refused (n=42) | 0% | 59.5% | 92.9% |
| Cost per task (list price) | $0.075 | $0.073 | $0.028 |

- **What holds up:** crmroute's leads over ReAct with its privacy prompt are all significant, and it costs about 60% less per task. Against plain ReAct, the business-task lead stops being significant if the 11 ReAct business tasks stopped by a 250K-token cap I set had succeeded, and crmroute's prompts carry hints tuned on the benchmark's dev tasks that ReAct's do not.
- **Guard:** in customer sessions, a small-model policy check with Presidio and a sensitive-field map, a tool-call guard and a PII scrub. Prompt Guard 2 is wired in but untested here.
- **Cost:** bounded tool results, and a nearest-neighbour router with a routing table fitted on dev that sends 47% of business tasks to Gemini Flash-Lite, with no measurable change in success.
- **Evaluation:** fixed dev/test splits, paired bootstrap intervals, pinned run manifests, and a local 8B judge checked against 40 reviewed labels.

[Results, method and limitations →](https://github.com/AdarshKirito/crm-agent-routing#results-in-brief)

## Toolbox

- **LLM and agents:** MCP, tool calling, context engineering, RAG, hybrid search, prompt caching
- **Evals and safety:** LLM-as-judge, Braintrust, A/B testing, OpenTelemetry, red teaming, guardrails
- **ML and MLOps:** PyTorch, fine-tuning, LayoutLM, OCR, Docker, Kubernetes, MLflow, CI/CD
- **Languages and platforms:** Python, TypeScript, AWS, Azure, Google Cloud (Vertex AI)
