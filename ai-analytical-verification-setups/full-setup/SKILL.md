
---
name: fc-fact-checker
description: >
  Rigorous fact-checking and logical verification layer for any Claude response.
  ALWAYS triggered when the user's message starts with the prefix [fc].
  When [fc] is detected, extract the real prompt (everything after [fc]),
  run a full internal verification pipeline — checking all factual claims via web search,
  identifying logical fallacies, detecting cognitive biases and disinformation patterns,
  auditing sources, and correcting hallucinations — before delivering the final verified answer.
  Use this skill unconditionally on [fc] prompts, regardless of topic, length, or apparent simplicity.
---

# [fc] Fact-Checker Skill

A verification-first response pipeline. When `[fc]` is detected, Claude must never generate a final answer from memory alone. Every answerable claim must be checked.

---

## Reference Files

Load these files **only when the pipeline step below calls for them**:

| File | Load when… |
|---|---|
| `references/EPISTEMOLOGY_BASICS.md` | Step 2 — assess burden of proof, evidence level, epistemic status |
| `references/LOGICAL_FLAWS_AND_FALLACIES_SOPHISMS.md` | Step 5 — full fallacy taxonomy (formal, informal, rhetorical, interpersonal) |
| `references/COMPLETE_LIST_OF_COGNITIVE_BIASES_BY_CATEGORY.md` | Step 6 — full categorized bias list |
| `references/SOURCE_EVALUATION_FRAMEWORK.md` | Step 4 — structured source credibility audit |
| `references/SCIENTIFIC_LITERACY_GUIDE.md` | Step 4b — for scientific or statistical claims |
| `references/MISINFORMATION_PATTERNS.md` | Step 7 — detect disinformation construction patterns |
| `references/MEDIA_LITERACY.md` | Step 7 — detect framing, agenda-setting, narrative bias |

---

## Trigger

Message starts with `[fc]` (case-insensitive). Strip the prefix and treat the remainder as the real prompt.

---

## Pipeline (run in this order)

### Step 1 — Parse the Prompt

Identify:
- The **domain** (science, history, tech, law, health, politics…)
- The **claim type**: factual · causal · comparative · definitional · predictive · opinion
- **Named entities**: people, places, products, events, dates, statistics
- The **origin**: is this a claim to verify, or content to generate fresh?

---

### Step 2 — Epistemological Assessment

*Load `references/EPISTEMOLOGY_BASICS.md`.*

Before drafting anything, frame the epistemic status of the claim:

- **Burden of proof**: Who bears it? (Always the person making the extraordinary claim.)
- **Evidence level required**: Proof · Strong · Moderate · Weak · None needed
- **Decidability**: Can this claim be resolved with available data, or is it underdetermined?
- **Bayesian prior**: Does background knowledge make this plausible or implausible? How strong would evidence need to be to update?
- **Epistemic error check**: Is the draft reasoning overconfident? Treating belief as fact? Ignoring uncertainty? Rejecting evidence without justification?

Flag epistemic violations with 🔍.

---

### Step 3 — Extract Verifiable Claims

Generate an internal draft (do NOT output it). Extract every claim that could be wrong:
- Dates, numbers, statistics
- Attributions ("X said…", "X invented…")
- Causal claims ("X causes Y")
- Comparative claims ("X is faster/larger/older than Y")
- Current facts (prices, positions, laws, records)
- Any claim you are less than fully certain about

---

### Step 4 — Source Audit & Web Verification

*Load `references/SOURCE_EVALUATION_FRAMEWORK.md`.*

For **each verifiable claim**, use web search, then evaluate every source against these five criteria:

| Criterion | Key questions |
|---|---|
| **Authority** | Author's qualifications? Recognized in *this specific* domain? |
| **Accuracy** | Claims evidenced? Cross-verifiable? Sources cited? |
| **Transparency** | Methodology disclosed? Limitations acknowledged? Conflicts of interest disclosed? |
| **Independence** | Free from political/commercial bias? Who funds it? |
| **Currency** | Up to date? Timing relevant to this claim? |

Prioritize primary sources (peer-reviewed papers, official institutions, government databases).
Flag sources failing multiple criteria with ⚠️.
Mark unconfirmable claims ⚠️ *unverified*.
**Never skip web search** because you feel confident — confidence is not verification.

#### Step 4b — Scientific/Statistical Claims

*If the claim is scientific or statistical, also load `references/SCIENTIFIC_LITERACY_GUIDE.md`.*

Additional checks:
- **Correlation vs causation**: Is a causal mechanism actually established?
- **Study type hierarchy**: RCT > observational > anecdote — weight evidence accordingly
- **Sample size**: Large enough for reliable conclusions?
- **Statistical vs practical significance**: Effect size matters more than p-values alone
- **Relative vs absolute risk**: Are relative figures inflated without base rates?
- **Consensus alignment**: Does this agree with the body of evidence across multiple studies?

Flag scientific literacy issues with 🔬.

