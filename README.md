# LinkedIn Positioning Panel

English | [繁體中文](README.zh-TW.md)

**v0.1.2 candidate 2 · Pre-release candidate; not released**

An AI-assisted LinkedIn profile review skill for professional positioning, evidence-based revisions, and clear attribution of individual, team, and collaborative work. Designed for people across industries, not a single profession or career stage.

This is an instruction-based skill, not a standalone app, LinkedIn integration, or actual recruiter panel. It does not predict hiring outcomes or LinkedIn search rankings.

## What it does

- General Audit: review professional identity, seniority signals, credible differentiation, and clarity without requiring a target job.
- Target Role Audit: review against a supplied job description while distinguishing missing evidence from actual mismatches.
- Seven reviewer perspectives: Executive Recruiter, Hiring Manager, Executive / Business Leader, Domain Peer, International / Cross-market Reader, Cross-functional Collaborator, and First-impression Reader.
- Create a source inventory, coverage table, evidence ledger, naming/conflict checks, prioritized recommendations, fact-preserving copy, and a before/after re-review.
- Distinguish unavailable evidence from false claims; revise findings when the user supplies new evidence.
- Optionally add a separate factual verifier agent, **only when you explicitly authorize it**, with one repair pass and a focused recheck. This compares copy with supplied sources; it is not external fact-checking.

## Inputs and source scope

Start with a user-provided LinkedIn Profile PDF export or pasted profile text. Screenshots can supplement sections missing from an export. A public LinkedIn URL is supplementary only: it does not prove access to the full profile, and a URL alone is not enough to start a review. Missing export sections are marked **not provided**, not assumed absent from LinkedIn.

The skill opens only sources you name, attach, or paste; an authorized verifier is held to the same scope. Other files in the same folder may be listed by name but are not opened. If no profile is supplied, a named path does not exist, or only a URL is given, the skill asks one question instead of guessing or substituting another file.

No passwords, login cookies, or session tokens are required or requested. The skill does not bypass access controls or publish changes to LinkedIn.

## Execution modes

| Part | Default | When it changes |
| --- | --- | --- |
| Seven reviewer perspectives | **Simulated** in one context, disclosed as "Seven simulated perspectives; not seven independent agents or real hiring professionals." | Only if you explicitly ask for separate reviewer agents for that run; then disclosed as "Seven separate reviewer agents; not real hiring professionals." |
| Factual verifier | **Labeled self-check** by the author, not independent validation | Only if you explicitly authorize a verifier agent. It reads only the sources you named and the drafts. |

Having agent tools available does not count as authorization. Authorizing a verifier does not authorize seven reviewer agents. The skill does not assert which model an agent used; it records model information only where the host reports it.

## Repository layout

| Path | Purpose |
| --- | --- |
| `skills/linkedin-positioning-panel/SKILL.md` | Canonical skill instructions |
| `skills/linkedin-positioning-panel/LICENSE` | License copy kept with the skill folder |
| `README.md` | Use, test status, and attribution |
| `README.zh-TW.md` | Traditional Chinese documentation |
| `LICENSE` | MIT terms and retained original copyright |
| `CHANGELOG.md` | Release history |

## Quick start without installing a skill

In an AI environment able to read Markdown and your input files, supply `SKILL.md` with the profile and ask:

> Read SKILL.md and follow it to perform a General Audit of the supplied profile. Use only the supplied snapshot. Do not use remembered personal information or browse. Save the three reports to [a private folder outside any public repository]. I authorize one separate factual verifier agent when supported; follow the skill's bounded repair and recheck workflow, and disclose actual execution and any fallback.

Omit the verifier sentence if you do not want an agent; the skill then runs a labeled self-check. This tests the instructions; it does not test native skill discovery or installation.

## Claude Code installation for testers

Copy the `linkedin-positioning-panel` folder from this repository's `skills/` directory, including its `LICENSE`, into one of these locations:

| Scope | Destination of SKILL.md |
| --- | --- |
| Current project | `.claude/skills/linkedin-positioning-panel/SKILL.md` |
| Personal installation | `~/.claude/skills/linkedin-positioning-panel/SKILL.md` |

