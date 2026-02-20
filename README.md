# CrewAI Multi-Agent Systems

A collection of autonomous AI crews built with [CrewAI](https://crewai.com) for market research, competitive intelligence, and content generation. Each crew orchestrates specialized agents that collaborate on complex, multi-step tasks.

---

## Table of Contents

- [Overview](#overview)
- [Crews](#crews)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [Outputs](#outputs)
- [Tech Stack](#tech-stack)
- [License](#license)
- [Support](#support)

---

## Overview

This repository contains two end-to-end CrewAI implementations:

| Crew | Description |
|------|-------------|
| **Market Research Crew** | Full market analysis pipeline for AI product ideas—market sizing, competitive intelligence, customer insights, product strategy, and business recommendations |
| **Research and Blog Crew** | Research-to-content pipeline: topic research → structured report → polished blog post |




### Market Research Crew

5 agents work in sequence to deliver a full business analysis report:

| Agent | Role | Responsibility |
|-------|------|----------------|
| Market Research Specialist | Market analyst | TAM/SAM/SOM, growth trends, industry dynamics, regulatory landscape |
| Competitive Intelligence Analyst | Competitor analyst | Direct/indirect competitors, positioning, gaps, threats |
| Customer Insights Researcher | Customer researcher | Personas, pain points, journeys, acquisition channels |
| Product Strategy Advisor | Product strategist | MVP scope, differentiation, technical feasibility, roadmap |
| Business Analyst | Report synthesizer | Pricing, revenue model, risk analysis, go/no-go recommendation |

**Tools:** SerperDevTool, ScrapeWebsiteTool, SeleniumScrapingTool

### Research and Blog Crew

2 agents work in sequence:

| Agent | Role | Responsibility |
|-------|------|----------------|
| Report Generator | Researcher | Deep-dive research on the given topic |
| Blog Writer | Content writer | Turns research into a structured, reader-friendly blog post |

---

## Prerequisites

- **Python:** >= 3.10, < 3.14
- **Package manager:** [UV](https://docs.astral.sh/uv/) (recommended) or pip
- **API keys:**
  - `OPENAI_API_KEY` (required)
  - `SERPER_API_KEY` (required for Market Research Crew)

---

## Installation

### 1. Clone the repository

```bash
git clone <repository-url>
cd CrewAI-End-to-End
```

### 2. Install UV (optional but recommended)

```bash
pip install uv
```

### 3. Install a crew

Each crew has its own `pyproject.toml`. Install dependencies for the crew you want to run:

**Market Research Crew:**
```bash
cd market_research_crew
uv sync
# or
crewai install
```

**Research and Blog Crew:**
```bash
cd research_and_blog_crew
uv sync
# or
crewai install
```

---

## Configuration

### Environment variables

Create a `.env` file in the crew directory:

```env
OPENAI_API_KEY=your_openai_api_key
SERPER_API_KEY=your_serper_api_key    # For Market Research Crew
```

### Customization

- **Agents:** Edit `config/agents.yaml` (roles, goals, backstories)
- **Tasks:** Edit `config/tasks.yaml` (descriptions, expected outputs)
- **Crew logic:** Edit `crew.py` (agents, tasks, tools)
- **Inputs:** Edit `main.py` (product idea, topic, etc.)

---

## Usage

Run from the root of each crew directory:

### Market Research Crew

```bash
cd market_research_crew
crewai run
```

Default input: AI product idea for market analysis (editable in `main.py`).

### Research and Blog Crew

```bash
cd research_and_blog_crew
crewai run
```

Default input: topic `"AI agents in coding"` (editable in `main.py`).

---

## Outputs

| Crew | Output location | Format |
|------|-----------------|--------|
| Market Research Crew | `market_research_crew/reports/report.md` | Markdown report |
| Research and Blog Crew | `research_and_blog_crew/blogs/blog.md` | Markdown blog post |

---

## Tech Stack

- [CrewAI](https://crewai.com) — Multi-agent orchestration
- [CrewAI Tools](https://github.com/joaomdmoura/crewai-tools) — SerperDevTool, ScrapeWebsiteTool, SeleniumScrapingTool
- Python >= 3.10
- [UV](https://docs.astral.sh/uv/) — Dependency management

---

## License

This project is licensed under the MIT License — see [LICENSE](LICENSE) for details.

Copyright © 2026 Suresh Beekhani

---

## Support

- [CrewAI Documentation](https://docs.crewai.com)
- [CrewAI GitHub](https://github.com/joaomdmoura/crewai)
- [CrewAI Discord](https://discord.com/invite/X4JWnZnxPb)