---

### Step 5 — Logical Audit

*Load `references/LOGICAL_FLAWS_AND_FALLACIES_SOPHISMS.md`.*

Run the draft through all six categories in the reference file:

- **I. Formal fallacies** — broken logical structure (affirming the consequent, circular reasoning, equivocation…)
- **II. Relevance fallacies** — off-topic attacks (ad hominem, straw man, red herring, appeal to emotion…)
- **III. Presumption fallacies** — unestablished premises (false dilemma, slippery slope, post hoc, hasty generalization…)
- **IV. Insufficient evidence fallacies** — weak proof (cherry picking, anecdote as evidence, survivorship bias…)
- **V. Rhetorical persuasion techniques** — framing, anchoring, Gish Gallop, moving the goalposts…
- **VI. Interpersonal manipulation techniques** — gaslighting, DARVO, projection, false urgency…

For each flaw: note the category, the specific technique, correct it before output.
Flag with ⚗️.

---

### Step 6 — Cognitive Bias Scan

*Load `references/COMPLETE_LIST_OF_COGNITIVE_BIASES_BY_CATEGORY.md`.*

Scan the full categorized list. Start with high-frequency disinformation biases:

| Bias | How disinformation exploits it |
|---|---|
| **Confirmation bias** | Targets already-convinced audiences; filters contradicting data |
| **Illusory truth effect** | Repetition makes false claims feel self-evident |
| **Availability heuristic** | Dramatic/emotional events overweighted as representative |
| **Anchoring bias** | False narrative frame set early to constrain interpretation |
| **In-group bias** | "Us vs. them" framing suppresses critical evaluation |
| **Dunning-Kruger exploitation** | Overconfident non-experts used as credibility proxies |
| **Base rate neglect** | Base frequencies ignored to dramatize a statistic |
| **Survivorship bias** | Only favorable cases shown to support the thesis |
| **Hindsight bias** | History rewritten to validate false predictions |

Then consult the full reference file for any remaining applicable biases.
Flag detections with 🧠.

---

### Step 7 — Disinformation & Media Pattern Check

*Load `references/MISINFORMATION_PATTERNS.md` and `references/MEDIA_LITERACY.md`.*

**Disinformation construction patterns** (MISINFORMATION_PATTERNS.md):
- Cherry picking · False balance · Misleading framing · Emotional manipulation
- Out-of-context quotes · Selective timelines · Misleading statistics
- Simplified "good vs. bad" narratives · Intent assignment without evidence
- Repetition to create perceived truth · Gish Gallop / information overload
- "Hidden truth" claims without evidence · Dismissal of all opposing evidence

**Media manipulation patterns** (MEDIA_LITERACY.md):
- **Framing** — presentation that constrains interpretation
- **Agenda setting** — topics foregrounded or suppressed
- **Narrative bias** — simplification for engagement over accuracy
- **Sensationalism** — exaggeration to attract attention
- **Headline vs content gap** — does the headline actually match the article?

Flag detections with 🗞️.

---

### Step 8 — Compose Final Answer

Write the final, corrected response:
- All factual errors fixed
- Unverified claims flagged with ⚠️
- Epistemic status labeled where it matters
- Logical fallacies removed or noted
- Biases and disinformation patterns surfaced
- Followed by the verification summary below

---

## Output Format

```
[Verified, corrected response]

---
**[fc] Verification Summary**
- ✅ Verified: [confirmed claims]
- ⚠️ Unverified: [claims that could not be confirmed — treat with caution]
- ❌ Corrected: [claims that were wrong in the draft, now fixed]
- 🔍 Epistemic: [burden of proof issues, overconfidence, underdetermined claims — or "No issues"]
- ⚗️ Logic: [fallacies or manipulation techniques found — or "No issues found"]
- 🧠 Biases: [cognitive biases detected — or "None detected"]
- 🗞️ Disinfo/Media: [patterns detected — or "None detected"]
- 🔬 Science: [study type issues, stat misuse, consensus conflicts — or "N/A"]
- 📚 Sources: [flagged sources — or "Sources adequate"]
```

Clean result shorthand: *"All claims verified. No logical, epistemic, bias, or disinformation issues found."*

---

## Rules

- **Never skip web search** because you feel confident — `[fc]` exists to catch exactly those confident-but-wrong moments.
- **Never hallucinate sources**. No result = say so explicitly.
- **Do not use unverified claims** as stepping stones to further conclusions.
- **Flag uncertainty explicitly** — "I could not confirm this" is better than presenting something unverified as fact.
- **If the prompt is purely logical/mathematical**, skip web search; focus on Steps 5 and 6.
- **If the prompt is opinion-based**, verify any factual premises it rests on, then label the opinion clearly.
- **Keep the verification note honest** — do not write "all verified" if you skipped any claims.
- **Apply bias and fallacy detection to your own reasoning**, not just to external sources.
- **Load reference files only as needed** per the table at the top — do not load all of them upfront.
  
  