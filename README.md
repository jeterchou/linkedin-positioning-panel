# LinkedIn Positioning Panel

English | [繁體中文](README.zh-TW.md)

**v0.1.1 · Early testing release**

An AI-assisted LinkedIn profile review skill for professional positioning, evidence-based revisions, and clear attribution of individual, team, and collaborative work. Designed for people across industries, not a single profession or career stage.

This is an instruction-based skill, not a standalone app, LinkedIn integration, or actual recruiter panel. It does not predict hiring outcomes or LinkedIn search rankings.

## What it does

- General Audit: review professional identity, seniority signals, credible differentiation, and clarity without requiring a target job.
- Target Role Audit: review against a supplied job description while distinguishing missing evidence from actual mismatches.
- Seven reviewer perspectives: Executive Recruiter, Hiring Manager, Executive / Business Leader, Domain Peer, International / Cross-market Reader, Cross-functional Collaborator, and First-impression Reader.
- Create a source inventory, coverage table, evidence ledger, naming/conflict checks, prioritized recommendations, fact-preserving copy, and a before/after re-review.
- Distinguish unavailable evidence from false claims; revise findings when the user supplies new evidence.
- Add a separate factual comparison gate when agent tools are available and authorized, with one repair pass and a focused recheck. This compares copy with supplied sources; it is not external fact-checking.

## Inputs

Start with a user-provided LinkedIn Profile PDF export or pasted profile text. Screenshots can supplement sections missing from an export. A public LinkedIn URL is supplementary only: it does not prove access to the full profile. Missing export sections are marked **not provided**, not assumed absent from LinkedIn.

No passwords, login cookies, or session tokens are required or requested. The skill does not bypass access controls or publish changes to LinkedIn.

## Repository layout

| Path | Purpose |
| --- | --- |
| `skills/linkedin-positioning-panel/SKILL.md` | Canonical skill instructions |
| `README.md` | Use, test status, and attribution |
| `README.zh-TW.md` | Traditional Chinese documentation |
| `LICENSE` | MIT terms and retained original copyright |
| `CHANGELOG.md` | Release history |

## Quick start without installing a skill

In an AI environment able to read Markdown and your input files, supply `SKILL.md` with the profile and ask:

> Read SKILL.md and follow it to perform a General Audit of the supplied profile. Use only the supplied snapshot and explicit supplementary evidence. Do not use remembered personal information or browse. Disclose whether the seven perspectives are simulated or independently executed. Produce PROFILE-AUDIT.md, POSITIONING-STRATEGY.md, and LINKEDIN-REVISED.md, or their clearly labeled equivalents if file creation is unavailable. Keep all outputs private and outside the public repository. I authorize a separate factual verifier when supported; follow the skill’s bounded repair and recheck workflow, and disclose any fallback to self-checking.

This tests the instructions; it does not test native skill discovery or installation.

## Claude Code installation for testers

**The behavior-identical v0.1.1 candidate 3 completed one maintainer-reported run in Claude Code 2.1.322 with seven simulated positioning perspectives and one separate factual verifier. See Test status for scope and remaining limitations.** Copy the `linkedin-positioning-panel` folder from this repository's `skills/` directory into one of these locations:

| Scope | Destination |
| --- | --- |
| Current project | `.claude/skills/linkedin-positioning-panel/SKILL.md` |
| Personal installation | `~/.claude/skills/linkedin-positioning-panel/SKILL.md` |

The repository's `skills/` folder alone is not a Claude Code project installation. After copying it, start a session in the relevant project and invoke:

```text
/linkedin-positioning-panel
Perform a General Audit of the profile file I provide. Use only supplied sources. For this run, simulate the seven positioning perspectives and use one separate factual verifier; I authorize that subagent when supported by the host. Follow the bounded repair and recheck workflow, disclose actual execution and any fallback, and save the three reports to a private working directory outside this repository.
```

For a Target Role Audit, also provide a target job description. A current Claude Code account/access method and a model capable of the requested operations are required; model/service costs are separate from this project's license. Check the [official Claude Code skills documentation](https://code.claude.com/docs/en/skills) for current loading behavior.

## Expected output

| Output | Contents |
| --- | --- |
| `PROFILE-AUDIT.md` | Sources, coverage, evidence, seven views, priorities, and verification queue |
| `POSITIONING-STRATEGY.md` | Inferred positioning, supplied career goals, trade-offs, and next steps |
| `LINKEDIN-REVISED.md` | Headline alternatives, About, all supplied Experience entries, change log, and re-review |

Supported environments can write these files; others should return equivalent Markdown sections and disclose the limitation. Do not commit private inputs or generated personal reports to this public project.

