---
name: tailor-resume
description: >-
  Tailor AmritSinhaCV.tex to a job description and write the result to
  tailored/. Use when the user pastes a JD, asks to customize their resume for
  a company/role, or mentions tailored resume, AmritSinhaCV_Company, or
  resume matching for an application.
---

# Tailor Resume to Job Description

## Source of truth

- **Base resume only:** `AmritSinhaCV.tex` at repo root
- **Never** use other files in `tailored/` as the source template
- **Never** invent experience, skills, or metrics not supported by the base resume

## Output

| Item | Rule |
|------|------|
| Directory | `tailored/` |
| Filename | `AmritSinhaCV_{CompanyOrRole}.tex` — PascalCase, no spaces |
| PDF | Compile with `pdflatex` from `tailored/`; output must be **1 page** |
| Git | `tailored/` is gitignored — do not commit tailored files unless the user asks |

## Workflow

```
Task Progress:
- [ ] Read AmritSinhaCV.tex (full file)
- [ ] Parse JD for stack, responsibilities, seniority, keywords
- [ ] Copy base LaTeX preamble/commands unchanged
- [ ] Add or skip Summary (see below)
- [ ] Reorder/reframe bullets — same facts, JD-aligned wording
- [ ] Reorganize Technical Skills for JD keywords
- [ ] Write tailored/AmritSinhaCV_{Name}.tex
- [ ] Compile PDF and confirm 1 page
- [ ] Report estimated JD match % and gaps
```

## Tailoring rules

### Summary
- **Include** for JD-specific applications when it adds framing the experience section lacks
- **Lead with** role-relevant stack (e.g. Django/DRF for backend roles)
- **Do not** use fluffy phrases ("motivated", "passionate", "team player")
- **Keep to 2–3 lines** max

### Experience
- Reuse **base resume bullet content** — reorder and lightly rephrase for JD keywords
- Do **not** merge facts from other tailored versions
- Do **not** claim mentoring, technical documentation, or tools absent from base
- Prioritize bullets that match JD: APIs, performance, security, databases, stack named in JD
- Trim lowest-relevance bullets if needed for 1 page

### Projects
- Keep project facts from base; emphasize JD-relevant angles (e.g. data pipelines vs GenAI)
- Trim to 2–3 bullets if space is tight

### Technical Skills
- Regroup (do not dump a generic list) — put JD stack first
- Only list skills present in base resume content

## Compile

```bash
cd tailored
pdflatex -interaction=nonstopmode AmritSinhaCV_{Name}.tex
```

If output is 2 pages: shorten summary, combine bullets, or trim project bullets. Recompile until 1 page.

## Finish message

After creating the file, briefly report:
1. Output path(s)
2. What was emphasized for this JD
3. Estimated match % with main gaps
4. Anything intentionally omitted (and why)

## Example prompt (user)

> Tailor my resume for this role at Stripe — [paste JD]

## Reference examples

If the JD type is unclear, read one or two existing `.tex` files in `tailored/` for tone and structure. Pick whichever best matches the role; do not treat any single file as the canonical template.