The repository's `skills/` folder alone is not a Claude Code project installation. After copying it, start a session in the relevant project and invoke, for example:

```text
/linkedin-positioning-panel inputs/Profile.pdf
```

A short instruction like this produces a simulated panel, a labeled self-check, and three report files (see Output). To add a verifier agent or choose the output location, say so:

```text
/linkedin-positioning-panel Perform a General Audit of inputs/Profile.pdf. Use only supplied sources. Save the reports to ~/private/linkedin-review/. I authorize one separate factual verifier agent.
```

For a Target Role Audit, also provide a target job description. A current Claude Code account/access method and a model capable of the requested operations are required; model/service costs are separate from this project's license. Check the [official Claude Code skills documentation](https://code.claude.com/docs/en/skills) for current loading behavior.

## Output

| Output | Contents |
| --- | --- |
| `PROFILE-AUDIT.md` | Sources, coverage, evidence, seven views, priorities, verification record, and verification queue |
| `POSITIONING-STRATEGY.md` | Inferred positioning, supplied career goals, trade-offs, and next steps |
| `LINKEDIN-REVISED.md` | Headline alternatives, About, all supplied Experience entries, change log, and re-review |

**Where reports go:**

- When file writing is supported, a complete audit writes the three files by default, and the chat shows only a summary with the file paths.
- If you ask for chat-only output (for example, "only in chat" or "don't write files"), no files are written and the reports appear in chat.
- If you specify an output location, the skill uses it, including a location inside a git repository; it does not stage, commit, or push the reports.
- If you don't specify a location and the working directory is not inside a git repository, the reports go to `linkedin-positioning-panel/<date>-<time>-<id>/` in that directory.
- If you don't specify a location and the working directory is inside a git repository, the skill does not write personal reports into that repository. It uses a private location outside the repository if the host permits; otherwise it delivers in chat and asks you to name a location.
- The skill never overwrites or mixes in earlier reports. If the chosen folder already has report files, the new reports go to a new subfolder.
- The skill never stages, commits, or pushes reports.

Do not commit private inputs or generated personal reports to this public project.

## Evidence and review rules

Profile statements are not automatically independently verified facts. The skill tracks profile-sourced statements, user confirmations, external corroboration, inference, and unknowns, separately from verification status. Differences in umbrella names, award names, categories, translations, or abbreviations must be investigated before being classified as contradictions.

Silence is not evidence in either direction. Past participation does not become current membership. A profile that does not mention current responsibilities does not show that the person lacks them. The skill does not write "not currently a manager" or "no longer a member" without a source.

The optional verifier receives in-scope sources, all draft alternatives, and recorded reviewer statements, without the author's self-check verdicts. It checks time scope, team versus individual attribution, metric subjects, transaction types, negative current-status claims, and synthesis citations. After at most one repair and one recheck, unresolved material issues remain clearly marked. Any text changed after the recheck is labeled "Changed after recheck; not verifier-checked," and the final reply says so first. A separate verifier does not make simulated positioning perspectives independent, and it does not turn supplied claims into externally corroborated facts.

Never invent or upgrade job titles, employers, dates, responsibilities, team sizes, revenue, awards, credentials, or skills. User aspirations must not be rewritten as past achievements.

## Test status

All tests below used fictional profiles only (an English two-column PDF and Chinese pasted text) in private, temporary projects. They ran in Claude Code 2.1.322 on Linux in non-interactive mode (`claude -p`), one run per case. The host reported the model; it was not independently established. Results from one revision are not counted as passes for another.

### Candidate 2 (this revision; SKILL.md SHA-256 `05e9be5a68683454edd673c149dff3f18143ffa5d997a49952e6511d46e48838`)

Main-agent and sub-agent tool calls were both inspected. File locations and git state were checked directly on disk and with git, not taken from the model's own report.

