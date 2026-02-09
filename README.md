# 🐝 HiveLoop

**Multi-Agent Orchestration Pattern for AI-Assisted Development**

> HiveLoop is an open-source framework for coordinating multiple AI agents to work on software projects in parallel while preventing context degradation.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

---

## 🎯 What is HiveLoop?

HiveLoop is a **multi-agent execution pattern** that enables:

- **Parallel AI agent execution** — Multiple specialist agents work simultaneously
- **Fresh context per agent** — Each agent starts clean, preventing "context rot"
- **Orchestrated coordination** — A lead agent manages task distribution and aggregation
- **Self-improving workflows** — Patterns discovered during execution are captured and reused

```
┌─────────────────────────────────────────┐
│           ORCHESTRATOR AGENT            │
│   • Analyzes project state              │
│   • Spawns specialist subagents         │
│   • Aggregates results                  │
│   • Updates progress tracker            │
└─────────────────────────────────────────┘
                    │
    ┌───────────────┼───────────────┐
    ▼               ▼               ▼
┌─────────┐   ┌─────────┐   ┌─────────┐
│FRONTEND │   │BACKEND  │   │VERIFY   │
│  Agent  │   │  Agent  │   │  Agent  │
└─────────┘   └─────────┘   └─────────┘
```

---

## 🚀 Quick Start

### 1. Copy the template files to your project

```bash
# Clone or download HiveLoop
git clone https://github.com/mirrorfolio-idea-labs/hiveLoop.git

# Copy templates to your project
cp -r hiveloop/templates/* your-project/.hiveloop/
```

### 2. Customize anchor documents

Edit the files in `your-project/.hiveloop/`:

1. **`prd.md`** — Your project requirements
2. **`tech_stack.md`** — Your technology choices
3. **`conventions.md`** — Your coding standards
4. **`implementation_plan.md`** — Your task breakdown

### 3. Run HiveLoop

Start your AI assistant and load the orchestrator prompt:

```
Load: .hiveloop/orchestrator.md
Execute HiveLoop iteration
```

---

## 📁 Repository Structure

```
hiveloop/
├── README.md                 # This file
├── LICENSE                   # MIT License
├── CONTRIBUTING.md           # Contribution guidelines
│
├── docs/                     # Core documentation
│   ├── concepts.md           # Core concepts explained
│   ├── getting-started.md    # Detailed setup guide
│   ├── agent-types.md        # Available agent types
│   ├── evaluation.md         # Metrics and evaluation
│   └── troubleshooting.md    # Common issues
│
├── core/                     # Core HiveLoop system
│   ├── orchestrator.md       # Lead agent configuration
│   ├── agent-prompts.md      # Specialist agent templates
│   ├── coordination.md       # Inter-agent protocols
│   ├── workflow.md           # Execution protocol
│   └── evaluation.md         # Metrics framework
│
├── templates/                # Ready-to-use templates
│   ├── prd.md                # Product requirements template
│   ├── tech_stack.md         # Tech stack template
│   ├── conventions.md        # Conventions template
│   ├── implementation_plan.md # Task planning template
│   └── progress_tracker.md   # Progress tracking template
│
└── examples/                 # Example configurations
    ├── web-app/              # Web application example
    ├── mobile-app/           # Mobile app example
    ├── api-service/          # API/backend example
    └── monorepo/             # Monorepo example
```

---

## 🧠 Core Concepts

### The Problem: Context Rot

When AI assistants work on long tasks, their output quality degrades as the context window fills up. This is called **context rot**.

### The Solution: Fresh Sessions + Parallel Execution

HiveLoop solves this by:

1. **Starting fresh** — Each agent begins with empty context
2. **Loading anchors** — Agents load standardized project documents
3. **Working in parallel** — Multiple agents execute simultaneously
4. **Aggregating results** — Orchestrator merges outputs and tracks progress

### When to Use HiveLoop

| Scenario | Recommendation |
|----------|----------------|
| Simple task (<30 min) | Single agent |
| Multiple independent tasks | HiveLoop (2-3 agents) |
| Full feature development | HiveLoop (3-5 agents) |
| Complex system changes | HiveLoop + Integration agent |

---

## 🤖 Agent Types

| Agent | Specialization |
|-------|----------------|
| **Orchestrator** | Coordinates all agents, manages state |
| **Frontend** | UI/UX, client-side code |
| **Backend** | APIs, databases, server logic |
| **DevOps** | Infrastructure, CI/CD, deployment |
| **Verification** | Testing, validation, quality |
| **Integration** | Cross-stack coordination |
| **Documentation** | Docs, comments, README |

---

## 📊 Key Metrics

| Metric | Target | Description |
|--------|--------|-------------|
| Task Completion | >90% | Tasks completed per iteration |
| First-Try Success | >70% | Tasks passing without retry |
| Context Rot Score | >90 | Quality preservation measure |
| Token Efficiency | <30K/task | Tokens used per task |

---

## 📄 License

MIT License — see [LICENSE](./LICENSE)

---

## 🤝 Contributing

See [CONTRIBUTING.md](./CONTRIBUTING.md) for guidelines.

---

## 🔗 Related Projects

- [Ralph Loop](https://blog.mirrorfolio.com/the-ralph-loop-an-engineering-grade-pattern-for-reliable-ai-assisted-software-development) — Single-agent predecessor
- [Anthropic Research Agents](https://www.anthropic.com/engineering/multi-agent-research-system) — Multi-agent research

---

**Built with 🐝 by the community**
