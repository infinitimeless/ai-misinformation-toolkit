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
  <a href="#-reference-documents">Reference Documents</a> ·
  <a href="#-the-fc-skill">The [fc] Skill</a> ·
  <a href="#-examples">Examples</a> ·
  <a href="#-contributing">Contributing</a>
</p>

---

## 🧭 What this is

This toolkit gives you everything you need to configure an AI assistant into a rigorous, analytical fact-checker and misinformation detector.

It is not a single prompt. It is a **modular system** made of:

* Structured analytical pipelines (simple and full)
* Exhaustive reference documents (cognitive biases, logical fallacies, epistemology, scientific literacy, media literacy)
* A trigger-based skill (`[fc]`) for on-demand fact-checking
* Real worked examples showing the system in action

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
    ├── oneshot-prompt.md              ← Single-prompt version (no Project required)
    │
    ├── full-setup/                    ← Setup B: full pipeline with [fc] skill
    │   ├── SKILL.md                   ← The [fc] skill definition
    │   ├── instructions.md            ← Full system instructions
    │   ├── description.md             ← Project description
    │   └── references-for-SKILL/      ← Reference files for the skill
    │       └── references.md
    │
    ├── project-knowledge-base/        ← Shared knowledge base (upload to all setups)
    │   ├── cognitive-biases-list.md
    │   ├── logical-flaws-and-fallacies-sophism.md
    │   ├── epistemology-basics.md
    │   ├── scientific-literacy-guide-misinformation-patterns.md
    │   ├── media-literacy.md
    │   ├── source-evaluation-framework.md
    │   └── content-to-check.md        ← Sample content for testing
    │   
    │
    └── examples/
        ├── content-to-check.md        ← Sample input
        ├── oneshot-check.md           ← Example output: one-shot prompt
        ├── simple-general-check.md    ← Example output: simple pipeline
        └── full-check.md              ← Example output: full pipeline
