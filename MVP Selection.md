# MVP Selection: Strategic Evaluation & Rationale
### Problem Space -> Product Decision

> Build a **Variance Commentary Agent** — a digital co-worker that transforms
> two spreadsheets into draft management commentary in minutes. It sits at the intersection
> of maximum pain, maximum LLM fit, minimum integration complexity, and maximum strategic
> positioning for Lyzr.

---

## 1. Evaluation Framework

Five candidates emerged from the problem framing. Each is scored on seven dimensions (1–5 scale):

| Criterion | Weight | Why It Matters |
|---|---|---|
| **Market Gap** | 25% | Is there an existing solution? White space = higher defensibility |
| **LLM-Native Fit** | 20% | Does the use case play to LLM strengths (reasoning, text gen)? |
| **Lyzr Product Fit** | 20% | Can Architect + GitClaw deliver this without heavy custom eng? |
| **Engineering Feasibility** | 15% | Can a lean team build an MVP in weeks, not months? |
| **Demo Impact** | 10% | Can you feel the value in 30 seconds? |
| **Expansion Potential** | 10% | Does it lead to broader CFO office adoption? |

### Scoring Matrix

| Use Case | Market Gap | LLM Fit | Lyzr Fit | Eng. Feasibility | Demo Impact | Expansion | **Weighted** |
|---|---|---|---|---|---|---|---|
| **Variance Commentary** | 5 | 5 | 5 | 5 | 5 | 4 | **4.85** |
| Account Reconciliation | 3 | 3 | 4 | 3 | 4 | 5 | 3.50 |
| Close Orchestration | 3 | 2 | 3 | 3 | 2 | 4 | 2.80 |
| Journal Preparation | 3 | 3 | 3 | 2 | 3 | 4 | 2.95 |
| Regulatory Returns | 4 | 3 | 3 | 2 | 2 | 2 | 2.85 |

```
SCORE DISTRIBUTION:

Variance Commentary  ████████████████████████████████████████████████░░  4.85
Journal Preparation  █████████████████████████████░░░░░░░░░░░░░░░░░░░░  2.95
Regulatory Returns   ████████████████████████████░░░░░░░░░░░░░░░░░░░░░  2.85
Close Orchestration  ████████████████████████████░░░░░░░░░░░░░░░░░░░░░  2.80
Account Recon        ███████████████████████████████████░░░░░░░░░░░░░░░  3.50
                     0          1          2          3          4          5
```

**Variance Commentary wins on every dimension.** Let me justify each score.

---

## 2. Why Variance Commentary Scores 5/5 on Market Gap

### Competitive Landscape

| Player | What It Solves | What It Doesn't Do |
|---|---|---|
| **BlackLine** ($1.5B rev) | Reconciliation matching, close task management | No commentary generation, no AI reasoning |
| **FloQast** (acq. $1.8B) | Close management, workflow orchestration | No narrative generation, no autonomous execution |
| **Workiva** | SEC filing, document management | External reporting only, not operational |
| **MS Copilot for Finance** | Q&A chatbot over financial data | Answers questions — doesn't PRODUCE deliverables |
| **Datarails** | FP&A consolidation, Excel integration | Planning/budgeting focused, no close commentary |
| **ChatGPT / Claude** | General-purpose text generation | No financial context, no workflow, no audit trail |

```
                    AUTONOMOUS EXECUTION
                    (Agent produces deliverables)
                         │
                         │  ★ Lyzr Variance
                         │    Commentary Agent
                         │                      Macquarie
                         │                      Project Nexus
                         │                      (internal only)
                         │
    NARROW ──────────────┼──────────────────── BROAD
    (single process)     │                    (general purpose)
                         │
                  Vic.ai │         MS Copilot
               (AP only) │         for Finance
                         │
              BlackLine  │
              FloQast    │         ChatGPT/Claude
                         │
                    WORKFLOW AUTOMATION
                    (Human still does the work)
```

**Nobody generates variance commentary.** Every finance team does it manually. This is genuine white space.

---

## 3. Why Lyzr Product Fit Is Perfect

### Architect Capability Mapping

