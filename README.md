<p align="center">
<img width="322" height="480" alt="gif" src="https://github.com/user-attachments/assets/2fad77d6-5006-4840-a9fb-22569f3fa1b6" />
</p>
  

<h1 align="center">ai-misinformation-toolkit</h1>

<p align="center">
A reproducible, open-source toolkit for building and configuring AI assistants specialized in detecting, explaining, and preventing misinformation — through bias analysis, source evaluation, logical auditing, and structured reasoning.
</p>

<p align="center">
  <a href="#-what-this-is">What this is</a> ·
  <a href="#-repo-structure">Structure</a> ·
  <a href="#-quick-start">Quick Start</a> ·
  <a href="#-the-two-setups">The Two Setups</a> ·
  <a href="#-reference-documents">Reference Documents</a> ·
  <a href="#-the-fc-skill">The [fc] Skill</a> ·
  <a href="#-examples">Examples</a> ·
  <a href="#-contributing">Contributing</a>
</p>

---

## 🧭 What this is

This toolkit gives you everything you need to configure an AI assistant — specifically Claude — into a rigorous, analytical fact-checker and misinformation detector.

It is not a single prompt. It is a **modular system** made of:

- Structured analytical pipelines (simple and full)
- Exhaustive reference documents (cognitive biases, logical fallacies, epistemology, scientific literacy, media literacy)
- A trigger-based skill (`[fc]`) for on-demand fact-checking
- Real worked examples showing the system in action

The goal is **critical thinking at scale** — giving anyone the tools to interrogate claims, expose rhetorical manipulation, and reason from evidence rather than intuition.

---

## 📁 Repo Structure

```
ai-misinformation-toolkit/
│
├── README.md                          ← You are here
├── MANIFESTO.md                       ← Why this project exists
│
└── ai-analytical-verification-setups/
    │
    ├── simple-general-setup.md        ← Setup A: lightweight, general-purpose
    ├── oneshot-prompt.md              ← Single-prompt version (no project required)
    │
    ├── full-setup/
    │   ├── SKILL.md                   ← The [fc] skill definition
    │   ├── instructions.md            ← Full system instructions for Claude
    │   └── description.md            ← Project description for Claude
    │
    ├── documents-for-both-setups/     ← Shared knowledge base
    │   ├── cognitive-biases-list.md
    │   ├── logical-flaws-and-fallacies-sophism.md
    │   ├── epistemology-basics.md
    │   ├── scientific-literacy-guide-misinformation-patterns.md
    │   ├── media-literacy.md
    │   ├── source-evaluation-framework.md
    │   ├── content-to-check.md        ← Sample content for testing
    │   └── skill.md                   ← Operational skill summary (arsenal)
    │
    └── examples/
        ├── content-to-check.md        ← Sample input
        ├── full-check.md              ← Example output: full pipeline
        └── simple-general-check.md   ← Example output: simple pipeline
```

---

## ⚡ Quick Start

You have three options depending on how much setup you want.

### Option 1 — One-shot prompt (zero setup)

