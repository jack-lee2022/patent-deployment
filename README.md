# Patent Deployment Strategy Skill

A Claude Code skill that translates patent landscape insights into concrete IP filing strategies. Sits at the end of the three-skill pipeline, consuming outputs from patent-mapping to recommend one or more of the five classic deployment modes — then triggering a second-pass search through pro-patent-search to validate the chosen strategy.

## Three-Skill Pipeline

This skill is the **strategy layer** — the final decision stage after data collection and visualization.

```
[1] pro-patent-search          [2] patent-mapping             [3] patent-deployment (this skill)
Search & score patents    →    9 strategy charts         →    Filing strategy + deployment matrix
                                                               ↓ (second-pass search loop)
                               ←──────────────────────────── [1] pro-patent-search (targeted)
```

| Phase | Skill | What it produces |
|-------|-------|-----------------|
| 1. Search & score | [pro-patent-search](https://github.com/jack-lee2022/pro-patent-search) | `*_Patent_List.csv` + audit report |
| 2. Visualize & analyze | [patent-mapping](https://github.com/jack-lee2022/patent-mapping) | 9 strategy charts (tech-effect matrix, competitor radar, evolution timeline, …) |
| 3. Strategize & deploy | **patent-deployment** | Strategy recommendation + deployment matrix + second-pass search triggers |

**Use this skill when you have:**
- Completed patent-mapping and identified Blue Ocean (technology white space) cells
- A specific competitor to defend against or pre-position patents against
- A budget decision to make (wide coverage vs. selective filing vs. defensive publication)

**Use pro-patent-search + patent-mapping without this skill when you only need:**
- A technology landscape overview (no filing action required yet)
- FTO (Freedom to Operate) or invalidity analysis

## Features

- **Five deployment modes** — Stronghold, Fence/Cluster, Carpet, Scarecrow, Choke Point — each with filing SOP and budget guidance
- **Chart-driven strategy selection** — each mode maps to specific patent-mapping outputs (see SKILL.md for full table)
- **Second-pass search loop** — after strategy selection, triggers targeted pro-patent-search queries to confirm White Space or competitor trajectory
- **Defensive publication guidance** — compliant process for putting technology into public domain when filing is not cost-effective

## Quick Start

```
Scenario: 你已完成霧化器技術的搜尋與地圖分析，現在要決定佈局策略

Step 1 (已完成 — pro-patent-search):
  nebulizer_Patent_List.csv

Step 2 (已完成 — patent-mapping):
  - 技術功效矩陣: 發現「網孔振動 × 藥物精準投遞」為 Blue Ocean
  - 競爭者雷達: Lunatech 在 A24F 維度幾乎空白
  - 技術演進時間軸: 網孔振動技術 2015 年才出現，仍在成長期

Step 3 (patent-deployment):
  → 堡壘式: 在「網孔振動 × 藥物精準投遞」Blue Ocean 格搶先申請廣域專利
  → 斷路式: 在 A24F (電子霧化) 方向預埋卡位，封鎖 Lunatech 可能的技術路徑

Step 4 (第二輪 pro-patent-search):
  → 以「vibrating mesh + drug delivery precision」確認空白格無先前技術
  → 以 assignee:Lunatech 搜尋其近期申請，驗證 A24F 進入跡象
```

## Five Deployment Modes

| Mode | Strategy | Best for | Key risk |
|------|----------|----------|----------|
| **Stronghold** | Broad claims on core invention | Breakthrough technology | Single point of failure |
| **Fence/Cluster** | Series of improvement patents around core | Blocking design-arounds | Ongoing maintenance cost |
| **Carpet** | Exhaustive coverage of all embodiments | Standard-setting / full blockade | Very high annuity cost |
| **Scarecrow** | Strategic defensive publication | Limited budget | No exclusivity |
| **Choke Point** | Pre-position at competitor's critical path | Targeting specific competitor | Requires accurate prediction |

## Installation

No additional dependencies — this skill is SOP and strategy guidance only. Requires patent-mapping to have been run first to produce the necessary chart outputs.

## Skill SOP

See `SKILL.md` for the full strategic workflow: Step 0 (data collection) → Step 1 (chart-driven analysis) → Step 2 (strategy assessment) → Step 3 (deployment matrix) → Step 4 (second-pass search).

---

## Five-Skill Workflow Guide

For the complete five-skill orchestration guide (Paths A / B / C), see **[WORKFLOW.md](https://github.com/jack-lee2022/patent-shared/blob/master/WORKFLOW.md)** in patent-shared.