## Evidence and review rules

Profile statements are not automatically independently verified facts. The skill tracks profile-sourced statements, user confirmations, external corroboration, inference, and unknowns, separately from verification status. Differences in umbrella names, award names, categories, translations, or abbreviations must be investigated before being classified as contradictions.

Use independent agents only when supported and authorized. Otherwise disclose seven **simulated perspectives**. Same-model passes do not become independent evidence; a first-impression pass that already saw the full profile is not a blind test.

The separate factual verifier receives source materials, all draft alternatives, and recorded reviewer statements without the author’s self-check verdicts. It checks time scope, team versus individual attribution, metric subjects, transaction types, and synthesis citations. After at most one repair and one recheck, unresolved material issues must remain clearly marked. If a separate agent is unavailable or prohibited, disclose self-checking instead. A separate verifier does not make seven simulated positioning perspectives independent, and it does not turn supplied claims into externally corroborated facts.

Never invent or upgrade job titles, employers, dates, responsibilities, team sizes, revenue, awards, credentials, or skills. User aspirations must not be rewritten as past achievements.

## Test status

| Check | v0.1.1 evidence and limits |
| --- | --- |
| YAML/name structural validation | Completed in the development environment |
| Claude Code execution | Candidate 3 completed one maintainer-reported run in Claude Code 2.1.322 on macOS 26.7.1, producing all three reports |
| Positioning reviewer mode | Seven simulated perspectives in one author context; not seven independent reviewers |
| Separate factual verifier | One fresh-context agent checked the drafts; one repair and one recheck were recorded |
| Factual gate outcome | The verifier reported no remaining material blockers after repair; two minor risks were retained and disclosed |
| Blind first-impression review | Not tested; full-profile exposure disclosed |
| Natural-language discovery in English or Chinese | Not tested; invocation used `/linkedin-positioning-panel` |
| External corroboration | Not performed in the candidate 3 source-only run |
| Supplementary-evidence updates | Exercised on earlier revisions; not rerun on candidate 3 |
| Target Role Audit and cross-industry/model reliability | Not established by this General Audit test |
| LinkedIn access, complete exports, platform character limits | Not guaranteed; live limits were not checked in the test |

### Version traceability

The tested candidate 3 SHA-256 was `5c405c7606473caa289949fa2fb27d01e7fc19ea805dd94a04d0ddbf5d627aff`. Release preparation changes only the revision/status paragraph in SKILL.md, so the release file has a different hash. Its workflow instructions are unchanged; the release-labelled file was not separately rerun in Claude Code. This describes a prepared release, not confirmation that a GitHub tag has been published. Model identity was not independently established.

### What the test showed

In one test run, a separate factual verifier identified inconsistencies between draft revisions and the supplied sources, followed by repair and recheck. This shows that the workflow caught draft errors in that run; it does not establish a dependable detection rate or general reliability.

Source comparison is not external corroboration. PDF-reading tools and extraction quality vary by environment, and users must review every proposed profile edit before publishing. Public documentation describes only the workflow, test scope, and limitations, without disclosing a tester's personal experience, source text, revised copy, or individual confirmation items. Private inputs and personal reports are not distributed.

## Feedback

Open a GitHub Issue describing your environment/model, skill version, input format and supplied sections, reviewer mode, expected behavior, observed behavior, and a minimal synthetic or redacted example. Please remove names, contact details, employer-confidential material, and personal career plans. Do not upload a real profile or report without the person's authorization.

Useful test questions: Were facts preserved? Were missing sections handled correctly? Did views differ meaningfully? Were naming relationships checked? Did new evidence update old findings? Were all three outputs complete?

## Attribution and license

Independent LinkedIn-focused adaptation of [Hiring Panel Skill](https://github.com/alexyc9381/hiring-panel-skill), created by [Alex Chen](https://github.com/alexyc9381) (known as `@nocodealex`; [chen.media](https://chen.media)). The original introduced a multi-reviewer résumé review and fact-preserving rebuild process.

This adaptation reworks the process for LinkedIn positioning and adds snapshot coverage checks, evidence-state tracking, naming relationship checks, bounded research, and LinkedIn-specific review/output rules. Adaptation and maintenance: Jeter Chou. The adaptation was developed with AI assistance. This does not imply participation, affiliation, or endorsement by the original author, LinkedIn, Anthropic, OpenAI, or an employer.

MIT licensed. The original copyright notice and permission terms are retained in [LICENSE](LICENSE). Keep attribution with redistributed copies. If distributing the skill folder alone, include a copy of the repository LICENSE alongside SKILL.md; the SKILL.md attribution paragraph is not a substitute for the license text.
