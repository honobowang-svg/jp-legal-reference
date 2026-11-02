# 日本法律参考アシスタント · Architecture（単一 Bot 内部分診）

> Workspace: `/workspace/global-law-agents/jp/`  
> Free public **legal reference** knowledge base（法律意見ではない）。  
> **1** つの Grok Bot で内部ルーティング（複数 Bot ではない）。  
> 改訂: 2026-11-02（Asia/Shanghai）

---

## 1. Design goals

1. Mirror China pack (`falv-pub`) and US pack (`global-law-agents/us`): master prompt + 11 branches × 5 files.
2. **National-law first** triage; ask **prefecture / court location** when minimum wage, ordinances, or venue matter.
3. Criminal = rights/procedure only; immigration = reference only.
4. Never fabricate statutes; mark gaps **`【要確認】`**.
5. Joint custody reform (令和6年法律第33号) documented with **2026-04-01** effective date from MOJ.

---

## 2. Runtime assembly

| Layer | File(s) | Role |
|-------|---------|------|
| Instructions | `bot_master_prompt.md` | Persona, triage, routing, refusals, disclaimer |
| Branch playbooks | `*/system_prompt.md` | Scope, refuse list, flow |
| Knowledge | `*/knowledge_base.md` | Cited statutes / official portals |
| Tools | `*/calculators.md` | Formulas (OT, MW, inheritance shares, notice pay, interest) |
| Clocks | `*/deadlines.md` | Limitation / procedure clocks |
| Forms | `*/templates.md` | Checklists / letter skeletons |
| QA (optional) | `test_cases.md`, `eval_report.md` | Do **not** attach as user-facing knowledge unless testing |

---

## 3. Triage sequence

```
User question
  → Ask key facts (+ prefecture/court when relevant)
  → Route to one of 11 categories
  → Load that branch five-pack
  → Answer with citations + disclaimer (answer language)
```

---

## 4. Coverage policy

| Tier | Content |
|------|---------|
| National | Civil Code, Labor Standards Act, Code of Civil Procedure, Consumer Contract Act, etc. via e-Gov |
| Prefectural snapshots | Regional minimum wage table (MHLW Reiwa 8 FY); ordinance pointers |
| Local venue | Courts.go.jp self-help; Houterasu |

---

## 5. Safety rails

- No sentence prediction / crime-evasion / evidence destruction.
- No guaranteed immigration outcomes; no false filing coaching.
- No fake statute numbers.
- Every answer ends with disclaimer (§7 of master prompt).

---

## 6. Maintenance

When a statute amends: update the branch `knowledge_base.md` quote + date line; bump calculator tables (esp. minimum wage each autumn); add a regression case to `test_cases.md`.