Copy the contents of [`oneshot-prompt.md`](https://github.com/infinitimeless/ai-misinformation-toolkit/blob/main/ai-analytical-verification-setups/oneshot-prompt.md) and paste it at the top of any conversation with Claude, followed by the content you want analyzed. No project, no configuration needed.

Best for: occasional use, quick checks, testing the system.

### Option 2 — Simple setup (Claude Project)

1. Create a new Claude Project
2. Paste [`simple-general-setup.md`](https://github.com/infinitimeless/ai-misinformation-toolkit/blob/main/ai-analytical-verification-setups/simple-general-setup.md) as the **Project Instructions**
3. Upload all files from [`documents-for-both-setups/`](https://github.com/infinitimeless/ai-misinformation-toolkit/tree/main/ai-analytical-verification-setups/documents-for-both-setups) as **Project Knowledge**
4. Start chatting — paste any claim, article, post, or argument and ask for analysis

Best for: regular use without the full analytical overhead.

### Option 3 — Full setup (Claude Project + [fc] skill)

1. Create a new Claude Project
2. Paste [`full-setup/instructions.md`](https://github.com/infinitimeless/ai-misinformation-toolkit/blob/main/ai-analytical-verification-setups/full-setup/instructions.md) as the **Project Instructions**
3. Copy [`full-setup/description.md`](https://github.com/infinitimeless/ai-misinformation-toolkit/blob/main/ai-analytical-verification-setups/full-setup/description.md) into the **Project Description**
4. Upload all files from [`documents-for-both-setups/`](https://github.com/infinitimeless/ai-misinformation-toolkit/tree/main/ai-analytical-verification-setups/documents-for-both-setups) as **Project Knowledge**
5. Upload [`full-setup/SKILL.md`](https://github.com/infinitimeless/ai-misinformation-toolkit/blob/main/ai-analytical-verification-setups/full-setup/SKILL.md) as an additional knowledge document
6. Prefix any message with `[fc]` to trigger the full 8-step verification pipeline

Best for: serious analysis, structured outputs, recurring fact-checking workflows.

---

## 🔧 The Two Setups

### Simple General Setup ([`simple-general-setup.md`](https://github.com/infinitimeless/ai-misinformation-toolkit/blob/main/ai-analytical-verification-setups/simple-general-setup.md))

A clean, neutral fact-checking system that adapts its depth to the complexity of the input.

- **Low complexity** (simple factual question) → direct answer with minimal verification note
- **Medium complexity** (a claim, a post) → claim clarification + evidence check + brief reasoning analysis
- **High complexity** (viral, technical, multi-layered) → full analytical pipeline

Output structure is flexible. Sections appear only when they add value. Tone is neutral, precise, structured — academic clarity with journalistic readability.

**What it covers:** claim identification, evidence verification, logical analysis, cognitive bias detection, source evaluation, synthesis, confidence assessment.

---

### Full Setup ([`full-setup/`](https://github.com/infinitimeless/ai-misinformation-toolkit/tree/main/ai-analytical-verification-setups/full-setup))

A more opinionated, rigorous configuration that turns Claude into the **Anti-Fake Demystifier** — a dedicated analytical persona with a strict methodology.

Key differences from the simple setup:

- Outputs always include a dedicated **Author Biases** section, explicitly distinguishing deliberate manipulation from sincere but biased belief
- Uses precise technical terminology for every detected fallacy and bias
- Applies a confidence color system: 🟢 Refuted with certainty / 🟡 Strongly contestable / 🔴 Insufficiently documented
- The `[fc]` prefix triggers an 8-step verification pipeline (see below)
- Tone is more formally academic; phrasing is syntactically controlled

---

## 📚 Reference Documents

All documents live in [`documents-for-both-setups/`](https://github.com/infinitimeless/ai-misinformation-toolkit/tree/main/ai-analytical-verification-setups/documents-for-both-setups) and are used as the knowledge base for both setups. Upload them all to your Claude Project.

| Document | What it covers |
|---|---|
| [`cognitive-biases-list.md`](https://github.com/infinitimeless/ai-misinformation-toolkit/blob/main/ai-analytical-verification-setups/documents-for-both-setups/cognitive-biases-list.md) | 200+ cognitive biases across 22 categories, with definitions and real-world examples. Covers perception, memory, reasoning, social, emotional, decision-making, financial biases and more. |
| [`logical-flaws-and-fallacies-sophism.md`](https://github.com/infinitimeless/ai-misinformation-toolkit/blob/main/ai-analytical-verification-setups/documents-for-both-setups/logical-flaws-and-fallacies-sophism.md) | Complete taxonomy of fallacies: formal, relevance, presumption, insufficient evidence, rhetorical techniques, and interpersonal manipulation. Each entry includes a plain-language description. |
| [`epistemology-basics.md`](https://github.com/infinitimeless/ai-misinformation-toolkit/blob/main/ai-analytical-verification-setups/documents-for-both-setups/epistemology-basics.md) | Foundations of knowledge, levels of evidence, burden of proof, Bayesian thinking, and common epistemic errors. Used to assess the epistemic status of any claim. |
| [`scientific-literacy-guide-misinformation-patterns.md`](https://github.com/infinitimeless/ai-misinformation-toolkit/blob/main/ai-analytical-verification-setups/documents-for-both-setups/scientific-literacy-guide-misinformation-patterns.md) | Correlation vs causation, study types, statistical concepts, and warning signs of scientific misuse. Used for any claim involving data or research. |
| [`media-literacy.md`](https://github.com/infinitimeless/ai-misinformation-toolkit/blob/main/ai-analytical-verification-setups/documents-for-both-setups/media-literacy.md) | Framing, agenda-setting, narrative bias, sensationalism, and the headline/content gap. Used to detect how information is shaped by its presentation. |
| [`source-evaluation-framework.md`](https://github.com/infinitimeless/ai-misinformation-toolkit/blob/main/ai-analytical-verification-setups/documents-for-both-setups/source-evaluation-framework.md) | Structured framework for evaluating source credibility across five criteria: authority, accuracy, transparency, independence, and currency. |

You do not need to read or memorize these. When loaded as Project Knowledge, Claude references them automatically during analysis.

---

## 🧠 The [fc] Skill

The `[fc]` prefix triggers a full 8-step verification pipeline. It is defined in [`full-setup/SKILL.md`](https://github.com/infinitimeless/ai-misinformation-toolkit/blob/main/ai-analytical-verification-setups/full-setup/SKILL.md) and is only active in the full setup.

**How to use it:** Start any message with `[fc]` followed by your content.

```
[fc] "AI will replace 90% of all jobs by 2030" — is this claim supported by evidence?
```

```
[fc] [paste a full article or social media thread here]
```

**The 8-step pipeline:**

| Step | What happens |
|---|---|
| 1. Parse | Domain, claim type, named entities, origin identified |
| 2. Epistemological assessment | Burden of proof, evidence level, decidability, Bayesian prior |
| 3. Claim extraction | Every verifiable sub-claim isolated from rhetoric |
| 4. Source audit & web verification | Each claim checked against primary sources; source credibility evaluated |
| 4b. Scientific/statistical check | If applicable: study type, sample size, correlation vs causation, consensus |
| 5. Logical audit | All six fallacy categories checked against the full taxonomy |
| 6. Cognitive bias scan | Full bias catalog applied; high-frequency disinformation biases prioritized |
| 7. Disinformation & media pattern check | Construction patterns and media manipulation tactics detected |
| 8. Final answer | Corrected, verified response with full summary |

**Output format:**

Every `[fc]` response ends with a structured verification summary using this flag system:

```
✅ Verified       — confirmed claims
⚠️ Unverified     — claims that could not be confirmed
❌ Corrected      — claims that were wrong, now fixed
🔍 Epistemic      — overconfidence, underdetermined claims
⚗️ Logic          — fallacies or manipulation techniques found
🧠 Biases         — cognitive biases detected
🗞️ Disinfo/Media  — disinformation and media manipulation patterns
🔬 Science        — statistical misuse, study type issues
📚 Sources        — flagged or weak sources
```

---

## 📄 Examples

Two complete worked examples are included in [`examples/`](https://github.com/infinitimeless/ai-misinformation-toolkit/tree/main/ai-analytical-verification-setups/examples) using the same input (a 20-tweet thread about agentic AI).

**[`simple-general-check.md`](https://github.com/infinitimeless/ai-misinformation-toolkit/blob/main/ai-analytical-verification-setups/examples/simple-general-check.md)** — Output from the simple setup. Covers claim summary, key facts, analysis, logical issues, cognitive biases, source assessment, and confidence level. Readable and structured without being exhaustive.

**[`full-check.md`](https://github.com/infinitimeless/ai-misinformation-toolkit/blob/main/ai-analytical-verification-setups/examples/full-check.md)** — Output from the full `[fc]` pipeline. Section-by-section breakdown of factual claims, fallacies detected, reader and author biases, source evaluation table, disinformation patterns, and a full verification summary with flags.

Reading both examples side by side is the fastest way to understand the difference between the two setups.

---

## 🤝 Contributing

Contributions are welcome. The most useful areas:

- **[`source-evaluation-framework.md`](https://github.com/infinitimeless/ai-misinformation-toolkit/blob/main/ai-analytical-verification-setups/documents-for-both-setups/source-evaluation-framework.md)** — currently empty; a structured framework here would strengthen both setups significantly
- **[`oneshot-prompt.md`](https://github.com/infinitimeless/ai-misinformation-toolkit/blob/main/ai-analytical-verification-setups/oneshot-prompt.md)** — currently empty; a well-crafted single-prompt version would lower the barrier to entry substantially
- **Additional examples** — more worked examples across different domains (health claims, political statements, scientific papers, product marketing) would make the repo far more practical
- **Translations** — the reference documents are in English; French versions or other languages would extend reach
- **Prompt improvements** — if you find edge cases where the system fails or produces weak output, open an issue with the input and the actual vs. expected output

To contribute, fork the repo, make your changes, and open a pull request with a clear description of what you changed and why.

---

## 📜 License

This project is open-source. See `LICENSE` for details.

---

## 🙏 Acknowledgments

Built on the existing body of work in epistemology, cognitive psychology, rhetoric, and media studies. This toolkit assembles and operationalizes that knowledge for practical use with AI assistants. No original research claimed — only applied synthesis.
A reproducible, open-source toolkit for building and configuring text‑generative AI assistants and "GPT"-style projects focused on detecting, explaining, and preventing misinformation through bias analysis, source evaluation, and structured reasoning.
