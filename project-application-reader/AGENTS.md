# XX Project Guidance

## Project focus

This workspace supports the EU project XX. Keep responses focused on the Norwegian Meteorological Institute's contribution (Met.no / Met), not on the consortium as a whole. Do not attribute a task or deliverable to Met unless the available project material supports that attribution.

The application document, `XX.pdf`, describes the full consortium and is lengthy. Read it only when the user asks or when the task cannot be answered without it; if needed, inspect only relevant sections.

The main purpose of this workspace is to read and organize project information. Respond in text by default. Create or modify code, figures, or other artifacts when requested or when they are necessary to complete the task.

## Working in the workspace

- Start with the files and context relevant to the current request. Explore further only as needed; do not routinely scan every file, read the full application, activate an environment, or run tests for document-only tasks.
- Follow applicable instructions in nearby files. For Python-specific work, use [PYTHON_DEVELOPMENT.md](PYTHON_DEVELOPMENT.md) as guidance, applying only the parts relevant to the task and existing project setup.
- If requirements or source material are ambiguous, identify the uncertainty and ask rather than inventing project facts.
- Keep changes scoped to the request and preserve existing user changes. Git and version control are managed by the user; do not make Git changes unless asked.
- Do not add dependencies, install tools, or change environments without a clear need. Ask before adding an external package or installing software.
- Protect confidential information. Do not store raw prompts or personal, confidential, or sensitive source data in any project file (README, documentation, `AGENTS.md`, logs, notes); redact or minimally summarize it, and never write credentials, passwords, or secrets. Redact sensitive values from diagnostic output.
- If something looks like a leaked secret or a security risk, tell the user immediately. Do not create code that is malicious or vulnerable; code must be safe to run and do what it advertises.
- Keep project `.md` files accurate: update them when a substantive change makes them inaccurate, and after a large task check all relevant `.md` files and create missing ones if needed. Create discussion or reasoning notes only for decisions or insights that are useful to retain, not for every interaction.

## Session continuity

- At the start of a session, read the most recent entries of `DISCUSSIONS_LOG.md` (if it exists) and any notes files it points to, so earlier work can be continued without the user repeating context. Do not read the whole project.
- Keep a `DISCUSSIONS_LOG.md` log of the discussions with the user, one entry per interaction. Keep each entry short: the goal is a scannable record, not a full transcript, and it must not bloat or it will fill the context. Use this minimal format:
  ```
  ## YYYY-MM-DD — <one-line topic>
  **Prompt:** <one or two sentence summary of what the user asked>
  **Actions:** <bullet list of what was done>
  **Outcome:** <one sentence on result or decision reached>
  ```
- Keep entries free of raw confidential content. Record durable insights that do not fit elsewhere in `THOUGHTS.md`.

## Extracting and condensing project information

- Every extracted or condensed statement from `XX.pdf` or another source must cite its source location, including the page number (and section or table/figure label) where possible.
- If the page cannot be determined, say so explicitly rather than omitting it or guessing.
- Distinguish what the source states from inference, and mark whether Met's involvement is stated or unclear.
- Store condensed results in a notes file (for example `MET_CONTRIBUTION.md`) that keeps these citations, and record which sections have been processed in `DISCUSSIONS_LOG.md` so later sessions do not redo them.

## Reasoning and collaboration

- The user is typically a PhD-level expert on the topic: discuss, brainstorm, and raise hard questions rather than guessing.
- After reaching an answer or solution, consider alternatives and the opposite. Does it still make sense? Suggest other viewpoints or solutions to the user where useful.
- If you see a better method, algorithm, data structure, or something more worth testing, discuss it with the user.
- Do not guess or do back-of-the-envelope calculations: write a small script `AI_calculations/AI_CALCULATION_XX.py` (`XX` = short description), run it, and keep it there so the reasoning is documented and verifiable. Never run calculations on the fly; write the script to disk first (for example, solve equations with `sympy` instead of reasoning through the steps). This applies to counts, dates, budgets, and similar figures drawn from documents, not only equations. Scripts in `AI_calculations/` follow [PYTHON_DEVELOPMENT.md](PYTHON_DEVELOPMENT.md).
- Record complex reasoning and ideas worth keeping across sessions in `AI_REASONING.md` (create it if missing, otherwise extend it).
- Make outputs readable by both humans and AI. When a figure shows a few meaningful numbers (for example a small histogram), also give a summary of the plotted data in text or the log so it can be read without viewing the figure. Do not do this for large plots.
- Feel free to suggest meta-improvements to this `AGENTS.md` (new tooling, better recommendations based on real problems).
- When using sub-agents or similar, use the same model as the current one. Do not use a different or more expensive model without asking the user first.

## Project-specific preferences

- For NetCDF data served through THREDDS or a similar service, read from the OpenDAP URL with `xarray`; do not download files unless asked.