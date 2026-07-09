---
name: magic-analysis
description: "Use when the user wants a comprehensive fate/destiny analysis combining Chinese Bazi (八字), Western astrology, Tarot archetypes, Buddhist/Taoist philosophy for one or two people. Triggers on: 'analyze my bazi', 'fate analysis', '命理分析', 'eight characters reading', 'analyze our compatibility', '分析八字', 'magic analysis', birth chart analysis requests."
---

# Magic Analysis

Deep multi-tradition fate analysis: Chinese Bazi + Western astrology + Taoist/Buddhist philosophy. Produces both a `.md` report and a dark-themed PPT-style `.html` slide deck.

---

## Step 1 — Gather Input

Ask the user to provide (for each person):
- **Birth date** (year / month / day)
- **Birth time** (hour, or approximate: morning / afternoon / evening / unknown)
- **Gender**
- **Any Bazi排盘 screenshot** (from apps like h5.40dhjien.cn) — if provided, extract all fields directly from the image

If birth time is unknown, note it and proceed with a 3-pillar reading, flagging which conclusions are uncertain.

Identify **who is who** from context (names, pronouns, "me vs. partner").

---

## Step 2 — Extract & Verify Data

From排盘 images or manual input, extract:

| Field | Where to find |
|-------|--------------|
| 四柱 (Four Pillars) | 天干地支 for year/month/day/hour |
| 日元 (Day Master) | 日柱天干 — the person's core element |
| 十神 (Ten Gods) | 主星/副星 columns |
| 五行占比 | 五行分数 section |
| 喜用神 / 忌神 | 五行信息 section |
| 大运 (Major Luck Cycles) | 大运 tab — current + upcoming |
| 流年 (Annual Luck) | 流年 tab |
| 神煞 (Special Stars) | 神煞 section: 文昌, 驿马, 羊刃, 桃花, etc. |
| 星座 (Western sign) | 基本 tab |
| 二十八宿 | 基本 tab |
| 称骨重量 | 基本 tab |
| 命宫 / 胎元 / 身宫 | 基本 tab |

---

## Step 3 — Analysis Framework

Apply **all four traditions** in every domain. Do not skip traditions even if data is sparse.

### Four Traditions

**Chinese Bazi (八字)**
- Day Master strength: 旺衰法 (strong vs. weak)
- Pattern/格局: what the chart is "built for" (食伤生财, 正官格, 从强格, etc.)
- Current luck cycle intersection with natal chart
- Key gods: 喜用神 feeding vs. 忌神 draining
- 神煞 effects (both positive and negative — never list only positives)

**Taoist / Buddhist Layer**
- 水火既济 / 阴阳 balance metaphors (道德经 quotes where apt)
- 五行 karma narrative: what element excess/deficiency means about life lessons
- Buddhist业力 framing for crisis patterns (飞刃, 无恩刑, etc.)
- Practical道家 remedies: colors, directions, objects, rituals

**Western Astrology**
- Sun sign character synthesis with Day Master (confirm or tension)
- 2026–2035 outer planet transits relevant to the chart
- White羊/处女/etc. compatibility角度 for couples
- Aspect between two charts if doing合盘 (conjunction, sextile, square, opposition)

**Tarot Archetype**
- Assign each person 1–2 Major Arcana cards that match their natal pattern
- Explain WHY the card fits (not generic card meaning — tie to specific chart features)
- For couples: a relationship card
- Current year card (流年 mapped to tarot)

### Analysis Domains

For **each person** cover all six:

| Domain | Key questions |
|--------|--------------|
| 格局/性格 | Core archetype, strengths, shadow side |
| 事业 | Career direction, peak years, risks |
| 财运 | Income style, wealth accumulation, danger years |
| 感情/婚姻 | Relationship patterns, best timing, red flags |
| 健康 | Organ systems at risk, trigger seasons, prevention |
| 人生功课 | The one lesson this chart keeps presenting |

For **couples** add:
- 天干合/地支组合 table
- 五行互补 analysis
- Astrology aspect + compatibility score (X/10 with reasoning)
- Taoist合卦 metaphor
- Shared risks in high-pressure years
- Communication style clash + concrete bridge

---

## Step 4 — Objectivity Rules

**Mandatory balance:** Every domain must include both positive and negative findings. If a domain has no negatives, re-examine — you missed something.

**Quantify risk levels:** Use A / B / C tiers for crises:
- **A级**: High probability + high impact — requires concrete action plan
- **B级**: Medium probability or medium impact — monitor + prepare
- **C级**: Low probability but worth noting — awareness only

**No fortune-telling tone.** Frame as: "This configuration tends to produce X pattern. The risk is Y. The lever to change outcomes is Z."

