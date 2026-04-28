# mph-ai-toolkit
### How I use AI across my MPH research workflow — from systematic review to data analysis to product thinking

> **Lin Fang Yu** | MPH Candidate, NUS Saw Swee Hock School of Public Health | Graduating July 2026  
> Former surgical nurse → public health researcher → health tech analyst

---

## Why this repo exists

Most AI showcases focus on building models. This one focuses on something different: **how a public health researcher uses AI as a thinking partner** across the full research workflow — from designing a systematic review, to cleaning clinical data, to translating findings into product implications.

My background sits at the intersection of clinical practice, population health, and digital health technology. That position gives me a specific lens: I use AI not just to write code faster, but to bridge the gap between complex health data and the humans who need to act on it. That gap — between what health technology can do and what real users actually experience — is what this repo is about.

---

## My MPH Research Context

This repo documents AI use across my current MPH research at NUS, which covers three interconnected projects:

| Project | Topic | AI Role |
|---------|-------|---------|
| **Systematic Review** | Behavioural theory-driven digital mental health interventions for Asian adolescents | Literature synthesis, framework extraction, quality assessment |
| **GUARDIAN** | Multimodal ML system for adolescent suicide/self-harm risk prediction | System design, database architecture, prompt-assisted SQL |
| **MIMIC Causal Inference** *(separate topic)* | Causal inference on 94,458 ICU stays — palliative care in cancer patients | Query writing, analysis pipeline, data narrative |

---

## Section 1 — AI-Assisted Systematic Review
### *Research thinking: using AI to synthesise 15 studies across 10 Asian countries*

**What I did:**  
Conducted a PRISMA 2020-compliant systematic review titled:  
*"A Systematic Review of Behavioural Theory-Driven Digital Mental Health Promotion Interventions for Adolescents in Asia"*

- Screened studies across PubMed, Scopus, PsycINFO, Web of Science, and Embase (2015–2025)
- Applied a two-tier theoretical framework classification system (Tier 1: explicitly theory-based; Tier 2: implicitly theory-informed using BCTTv1)
- Extracted data from 15 included studies across 10 Asian countries (China, Japan, South Korea, Singapore, Malaysia, Thailand, Indonesia, India, Hong Kong, Iran)
- Assessed risk of bias using Cochrane RoB 2 (RCTs) and ROBINS-I (quasi-experimental studies)

**How I used AI:**

1. **Literature triage** — Used AI to help identify keyword clusters and refine Boolean search strings across five databases. Example prompt:
   > *"I'm searching for digital mental health promotion interventions for adolescents in Asia. My key concepts are: digital delivery, adolescents aged 10–24, Asian countries, and behavioural theory. Help me build a PubMed search string that captures implicit theory use (behaviour change techniques) as well as explicit theory naming."*

2. **BCT coding assistance** — Used AI to cross-check my Behaviour Change Technique Taxonomy v1 (BCTTv1) coding decisions. I coded independently first, then used AI to identify any BCTs I may have missed in intervention descriptions. Final decisions were always my own.

3. **Risk of Bias reasoning** — After independently assessing each domain using RoB 2, I used AI as a sounding board to articulate my rationale clearly. For example:
   > *"Moeini et al. 2019 reported a significant ITT result at 12 weeks (p=0.031) but a non-significant result at 24 weeks (p=0.062). The 24-week endpoint was the stated study duration. Help me articulate why this warrants a High Risk rating in D5 (Selection of Reported Result)."*

4. **Data extraction table drafting** — Used AI to help structure consistent language across 15 study summaries, ensuring parallel framing of theoretical constructs, mechanisms of change, and alignment ratings.

**What AI could NOT do:**  
AI could not make methodological judgement calls. Deciding whether allocation concealment was adequately described, or whether a non-significant 24-week result being downplayed warranted a High Risk RoB rating — these required reading the full paper, clinical reasoning, and domain expertise. AI helped me articulate my reasoning; it did not replace it.

**Key finding:**  
CBT was the dominant framework (9/15 studies). Despite high theoretical diversity, only 3/15 studies demonstrated strong theory-to-intervention alignment with adequate cultural adaptation for Asian adolescent contexts. Chatbot and app-based delivery showed the highest scalability potential but also the weakest theory fidelity.