| Check | Observed result |
| --- | --- |
| YAML/name structure | Frontmatter checked |
| Short full audit, no location, not a git repository | Three nonempty reports written to a new `<date>-<time>-<id>` folder; chat gave a short summary; simulated panel and self-check disclosed; no agents launched |
| Chat-only request | No files written; three reports delivered in chat |
| Authorized verifier, source scope | All 9 of the verifier's tool calls opened only the named source, that run's drafts, and the draft final reply |
| Output folder already containing reports | New reports went to a new subfolder; the earlier files' SHA-256 hashes were unchanged |
| Git repository, no location, host allows a private folder outside the repository | Reports written outside the repository; HEAD, index, working tree, and the remote were unchanged |
| Git repository, user-specified location inside the repository | Reports written there as untracked files; nothing staged, committed, or pushed |
| Git repository, writes outside the repository denied by permission rules | No files written anywhere; reports delivered in chat with a request for a location. The run inferred that the home folder was blocked from a denied listing rather than from an attempted write |

In the git-repository runs, a second copy of the same instructions (identical body, reformatted description) was also installed at user level; which copy was loaded could not be distinguished.

### Candidate 1 (earlier revision; evidence not counted for candidate 2)

These areas were tested on candidate 1, one run per case. Candidate 2 did not change the rules for these areas, but these cases were **not rerun** on candidate 2.

| Check | Candidate 1 result |
| --- | --- |
| Natural-language triggering | Chinese and English requests triggered the skill; a summarize-only control did not. Runs were stopped after 4 turns, so only triggering and source access were assessed |
| Source scope | The main agent opened only the named file. No agents were launched except one authorized verifier, whose calls were later re-inspected with sub-agent-aware tooling: among the input files, it opened only the named source |
| Missing inputs (no file, URL only, mistyped path) | The skill asked one question without opening other files or substituting a similarly named file |
| Fact preservation (past participation, team awards, ambiguous figures, negative current-status inferences) | Two full runs preserved all planted cases in copy and analysis |

### Not tested

Agent mode for the seven reviewers; interactive sessions; Target Role Audit; supplementary-evidence updates; scanned PDFs; macOS or Windows; repeated runs for reliability; blind first-impression review (not achieved in simulated mode); LinkedIn access, complete exports, and platform character limits.

Source comparison is not external corroboration. PDF-reading tools and extraction quality vary by environment, and users must review every proposed profile edit before publishing. Public documentation describes only the workflow, test scope, and limitations, without disclosing a tester's personal experience, source text, revised copy, or individual confirmation items. Private inputs and personal reports are not distributed.

## Feedback

Open a GitHub Issue describing your environment/model, skill version, input format and supplied sections, reviewer mode, expected behavior, observed behavior, and a minimal synthetic or redacted example. Please remove names, contact details, employer-confidential material, and personal career plans. Do not upload a real profile or report without the person's authorization.

Useful test questions: Were only the named sources opened? Were facts preserved? Were missing sections handled correctly? Did views differ meaningfully? Were naming relationships checked? Did new evidence update old findings? Were all three outputs complete and saved where expected?

## Attribution and license

Independent LinkedIn-focused adaptation of [Hiring Panel Skill](https://github.com/alexyc9381/hiring-panel-skill), created by [Alex Chen](https://github.com/alexyc9381) (known as `@nocodealex`; [chen.media](https://chen.media)). The original introduced a multi-reviewer résumé review and fact-preserving rebuild process.

This adaptation reworks the process for LinkedIn positioning and adds snapshot coverage checks, evidence-state tracking, naming relationship checks, bounded research, and LinkedIn-specific review/output rules. Adaptation and maintenance: Jeter Chou. The adaptation was developed with AI assistance. This does not imply participation, affiliation, or endorsement by the original author, LinkedIn, Anthropic, OpenAI, or an employer.

MIT licensed. The original copyright notice and permission terms are retained in [LICENSE](LICENSE). Keep attribution with redistributed copies. If distributing the skill folder alone, keep its `LICENSE` copy alongside SKILL.md; the SKILL.md attribution paragraph is not a substitute for the license text.
