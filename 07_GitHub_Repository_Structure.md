# GenAI Mentorship Program Pack
### Applied GenAI Projects — Final Year Engineering Students
**Mentor:** James Gnanasekaran · HCLTech
**Program Duration:** 8 Weeks
**Weekly Call:** Every Sunday, 10:00 AM IST, 45 minutes via Microsoft Teams

---


# Document : GitHub Repository Structure Guide

## Repository Naming Conventions

Use lowercase, hyphen-separated names that describe the project clearly.

| Project | Repository Name |
|---------|----------------|
| Contract Deviation Detection | `contract-deviation-detection` |
| Home Insurance Claims Processing | `home-insurance-claims-ai` |

If you are creating branches or sub-repositories for experiments, use:
- `contract-deviation-detection-experiments` for a separate experiment sandbox

Avoid names like `project1`, `aiproject`, `finalproject`, or anything that requires context to understand.

---

## Branch Strategy for Beginners

Keep it simple. Do not introduce complex branching strategies that slow you down.

**Recommended: Two-branch model**

| Branch | Purpose |
|--------|---------|
| `main` | Stable, working code only. Push here when something is working. |
| `dev` | Active development. Push here frequently. |

Rules:
- Never push broken code to `main`
- Commit to `dev` at least twice per week
- Merge `dev` into `main` at the end of each week if the code is in a working state
- Write a brief merge message explaining what changed

**Optional:** If two team members are working on different features simultaneously, create short-lived feature branches:
- `dev-prompt-iteration`
- `dev-output-schema`
Merge these back into `dev` when complete.

---

## Pull Request Expectations

For a small student team, formal pull requests between team members are optional but encouraged as a learning practice. The minimum expectation is:

- Do not merge into `main` without at least one teammate reviewing the code
- When merging to `main`, write a PR description that explains what was added and why
- Use PR comments to note known issues or things to improve later

---

## Recommended Folder Structure

```
project-repo/
│
├── README.md                    ← Project overview and setup instructions
├── .gitignore                   ← Exclude .env files, __pycache__, etc.
├── requirements.txt             ← Python dependencies
│
├── notebooks/                   ← Jupyter notebooks for experiments
│   ├── 01_first_prototype.ipynb
│   ├── 02_output_structure.ipynb
│   └── 03_edge_cases.ipynb
│
├── src/                         ← Clean, reusable source code
│   ├── main.py                  ← Entry point
│   ├── contract_loader.py       ← Input handling
│   ├── deviation_detector.py    ← Core logic
│   └── output_formatter.py     ← Output structuring
│
├── prompts/                     ← All prompts, versioned
│   ├── system_prompt_v1.txt
│   ├── system_prompt_v2.txt
│   └── comparison_prompt_v3.txt
│
├── data/                        ← Sample inputs (no real PII or real client data)
│   ├── sample_standard_contract.txt
│   ├── sample_received_contract.txt
│   └── sample_claim_01.json
│
├── tests/                       ← Test cases and results
│   ├── test_cases.md            ← Inputs and expected outputs
│   └── test_results.md         ← Actual outputs from system
│
├── docs/                        ← Architecture and design documents
│   ├── architecture_diagram.png
│   ├── architecture_notes.md
│   └── prompt_engineering_log.md
│
└── outputs/                     ← Sample outputs (committed for review)
    ├── output_scenario_01.json
    ├── output_scenario_02.json
    └── output_scenario_03.json
```

---

## How to Document Prompts

The `prompts/` folder is important. Do not just save the final prompt — save every significant version with a brief note.

**Naming convention:** `[purpose]_v[number].txt`

**At the top of each prompt file, add a comment block:**
```
# Prompt: System prompt for clause-level deviation detection
# Version: 3
# Date: [date]
# Change from previous version: Added instruction to output JSON only; removed verbose explanation request
# Result: Output is now consistently structured but sometimes misses cross-reference clauses
```

The `docs/prompt_engineering_log.md` file should summarise all iterations in a table:

| Version | Date | Key Change | Result | Notes |
|---------|------|------------|--------|-------|
| v1 | Week 2 | Initial draft | Too verbose, no structure | |
| v2 | Week 3 | Added JSON output instruction | Better structure, misses some clauses | |
| v3 | Week 4 | Added section-by-section instruction | Most accurate so far | Long contracts still problematic |

---

## General GitHub Hygiene

- Never commit API keys, passwords, or environment variables. Use a `.env` file and add it to `.gitignore`.
- Commit messages should describe what changed, not what you did: "Add JSON output schema to deviation detector" not "updated file"
- Push to GitHub at least twice per week, even if the code is in progress
- Add your name and date to any significant notebook or script at the top as a comment

---

