# **SRE Debugging & Automation using MCP Servers**

*A Practical Implementation of AI-Assisted Observability, Debugging, and Workflow Automation*
Developed and Research during my internship


## **Overview**

This repository contains two example **Model Context Protocol (MCP) servers** I built as part of my internship work focused on **SRE (Site Reliability Engineering)**, **observability**, and **AI-powered debugging**.
Due to confidentiality, I cannot share the full internal codebase, infrastructure, or production-grade MCP servers built for Sherlocks.AI. However, this repository showcases:

* The **architecture**,
* The **design patterns**,
* The **concepts**,
* And **two simplified MCP server examples**

…that represent the type of functionality I engineered during my internship.

My actual internship work included advanced integrations with:

* Sentry
* Datadog
* New Relic
* Coralogix
* AWS EKS / ECS / EC2
* Internal engineering APIs
* Custom incident-automation pipelines

# **What I Worked On During the Internship**

During the internship, I developed multiple MCP servers enabling **Claude AI** to directly interact with:

### Cloud Infrastructure

* Query EKS/ECS cluster health
* Analyze pod crashes, deployments, scaling failures
* Recommend remediation steps

### Observability Platforms

* Fetch and interpret real-time KPIs (latency, CPU, 95th percentile, throughput)
* Correlate APM traces (New Relic, Datadog)
* Retrieve logs, errors, alerts, incident states

### Debugging Automation

* Autonomous error triage
* Root-cause summarization using LLMs
* Incident timeline reconstruction
* Automated ticket updates and reporting

### Developer Experience Tools

* Build MCP command interfaces
* Create endpoint schemas for debugging
* Integrate Claude Desktop with MCP servers
* Optimize development workflows using AI

All production versions are private, but the concepts are recreated here.

# **What This Repository Contains**

This repo includes **two simplified MCP servers** illustrating the same concepts I used in production:

### **1. Example JSON MCP Server**

A lightweight MCP server that serves JSON resources with schemas.

**Features:**

* Demonstrates MCP tool definitions
* Shows server registration flow
* Teaches how JSON resources are exposed to Claude
* Useful for configuration debugging

Code: `/json-server/`

---

### **2. Example Directory MCP Server**

A filesystem-based MCP server enabling:

* File search
* File preview
* Directory traversal
* Secure file queries

This mirrors the file-system-observability logic I built internally.

Code: `/directory-server/`

---

# **Architecture I Worked With (High-Level)**

Here is a simplified architecture diagram of the debugging pipeline:

```
Claude Desktop
      |
      ↓
MCP Server (FastAPI / Node)
      |
      ↓
Platform Integrations
(AWS / Datadog / Sentry / NR / Internal APIs)
      |
      ↓
LLM-Powered Debugging
- Incident summaries
- RCA explanations
- Log + metric correlation
- Deployment analysis
```

My work involved building these MCP layers so Claude could perform tasks like:

> “Show me all pods crashing in production in the last 15 min.”
> “Correlate Sentry errors with Datadog CPU spikes.”
> “Explain this stack trace and suggest fixes.”
> “Why is my EKS node not scaling?”
> “Check the 95th percentile latency for today.”

---

# **Why MCP is a Game Changer for SRE**

Model Context Protocol (MCP) turns Claude into an **SRE assistant capable of interacting with real infrastructure**.

### With MCP, Claude can:

* Query observability APIs
* Access server state
* Troubleshoot deployments
* Analyze logs, traces, errors
* Suggest remediation steps
* Correlate multi-source data

It removes the need to switch between 10 dashboards—
**your debugging becomes conversational.**

# **Example Use Cases (from internship work)**

### **Real Incident Scenario**

> “Users are reporting 500 errors. Can you debug?”

Claude (via MCP):

1. Checks EKS pod health
2. Fetches Sentry error spike “DB Connection Timeout”
3. Queries Datadog CPU saturation
4. Correlates deployment history
5. Generates RCA
6. Suggests:

   * Increase DB connection pool
   * Restart affected services
   * Improve readiness probes

# **Installation & Usage**

### Install MCP CLI

```bash
pip install mcp[cli]
```

### Run an example server

```bash
mcp run json-server
```

### Connect to Claude Desktop

Add configuration in:

**Windows:**

```
%APPDATA%\Claude\claude_desktop_config.json
```

**macOS:**

```
~/Library/Application Support/Claude/claude_desktop_config.json
```

Example:

```json
{
  "mcp_servers": {
    "json": {
      "command": "python",
      "args": ["json-server/server.py"]
    }
  }
}
```

# 🛠️ **Tech Stack Used in Real Internship**

While repo shows simplified code, actual work involved:

* **Python / FastAPI for MCP servers**
* Node.js for real-time observability tools
* **Datadog API, Sentry API, NR API, Coralogix API**
* AWS EKS/ECS/EC2 SDKs
* Claude SDK (prompt engineering + tool schemas)
* Structured logging + monitoring
* Async queues + rate limit handling