```

---

## ⚡ Quick Start

You have three options depending on how much setup you want.

### Option 1 — One-shot prompt (zero setup)

For AI providers with no **Project** feature and no knowledge base upload.

1. Copy the contents of [`oneshot-prompt.md`](https://github.com/infinitimeless/ai-misinformation-toolkit/blob/main/ai-analytical-verification-setups/oneshot-prompt.md) and paste it at the top of any conversation.
2. Replace the `{CONTENT_TO_CHECK}` placeholder with the content you want analyzed. No **Project**, no documents to upload, no configuration needed.

---

### Option 2 — Simple setup (GPT, Lumo, Mistral, LMStudio…)

For AI providers that offer a single **Project** setup field and allow document uploads.

1. Create a new **Project**.
2. Paste [`simple-general-setup.md`](https://github.com/infinitimeless/ai-misinformation-toolkit/blob/main/ai-analytical-verification-setups/simple-general-setup.md) into the dedicated **Project** field.
3. Upload all files from [`project-knowledge-base/`](https://github.com/infinitimeless/ai-misinformation-toolkit/tree/main/ai-analytical-verification-setups/project-knowledge-base) as **Project Knowledge**.
4. Start chatting — paste any claim, article, post, or argument and ask for analysis.

> [`oneshot-prompt.md`](https://github.com/infinitimeless/ai-misinformation-toolkit/blob/main/ai-analytical-verification-setups/oneshot-prompt.md) and [`simple-general-setup.md`](https://github.com/infinitimeless/ai-misinformation-toolkit/blob/main/ai-analytical-verification-setups/simple-general-setup.md) are essentially the same prompt. The difference: `simple-general-setup.md` omits the `{CONTENT_TO_CHECK}` placeholder since you provide input directly in the chat. It will be loaded as the first instruction each time you open a new chat from the **Project**. The [`simple-general-setup.md`](https://github.com/infinitimeless/ai-misinformation-toolkit/blob/main/ai-analytical-verification-setups/simple-general-setup.md) also mention the documents uploaded in the **Project Knowledge** (you can find those documents in [`project-knowledge-base/`](https://github.com/infinitimeless/ai-misinformation-toolkit/tree/main/ai-analytical-verification-setups/project-knowledge-base))

> **LM Studio:** Upload [`project-knowledge-base/`](https://github.com/infinitimeless/ai-misinformation-toolkit/tree/main/ai-analytical-verification-setups/project-knowledge-base) in the "Folders" panel and paste [`simple-general-setup.md`](https://github.com/infinitimeless/ai-misinformation-toolkit/blob/main/ai-analytical-verification-setups/simple-general-setup.md) into the **System Prompt** field in the right **Configuration** panel.

---

### Option 3 — Full setup (Claude Project + \[fc\] skill)

For AI providers that offer both a **Project** description/instructions field and a **Project Knowledge** base — and that support a **Skill** feature. This is the recommended setup for Claude.

1. Create a new **Project**.
2. Copy [`full-setup/description.md`](https://github.com/infinitimeless/ai-misinformation-toolkit/blob/main/ai-analytical-verification-setups/full-setup/description.md) into the **Project Description** field.
3. Paste [`full-setup/instructions.md`](https://github.com/infinitimeless/ai-misinformation-toolkit/blob/main/ai-analytical-verification-setups/full-setup/instructions.md) into the **Project Instructions** field.
4. Create a **Skill** using [`full-setup/SKILL.md`](https://github.com/infinitimeless/ai-misinformation-toolkit/blob/main/ai-analytical-verification-setups/full-setup/SKILL.md).
5. Upload the files listed in [`references-for-SKILL/references.md`](https://github.com/infinitimeless/ai-misinformation-toolkit/blob/main/ai-analytical-verification-setups/full-setup/references-for-SKILL/references.md) into the skill's references folder.
6. Upload all files from [`project-knowledge-base/`](https://github.com/infinitimeless/ai-misinformation-toolkit/tree/main/ai-analytical-verification-setups/project-knowledge-base) as **Project Knowledge**.

> Once the skill is configured, prefixing any message with `[fc]` — even in chats outside your dedicated **Project** — will trigger the full 8-step verification pipeline defined in the [`full-setup/SKILL.md`](https://github.com/infinitimeless/ai-misinformation-toolkit/blob/main/ai-analytical-verification-setups/full-setup/SKILL.md)

---

## 📚 Reference Documents

All documents live in [`project-knowledge-base/`](https://github.com/infinitimeless/ai-misinformation-toolkit/tree/main/ai-analytical-verification-setups/project-knowledge-base) and serve as the knowledge base for all three setups.

| Document | What it covers |
| --- | --- |
| [`cognitive-biases-list.md`](https://github.com/infinitimeless/ai-misinformation-toolkit/blob/main/ai-analytical-verification-setups/project-knowledge-base/cognitive-biases-list.md) | 200+ cognitive biases across 22 categories, with definitions and real-world examples. Covers perception, memory, reasoning, social, emotional, decision-making, and financial biases. |
| [`logical-flaws-and-fallacies-sophism.md`](https://github.com/infinitimeless/ai-misinformation-toolkit/blob/main/ai-analytical-verification-setups/project-knowledge-base/logical-flaws-and-fallacies-sophism.md) | Complete taxonomy of fallacies: formal, relevance, presumption, insufficient evidence, rhetorical techniques, and interpersonal manipulation. Each entry includes a plain-language description. |
| [`epistemology-basics.md`](https://github.com/infinitimeless/ai-misinformation-toolkit/blob/main/ai-analytical-verification-setups/project-knowledge-base/epistemology-basics.md) | Foundations of knowledge, levels of evidence, burden of proof, Bayesian thinking, and common epistemic errors. Used to assess the epistemic status of any claim. |
| [`scientific-literacy-guide-misinformation-patterns.md`](https://github.com/infinitimeless/ai-misinformation-toolkit/blob/main/ai-analytical-verification-setups/project-knowledge-base/scientific-literacy-guide-misinformation-patterns.md) | Correlation vs causation, study types, statistical concepts, and warning signs of scientific misuse. Used for any claim involving data or research. |
| [`media-literacy.md`](https://github.com/infinitimeless/ai-misinformation-toolkit/blob/main/ai-analytical-verification-setups/project-knowledge-base/media-literacy.md) | Framing, agenda-setting, narrative bias, sensationalism, and the headline/content gap. Used to detect how information is shaped by its presentation. |
| [`source-evaluation-framework.md`](https://github.com/infinitimeless/ai-misinformation-toolkit/blob/main/ai-analytical-verification-setups/project-knowledge-base/source-evaluation-framework.md) | Structured framework for evaluating source credibility across five criteria: authority, accuracy, transparency, independence, and currency. |

You do not need to read or memorize these. When loaded as **Project Knowledge**, the AI references them automatically during analysis.

---

## 🧠 The \[fc\] Skill

The `[fc]` prefix triggers a full 8-step verification pipeline. It is defined in [`full-setup/SKILL.md`](https://github.com/infinitimeless/ai-misinformation-toolkit/blob/main/ai-analytical-verification-setups/full-setup/SKILL.md) and is only active in the full setup (Option 3).

**How to use it:** Start any message with `[fc]` followed by your content.

```
[fc] "AI will replace 90% of all jobs by 2030" — is this claim supported by evidence?
```

```
[fc] [paste a full article or social media thread here]
```

**The 8-step pipeline:**

| Step | What happens |
| --- | --- |
| 1. Parse | Domain, claim type, named entities, and origin identified |
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

Three complete worked examples are included in [`examples/`](https://github.com/infinitimeless/ai-misinformation-toolkit/tree/main/ai-analytical-verification-setups/examples), all using the same input — a 20-tweet thread about agentic AI — so you can directly compare the three setup outputs side by side.

**[`oneshot-check.md`](https://github.com/infinitimeless/ai-misinformation-toolkit/blob/main/ai-analytical-verification-setups/examples/oneshot-check.md)** — Output from the one-shot prompt. Shows what you get from a single pasted prompt with no **Project** configuration.

**[`simple-general-check.md`](https://github.com/infinitimeless/ai-misinformation-toolkit/blob/main/ai-analytical-verification-setups/examples/simple-general-check.md)** — Output from the simple setup. Covers claim summary, key facts, analysis, logical issues, cognitive biases, source assessment, and confidence level. Readable and structured without being exhaustive.

**[`full-check.md`](https://github.com/infinitimeless/ai-misinformation-toolkit/blob/main/ai-analytical-verification-setups/examples/full-check.md)** — Output from the full `[fc]` pipeline. Section-by-section breakdown of factual claims, fallacies detected, reader and author biases, source evaluation table, disinformation patterns, and a complete verification summary with flags.

Reading all three side by side is the fastest way to understand the difference between the setups.

---

## 🤝 Contributing

Contributions are welcome. The most useful areas:

* **[`source-evaluation-framework.md`](https://github.com/infinitimeless/ai-misinformation-toolkit/blob/main/ai-analytical-verification-setups/project-knowledge-base/source-evaluation-framework.md)** — could be expanded with more concrete real-world examples and scoring rubrics to strengthen all three setups
* **[`oneshot-prompt.md`](https://github.com/infinitimeless/ai-misinformation-toolkit/blob/main/ai-analytical-verification-setups/oneshot-prompt.md)** — improvements and refinements to the single-prompt version are welcome; edge cases and failure modes especially
* **Additional examples** — more worked examples across different domains (health claims, political statements, scientific papers, product marketing) would make the repo far more practical
* **Translations** — the reference documents are in English; French versions or other languages would extend reach
* **Prompt improvements** — if you find edge cases where the system fails or produces weak output, open an issue with the input and the actual vs. expected output

To contribute, fork the repo, make your changes, and open a pull request with a clear description of what you changed and why.

---

## 📜 License

MIT License — Copyright (c) 2026 infinitimeless

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

---

## 🙏 Acknowledgments

Built on the existing body of work in epistemology, cognitive psychology, rhetoric, and media studies. This toolkit assembles and operationalizes that knowledge for practical use with AI assistants. No original research claimed — only applied synthesis.