| Architect Feature | How It's Used for Variance Commentary |
|---|---|
| Natural language → agent + UI | Manager describes process → gets working co-worker |
| **Workflow agent** (deterministic) | Data parsing, variance calculation, materiality filtering |
| **Manager agent** (reasoning) | Commentary generation, exception triage, context assembly |
| Generated Next.js frontend | Review UI with variance table, editable commentary, approval buttons |
| Gmail/Slack integration | Notify supervisor when draft is ready, distribute approved commentary |
| Built-in Control Plane | Track accuracy rates, processing times, approval metrics |

### GitClaw Governance Mapping

| GitClaw Pattern | Finance Requirement It Satisfies |
|---|---|
| Pattern 1: Human-in-the-loop via PRs | Supervisor reviews/approves all commentary before distribution |
| Pattern 2: Agent Versioning | Commentary rules versioned — "why did the format change?" |
| Pattern 5: Live Agent Memory | Agent remembers: "Account 4520 variance was due to lease renewal last quarter" |
| Pattern 6: Audit Trail | Every edit, approval, and distribution is cryptographically signed |
| Pattern 9: CI/CD for Agents | Quality gates: do numbers in commentary match source data? |
| Pattern 14: SOD | Agent = maker, supervisor = checker — enforced by infrastructure |

### Hallucination Manager — Critical Integration

Variance commentary has a **zero-tolerance requirement** for numerical accuracy. The numbers cited in narrative MUST match the source data. Lyzr's Hallucination Manager provides:

| Check | Method | Threshold |
|---|---|---|
| Numerical accuracy | Extract numbers from text, compare to source | 100% match required |
| Directional correctness | "Increased" must align with positive variance | 100% match required |
| Completeness | All material items above threshold must have commentary | 100% coverage |
| Causal plausibility | LLM-as-judge: "Is this explanation reasonable?" | >90% confidence |

---

## 5. Engineering Feasibility: Why File-Based Is Strategically Correct

The MVP requires **zero ERP integration**. Here's why:

```
CURRENT STATE (without agent):
ERP → [Human exports to Excel, 10 sec] → Excel → [Human analyzes, 4 hrs] → Commentary

WITH AGENT:
ERP → [Human exports to Excel, 10 sec] → Upload to Agent → [Agent, 2 min] → Draft → [Human reviews, 30 min]
                                          ▲
                                          │
                                    THIS IS THE MVP
                                    No ERP connector needed
                                    Just process what the human
                                    already exports
```



---

## 6. Market Sizing

### Bottom-Up

| Parameter | Value | Source |
|---|---|---|
| Companies with monthly close | ~50,000 (US mid-market + enterprise) | APQC |
| Avg material line items per close | 30–50 | Industry benchmark |
| Avg time per commentary item | 20–40 min | Deloitte Finance Benchmarking |
| Total analyst hours per close | 10–33 hrs per entity | Calculated |
| Analyst cost | $50–80/hr fully loaded | Glassdoor + benefits |
| **Monthly cost per entity** | **$500–$2,600** | Calculated |
| Avg entities per company | 5–50 | Varies by size |
| **Annual spend per company** | **$30K–$1.5M** | Calculated |
| **Total addressable market** | **$1.5B–$7.5B** | 50K companies × avg spend |


---

## 7. Variance Commentary as Entry Point

Variance commentary is the **minimum risk entry point** that leads to full CFO office adoption:

```
TRUST LEVEL    USE CASE                   RISK        LYZR PRODUCT
─────────────────────────────────────────────────────────────────────

Level 1        Variance Commentary        LOW         ← MVP
"Show me"      (human reviews text        (no GL      
                before anyone sees it)     impact)    

Level 2        Account Reconciliation     MEDIUM      ← 3-6 months
"Help me"      (matching has right/wrong  (identifies 
                answers to verify)         errors)    

Level 3        Journal Preparation        HIGH        ← 6-12 months
"Do it"        (directly impacts GL —     (direct GL  
                requires deep trust)       posting)   

Level 4        Multi-Agent Co-Worker      HIGHEST     ← 12+ months
"Run the team"  Team (portfolio of agents (full process
                across CFO office)        ownership)  
```



---