**Show the math:** When citing a crisis, name the exact configuration causing it (e.g., "午午自刑", "劫财+羊刃", "伤官见官") so the reader can verify.

---

## Step 5 — Output Files

Generate **two files** in the folder the user specifies (default: same folder as input images, or `~/Desktop/magic_analysis/`).

### File 1: `命理全析_[Name].md`

Structure:
```
# 命理全析报告
## 排盘数据汇总
## [Person A] 个人全析
  - 八字格局
  - 性格特质（正面 + 负面）
  - 事业财运
  - 感情婚姻
  - 健康隐患
  - [星座] 视角
  - [二十八宿] 视角
  - 塔罗原型
  - 人生功课
## [Person B] 个人全析  (if couple)
  - (same sections)
## 合盘分析  (if couple)
  - 天干合分析
  - 地支组合表
  - 五行互补
  - 星座合盘
  - 道家/佛教视角
## 流年大运详解 (year-by-year table, current year to +10)
## 危机清单与化解方案 (A/B/C级)
## 综合结论
```

### File 2: `命理全析_[Name].html`

Dark-themed PPT slide deck. **Do not auto-open after creation.**

#### Required Slides

| # | Title | Content |
|---|-------|---------|
| 1 | Cover | Day Master symbols + names + traditions banner + date |
| 2 | Data Overview | Side-by-side data cards (both people if couple) |
| 3 | Four Pillars | Visual 天干地支 columns + five-element bar charts |
| 4 | Person A Deep Analysis | 3×2 grid of 6 domain blocks |
| 5 | Person B Deep Analysis | 3×2 grid (if couple) |
| 6 | Compatibility | Avatar pair + compat scores + key points (if couple) |
| 7 | Luck Timeline | Year-by-year table with ★ ratings + color tags |
| 8 | Crisis & Solutions | A/B/C-level crisis cards with fixes |
| 9 | Conclusion | Final verdict cards + closing quote |

#### HTML Design System

```css
/* Color palette */
--dark-bg: #0d0d1a
--water-accent: #4a9eca    /* 壬/癸水 */
--fire-accent: #e05c00     /* 丙/丁火 */
--gold: #c9a84c            /* headings, borders */
--wood: #5ba85b
--metal: #c0c0d0
--earth: #c8a85e
--text-primary: #e8e0d0
--text-muted: rgba(200,200,200,0.6)
--pro-green: #7dd17d
--warn-yellow: #f0c060
--danger-red: #e87070
```

Adapt water/fire accent colors to match the Day Masters being analyzed (e.g., 甲木 → use wood green as primary, 庚金 → use metal silver).

**Typography:** `Noto Serif SC` for headings/titles, `Noto Sans SC` for body.

**Cards:** `background: rgba(255,255,255,0.03)`, `border-radius: 12–16px`, `border: 1px solid rgba(gold, 0.2)`. Domain-specific cards get tinted background matching their element.

**Navigation:** Fixed bottom nav bar (← prev / counter / next →) + right-side dot indicators + keyboard arrow support + touch swipe.

**Tags inside cards:**
```html
<span class="tag tag-pro">✦ positive finding</span>
<span class="tag tag-con">✗ risk/negative</span>
<span class="tag tag-warn">⚠ caution</span>
```

**Crisis card levels:**
- A级: red left border + subtle red background
- B级: yellow left border + subtle yellow background  
- C级: green left border + subtle green background

**Do not** add an auto-open script. File is dropped in the target folder only.

---

## Step 6 — Deliver

1. Confirm both files created successfully with paths
2. Give a 5-line verbal summary:
   - One sentence on Person A's core archetype
   - One sentence on Person B's core archetype (if couple)
   - The single most important risk for the current year
   - The single best opportunity in the next 3 years
   - One relationship insight (if couple)

---

## Common Mistakes

| Mistake | Fix |
|---------|-----|
| Only listing positives | Every domain needs negatives — chart the shadow |
| Generic tarot meanings | Tie card to specific chart features, not textbook definition |
| Ignoring忌神 in luck analysis | Check each year's stem/branch against喜忌神 first |
| Missing神煞 effects | Scan all神煞 and note both positive (文昌, 天乙) and negative (飞刃, 五鬼, 无恩刑) |
| Vague "take care of health" advice | Name the specific organ system + trigger season + one concrete action |
| Skipping the Taoist/Buddhist layer | Even 2–3 sentences per person grounds the reading in philosophy |
| Auto-opening the HTML file | Never open the file — just report the path |
| Flat year-by-year table with no standout years | Highlight 2–3 peak years and 1–2 danger years with color tags |