---

## Section 2 — AI + Google BigQuery Workflow
### *Coding skills: using AI as a SQL collaborator on real-world clinical data*

> **Note on project separation:** This section covers my MIMIC-IV causal inference project — a **completely separate project** from the systematic review in Section 1. The MIMIC project analyses ICU clinical data; the systematic review synthesises digital mental health intervention literature. They share no data source. Together they demonstrate range: evidence synthesis on one end, large-scale quantitative clinical data analysis on the other.

**What I did:**  
Analysed the MIMIC-IV clinical database to examine the effect of palliative care consultation on outcomes in cancer ICU patients, using propensity score matching (PSM) and inverse probability of treatment weighting (IPTW).

- Queried 94,458 ICU stays → filtered to 4,703 eligible cases → matched to 303 pairs
- Built a 7-step SQL pipeline in Google BigQuery
- Ran causal inference analysis in Python (scikit-learn, pandas)

**How I used AI:**

1. **Query debugging** — When my cohort flowchart numbers weren't matching, I used AI to help trace the logic:
   > *"My query returns 5,793 patients after filtering for first ICU stay and age ≥18, but I expect closer to 6,000. Here's my SQL. Can you identify where I might be double-counting or missing a join condition?"*
   AI identified a missing `DISTINCT` clause on the `hadm_id` join — something I would have caught eventually but that AI found in seconds.

2. **Overlap trimming logic** — Used AI to explain the statistical rationale for IPTW overlap trimming before I implemented it:
   > *"Explain why trimming propensity scores outside the 0.1–0.9 range improves the validity of IPTW estimates in a small dataset."*

3. **Writing the analysis narrative** — After analysis, used AI to help translate statistical outputs into plain-English findings for a non-statistician audience. I then edited heavily for accuracy and clinical nuance.

**What AI could NOT do:**  
AI did not design the causal inference strategy, select appropriate confounders, or interpret the clinical meaning of the results. Domain knowledge about ICU care, oncology, and palliative medicine was essential and irreplaceable.

