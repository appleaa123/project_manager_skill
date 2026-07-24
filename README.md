# Project Manager Framework (PM-OS)

An AI skill that equips the model to act as a project manager — either as a hands-on task
manager (WBS, timelines, scope, risk) or as a PM executive advisor (trade-off analysis, framework
selection, governance).

## When it triggers

Mentions of "project manager," "PM mode," "manage this project," "PM advice," "act as PM," or
requests for help with project planning, scope, schedule, risk, or execution.

## How it works

On activation, the skill follows a 4-step protocol (see `SKILL.md` §2):

1. **Intake & Mode Selection** — clarify methodology (Traditional/Agile/Hybrid) and role
   (hands-on manager vs. advisor).
2. **Project Landscape Diagnosis** — classify the project on the Goal Clarity × Solution Clarity
   matrix.
3. **Framework Execution** — run the matching lifecycle (Predictive phase-gates or Agile/Hybrid
   iteration cycles).
4. **Active Monitoring & Creep Defense** — watch for scope, feature, hope, and effort creep.

`SKILL.md` also defines five core mental models (Scope Triangle, Chef vs. Cook, Dual-Aspect Risk,
Co-Manager Leadership, EVM), a communication style, and decision heuristics.

## Layout

```
project-manager-skill/
├── SKILL.md                # Operating protocol, mental models, heuristics (always loaded on trigger)
└── references/              # Full-depth source material, loaded on demand — see SKILL.md §9
    ├── Project_Landscape.md
    ├── Scope_Triangle_and_Risk_Management.md
    ├── Project_Risk_Management.md
    ├── Process_Group_Integration.md
    ├── Project_Management_Knowledge.md
    ├── PMLC_Models_and_Risk_Integration.md
    └── Project_Maturity_and_Performance.md
```

The content is synthesized from PMI/PMBOK (Process Groups, Knowledge Areas, risk strategies) and
Robert Wysocki's *Effective Project Management* (Scope Triangle, Project Landscape quadrants,
Scope Bank).

## Evaluating changes

Test cases and grading live under `project-manager-skill-workspace/` (sibling to this directory),
following the skill-creator eval workflow: run the skill against realistic PM prompts, compare
against a baseline, grade objective assertions, and review qualitatively in the eval viewer.
