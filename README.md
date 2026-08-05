# JSON Persona Tool

A lightweight, browser-based tool for building and editing UX personas through a guided, multi-step form — no install, no backend, no account. Fill it out, download a clean JSON file, and use it anywhere: paste it into an LLM for a heuristic review, hand it to a design team, or version it alongside your research docs.

**Try it live →[Persona Creator](https://pjordan-bch.github.io/persona_creator/)** *(add your GitHub Pages URL here once deployed)*

## Why this exists

Personas are useful right up until they're a stale slide buried in a deck. This tool keeps them as structured, editable data instead — easy to update as research evolves, easy to diff over time, and easy to feed into other tools (prompts, dashboards, design systems) without re-typing anything.

## Features

- **Guided multi-step form** — Basics, Goals & Motivations, Identity Snapshot, Access/Literacy/Complexity Profile, Barriers & Constraints, and a final Review step before download
- **Sensible input types** — sliders for age ranges (with an N/A option where age isn't applicable), tap-to-select buttons for categorical fields, add/remove lists for goals
- **Edit existing personas** — upload a previously exported JSON file to load it back into the form and continue editing
- **Nothing leaves your browser** — all parsing, editing, and file generation happens client-side; there's no server, no analytics, and no data storage
- **One file, zero dependencies** — a single `index.html` with no build step, no npm install, no external services

## Using it

1. Open the tool (locally or via the hosted link)
2. Choose **Create New Persona** or **Upload Existing Persona (JSON)** to edit one you already have
3. Step through the form — most fields are optional; only a persona name is required
4. Review your entries on the final step
5. Click **Download Persona JSON**

## Running it locally

No build step required:

```bash
git clone <this-repo-url>
cd <repo-folder>
open index.html   # or just double-click the file
```

## Output format

Downloads are plain JSON in a consistent, flat-ish schema:

```json
{
  "persona_name": "",
  "descriptor": "",
  "representative_quote": "",
  "goals_and_motivations": [],
  "identity_snapshot": {
    "age_of_patient": "",
    "age_of_caregiver": "",
    "relationship_to_patient": "",
    "geographic_scope": "",
    "patient_tenure": "",
    "life_stage": "",
    "family_context": "",
    "primary_language": "",
    "specialties_visited": "",
    "average_visits_per_month": ""
  },
  "access_literacy_complexity_profile": {
    "level_of_digital_engagement": "",
    "care_complexity": "",
    "literacy_profile": {
      "health_literacy": "",
      "digital_literacy": "",
      "reading_literacy": ""
    },
    "access_barriers": {
      "physical": "",
      "non_physical": ""
    },
    "resource_constraints": "",
    "goals_related_to_access_and_complexity": []
  }
}
```

Because the export is plain, predictable JSON, it's easy to script against, template into other documents, or paste directly into an LLM conversation for context.

## A note on the data

This tool is meant for **sample/composite personas** built from research and synthesized patterns — not real individuals' personal or health information. Nothing is transmitted anywhere by the tool itself, but it's still good practice to keep any identifying details out of what you type in.