📁 **Repo:** [MIMIC-Causal-Inference](https://github.com/lfangyu443-ui/MIMIC-Causal-Inference)

---

## Section 3 — AI-Assisted Qualitative Analysis
### *Research thinking: thematic analysis of wearable device adoption*

**What I did:**  
Conducted in-depth user interviews and thematic analysis on digital health wearable device adoption and retention barriers among users in Asia (NUS SPH5409).

**How I used AI:**

1. **Codebook development** — After initial open coding, I used AI to help identify thematic patterns across my codes:
   > *"Here are 40 codes from my wearable adoption interviews. Can you help me identify potential higher-order themes? I'll compare your groupings against my own and document where we agree and diverge."*

2. **Negative case analysis** — Used AI to help identify participant responses that challenged my emerging themes:
   > *"My emerging theme is 'trust in data accuracy drives sustained use.' Here are 5 quotes. Are there any that could be interpreted as contradicting this theme?"*

3. **Reflexivity** — Used AI to help articulate researcher positionality statements clearly.

**Key insight for product marketing:**  
The most common adoption barrier was not usability — it was **trust in the data narrative**. Users abandoned wearables not because the app was hard to use, but because they did not understand what the numbers meant for their lives. This is a product marketing problem: the gap between what the device measures and what the user values was never bridged. This insight directly informs how I think about marketing health AI tools like Google Fit or Fitbit in Asian markets.

---

## Section 4 — AI for Data Storytelling
### *Product strategy thinking: translating health data into narratives that move people*

**The translation problem in health tech:**  
Health data is almost always more complex than users want it to be. A wearable generates continuous physiological streams. A systematic review produces a 15-study evidence matrix. A causal inference model outputs adjusted odds ratios with confidence intervals. None of these are inherently meaningful to the person who needs to make a decision.

**How I use AI for storytelling:**

The workflow I've developed:
1. **Produce the finding** — analysis done by me, using domain expertise
2. **Draft the narrative** — use AI to write a first version in plain language
3. **Stress-test the narrative** — ask AI: *"What would a sceptical clinician / parent / policy-maker push back on here?"*
4. **Revise for accuracy** — rewrite in my own words, correcting any oversimplification
5. **Test the headline** — ask AI: *"If this finding were a product feature, what problem does it solve for the user?"*

**Example — from my systematic review:**

Raw finding:
> *"9/15 studies used CBT. 3/15 demonstrated strong theory-to-intervention alignment. Cultural adaptation was absent or partial in 10/15 studies."*

AI-drafted narrative (first pass):
> *"Most digital mental health apps for Asian teens are built on Western therapy frameworks without meaningful cultural adaptation — and it shows in the outcomes."*

My revised version:
> *"The evidence base for digital mental health in Asia is growing, but a consistent gap remains: most interventions import CBT frameworks developed in Western clinical contexts without adequately adapting them for the social and cultural dynamics of Asian adolescent life — including family-centred identity, academic pressure, and stigma around help-seeking. Closing this gap is not just a research challenge; it is a product design and marketing challenge."*

The AI draft was usable but flattened nuance. My revision restored clinical accuracy while keeping the narrative accessible.

---

## Section 5 — Reflections: AI Limitations in Health Research
### *And what that means for building health AI products*

After using AI across all four stages above, here is what I have learned:

**Where AI genuinely helped:**
- Speed of first drafts (literature, code, narrative)
- Identifying inconsistencies in logic or data I had been too close to see
- Articulating reasoning I understood intuitively but had not yet written clearly
- Generating alternative framings of findings for different audiences

**Where AI consistently fell short:**
- **Clinical judgement** — AI does not know what a post-surgical patient or an ICU patient's trajectory actually looks like. I do, from three years at the bedside.
- **Cultural context** — AI tends to flatten Asian cultural diversity into generic "Asian context" statements. The difference between how adolescent mental health is perceived in South Korea vs Indonesia vs India requires lived and studied knowledge.
- **Methodological integrity** — AI will suggest a more elegant statistical approach without flagging whether it is appropriate for your sample size, data distribution, or research question. You have to know enough to push back.
- **Ethical dimensions** — AI did not spontaneously flag the PDPA consent implications of my GUARDIAN design, or the equity implications of requiring smartphone ownership for a digital mental health intervention. I had to bring those questions.

**The product implication:**  
If these are the limitations of AI *when used by a researcher with domain expertise*, they are even more significant when AI health tools are deployed directly to end users — adolescents, parents, or clinicians — without that expertise buffer. The companies building health AI products need people who understand both the technology and the clinical and cultural context. That is the gap I am positioned to bridge.

---

## Tools Used

![Google BigQuery](https://img.shields.io/badge/BigQuery-4285F4?style=flat&logo=google-cloud&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![R](https://img.shields.io/badge/R-276DC3?style=flat&logo=r&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat&logo=mysql&logoColor=white)
![Power BI](https://img.shields.io/badge/Power_BI-F2C811?style=flat&logo=powerbi&logoColor=black)
![Stata](https://img.shields.io/badge/Stata-1A5276?style=flat)

**AI tools used in research workflow:**
- Large language models (for drafting, debugging, reasoning articulation)
- Systematic review tools (Covidence, Zotero)
- BCTTv1 coding framework

---

## Related Repositories

| Repo | Description |
|------|-------------|
| [guardian-db](https://github.com/lfangyu443-ui/guardian-db) | MySQL database for GUARDIAN — multimodal adolescent mental health risk prediction |
| [MIMIC-Causal-Inference](https://github.com/lfangyu443-ui/MIMIC-Causal-Inference) | Causal inference on 94K+ ICU stays using Google BigQuery and PSM |
| [Power-BI-data-visualization](https://github.com/lfangyu443-ui/Power-BI-data-visualization) | Interactive health data dashboards |
| [Stata-data-analysis](https://github.com/lfangyu443-ui/Stata-data-analysis) | Epidemiological analysis scripts |

---

## About Me

I am a nurse-turned-public-health-researcher interested in the space where clinical evidence, digital technology, and human behaviour intersect. My research focuses on how AI and digital tools can be designed and marketed to actually reach and help the Asian adolescents who need them — not just the ones who fit the assumptions of Western product design.

📍 Taipei, Taiwan | 🎓 NUS MPH, graduating July 2026  
📧 el649078@u.nus.edu
