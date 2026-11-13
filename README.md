# LinkedIn Positioning Panel

English | [繁體中文](README.zh-TW.md)

**v0.1.3 · Plugin packaging; not yet released.** The skill instructions are identical to the v0.1.2 early testing release.

| Step | Status |
| --- | --- |
| GitHub release v0.1.3 | Not published (v0.1.2 is the latest published release) |
| Anthropic plugin directory listing | Not submitted |

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
| `.claude-plugin/plugin.json` | Plugin manifest: name, version, description, icon, and links (documentation, support, privacy policy) |
| Listing icon | A 1024 × 1024 PNG in the `.claude-plugin` folder, named by the `icon` field in `plugin.json` |
| `skills/linkedin-positioning-panel/SKILL.md` | Canonical skill instructions |
| `skills/linkedin-positioning-panel/LICENSE` | License copy kept with the skill folder |
| `README.md` | Use, test status, and attribution |
| `README.zh-TW.md` | Traditional Chinese documentation |
| `LICENSE` | MIT terms and retained original copyright |
| `CHANGELOG.md` | Release history |
| `PRIVACY.md` | Privacy notice (English and Traditional Chinese) |
| `examples/` | Fictional sample profiles for trying the skill |

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

## Load as a plugin

The repository root is also a Claude plugin. Its manifest is `.claude-plugin/plugin.json`, and its skill is in `skills/`. A listing in Anthropic's plugin directory has not been published; until one is, use the copy-based installation above or load the repository as described here.

### Claude Code

Clone the repository, then start Claude Code **from inside the repository folder**, so that the `examples/` paths below resolve:

```text
git clone https://github.com/jeterchou/linkedin-positioning-panel
cd linkedin-positioning-panel
claude --plugin-dir .
```

Loaded as a plugin, the skill's full name is `linkedin-positioning-panel:linkedin-positioning-panel`. In a Claude Code 2.1.322 check, the short command `/linkedin-positioning-panel` also loaded it. If another skill with the same name is installed, use the full name.

The repository folder is a git repository. If you name no output location, the skill does not write reports inside it; see Output.

### claude.ai chat and Cowork

Skills in a plugin also load in claude.ai chat and Cowork. Until a directory listing exists, add the plugin from a zip of the plugin folder: **Customize → Plugins → Add → Upload plugin**. Skills run in Claude's code sandbox there, so **Code execution and file creation** must be on under Settings → Capabilities.

In one upload test, the SKILL.md SHA-256 that the skill reported in its audit (`92cfa6c5c99898fc4548a1e5ee67be3cada176aa71479357cc1ee97f04af4cf3`) matched the repository file with the multi-line `description` in its front matter rewritten as a single line; the rest was identical. This was observed once and is not established as fixed platform behavior. In the same test, the plugin page listed the plugin as "Linkedin positioning panel", not by its `displayName`, with a generic icon.

claude.ai chat was tested once (see Test status). Cowork has **not been tested**.

## Example prompts

The examples use the fictional profiles in `examples/`. Replace them with your own Profile PDF export or pasted text.

### In Claude Code (started from the repository folder)

1. General Audit with default delivery:
   `/linkedin-positioning-panel Perform a General Audit of examples/sample-profile-en.md.`
2. Target Role Audit, with the reports kept in chat:
   `/linkedin-positioning-panel Perform a Target Role Audit of examples/sample-profile-en.md against this job description: [paste the job description]. Show the reports only in chat; don't write files.`
3. Chinese analysis with an authorized verifier and a chosen output folder:
   `/linkedin-positioning-panel 請對 examples/sample-profile-zh.md 執行 General Audit，報告存到 ~/private/linkedin-review/。我授權使用一個獨立事實檢查代理。`

### In claude.ai chat or Cowork

These examples attach a file or paste text instead of relying on a local project path. Download a sample file from `examples/` on GitHub, attach it to the conversation (or paste its text), and ask in words, for example:

`Use the LinkedIn Positioning Panel skill to perform a General Audit of the attached profile. Use only the attached file.`

The sample profiles deliberately contain a team award, past participation, and figures without a stated period. A careful review keeps that wording as supplied rather than turning it into an individual award, a current role, or an assumed period.

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
- If you don't specify a location and the working directory is inside a git repository, the skill does not write personal reports into that repository. It uses a private location outside the repository if the host permits; otherwise it delivers in chat and asks you to name a location. It suggests a location outside the repository first; any in-repository example is labeled as inside the repository, so choosing it is your explicit decision.
- The skill reports each location's status only as observed: write explicitly prohibited, write attempted and failed, only listing or reading denied, or not attempted. A denied directory listing is not reported as a write failure. The skill does not try to get around an explicit prohibition.
- The skill never overwrites or mixes in earlier reports. If the chosen folder already has report files, the new reports go to a new subfolder.
- The skill never stages, commits, or pushes reports.

Do not commit private inputs or generated personal reports to this public project.

## Data handling

The full privacy notice is in [PRIVACY.md](PRIVACY.md). Issues on this repository are public: do not post private profiles or reports there.

This plugin contains instructions only: one skill, with no hooks, scripts, MCP servers, or other code. It has no backend operated by the author, and the plugin itself sends nothing to the author.

| What happens | Details |
| --- | --- |
| Claude processing | The profile content and anything else you supply are sent to Claude as part of your conversation and processed under your Claude account's terms and data settings. If you authorize agents, they receive the in-scope sources and drafts within the same session. |
| Report files | When the environment supports file writing, a complete audit by default writes three Markdown reports containing your profile content and the analysis to the location described in Output. How long they are kept depends on the host: files in cloud sessions or temporary locations may be removed, so download or copy the reports to a persistent location if you need to keep them. Chat-only delivery writes no report files. While working, the host may also create temporary files, such as page images used to check a PDF's layout, in its working or scratch locations. |
| External lookups | When you ask it to use only the supplied sources, the skill does not browse. Otherwise it may check external claims when you ask for verification, or when it judges that accessible authoritative sources materially affect the audit. Such lookups use only the web or fetch tools your host provides, and they send search terms, such as employer, award, or credential names, to those services. To prevent lookups, say "use only the supplied sources; do not browse." Whether lookups happen without such an instruction has **not been tested**. |
| LinkedIn URLs | URLs are supplementary sources only. The skill does not ask for passwords, cookies, or session tokens, and it does not bypass access controls. Opening a URL, if it happens, uses your host's tools. |
| Author backend | None. |

## Evidence and review rules

Profile statements are not automatically independently verified facts. The skill tracks profile-sourced statements, user confirmations, external corroboration, inference, and unknowns, separately from verification status. Differences in umbrella names, award names, categories, translations, or abbreviations must be investigated before being classified as contradictions.

Silence is not evidence in either direction. Past participation does not become current membership. A profile that does not mention current responsibilities does not show that the person lacks them. The skill does not write "not currently a manager" or "no longer a member" without a source.

The optional verifier receives in-scope sources, all draft alternatives, and recorded reviewer statements, without the author's self-check verdicts. It checks time scope, team versus individual attribution, metric subjects, transaction types, negative current-status claims, and synthesis citations. After at most one repair and one recheck, unresolved material issues remain clearly marked. Any text changed after the recheck is labeled "Changed after recheck; not verifier-checked," and the final reply says so first. A separate verifier does not make simulated positioning perspectives independent, and it does not turn supplied claims into externally corroborated facts.

Never invent or upgrade job titles, employers, dates, responsibilities, team sizes, revenue, awards, credentials, or skills. User aspirations must not be rewritten as past achievements.

## Test status

All tests used fictional data only, in private, temporary projects or accounts, one run per case. Unless a row says otherwise, they ran in Claude Code 2.1.322 on Linux in non-interactive mode (`claude -p`), using an English two-column PDF and Chinese pasted text. The v0.1.3 packaging checks instead used the Markdown samples in `examples/`, and one of them ran in claude.ai chat on the web, not in Claude Code. Where the host reported a model, it was not independently established. Results from one revision are not counted as passes for another.

### Plugin packaging v0.1.3 (SKILL.md unchanged from v0.1.2)

One run per check. SKILL.md is the v0.1.2 release file. The environment is named in each row.

| Check | Observed result |
| --- | --- |
| Package validation (Claude Code 2.1.322, Linux) | `claude plugin validate --strict --profile directory .` passes |
| Claude Code 2.1.322 (Linux, `claude -p`), `--plugin-dir .` from the repository folder, README example 1 with the Markdown sample | Loaded at plugin version 0.1.3. Only the named sample file was opened, no agents were launched, and no web tool was attempted. Three reports were written outside the repository, and git state was unchanged. The host's session scratch folder was used, and the reply said it is temporary |
| claude.ai chat (web), uploaded plugin, General Audit of the attached Markdown sample (Test A) | Behaved as expected on every item checked; see the evidence table below for what each finding rests on |
| claude.ai chat, chat-only request (Test B) | Not tested |
| Cowork | Not tested |

#### claude.ai chat Test A: evidence by source

| Item | Result | Evidence |
| --- | --- | --- |
| Plugin installed | The plugin page showed version v0.1.3, no connectors, "adds only instructions to Claude", the name "Linkedin positioning panel", and a generic icon | Interface: plugin page |
| Skill loaded | The run log showed "Loaded skill linkedin-positioning-panel" | Interface: run log |
| Loaded content | The audit reported SKILL.md SHA-256 `92cfa6c5c99898fc4548a1e5ee67be3cada176aa71479357cc1ee97f04af4cf3`. Reconstruction showed this equals the repository file with only the description rewritten as one line. This is consistent with the uploaded v0.1.3 plugin. It does not show whether an older copy on the account was removed | Report self-statement, checked by reconstruction |
| Files and commands | The run log showed three reports created and shared, and two commands run: checking git status and the output folder, and confirming that the reports exist and are nonempty | Interface: run log |
| Source scope | The audit states that only the attached file was read. The run log shows no other file or web step, but its summary may not list every read | Report self-statement; interface consistent |
| External lookups and agents | The audit states that none were used, and the run log shows none | Report self-statement; interface consistent |
| Execution label and self-check | The exact simulated-mode label and the self-check labeling appear in the reports and the reply | Document review |
| Fact preservation | The team award stays a team award, "600 hours" has no added period, the 18% figure keeps "contributed to", past volunteering is not labeled "former", and coordination stays dated 2021–2022 | Document review |
| Minor interpretations | About adds "with a focus on demand planning", drawn from a three-item Skills list. The analysis calls the award "internal", an inference from its name, in sections labeled as inference | Document review |
| Delivery wording | The reply gave a relative report path without saying where the files are kept or for how long | Document review |
| Not confirmable | Model and app version, the complete list of file reads, and the web search setting (not recorded) | — |

### Version traceability

| File | SHA-256 |
| --- | --- |
| Released SKILL.md (v0.1.2) | `59efb0a511e4a31df450b97cc537acfab997f378ba8aae51b05b99b981e3dcf2` |
| Tested candidate 3 | `2e81d84c403da47be9335bbeff28045ecea6451fc9aefc4c8f7a2520d434ff24` |

Only the revision/status paragraph changed between tested candidate 3 and the v0.1.2 release file; the workflow instructions are identical. The release-labelled file was not separately runtime-tested. This describes the prepared release; it does not confirm that a GitHub tag or release has been published.

### Candidate 3 (tested candidate for v0.1.2; SKILL.md SHA-256 `2e81d84c403da47be9335bbeff28045ecea6451fc9aefc4c8f7a2520d434ff24`)

Candidate 3 changes only the write-permission reporting and the location suggestions after chat delivery. Only those two cases were tested. Each ran in an isolated configuration in which only one skill with this name was available, and that file's SHA-256 matched this candidate. The actual load path did not appear directly in the run records, so attributing the loaded instructions to that file is an inference. Written files, chat explanations, and git state were checked directly.

| Check | Observed result |
| --- | --- |
| Git repository, writes outside the repository denied by permission rules | Alternative delivery behaved as expected; the reason for the denial could not be confirmed. No files were written anywhere, the reports were delivered in chat, and the denial was not circumvented. HEAD, index, working tree, and the remote were unchanged. One command was denied, but it combined several operations and the host did not say which one caused the denial; the run described it as an explicit prohibition of creating a folder, which these records do not confirm. The home folder was reported as not attempted rather than blocked. The suggested location was outside the repository, and no in-repository example was given |
| Git repository, directory listing outside the repository denied but writing allowed | After the listing was denied, the skill attempted the write once; three nonempty reports were written outside the repository, and no blocked location was claimed. HEAD, index, working tree, and the remote were unchanged |

Not exercised in these runs: a denial confirmed to have been caused by a write; a write that was attempted and failed with an error; and labeling an in-repository example (none was offered).

### Candidate 2 (earlier revision; evidence not counted for candidate 3)

Main-agent and sub-agent tool calls were both inspected. File locations and git state were checked directly on disk and with git, not taken from the model's own report. Candidate 3 did not change the rules behind these checks, but they were **not rerun** on candidate 3.

| Check | Candidate 2 result |
| --- | --- |
| YAML/name structure | Frontmatter checked |
| Short full audit, no location, not a git repository | Three nonempty reports written to a new `<date>-<time>-<id>` folder; chat gave a short summary; simulated panel and self-check disclosed; no agents launched |
| Chat-only request | No files written; three reports delivered in chat |
| Authorized verifier, source scope | All 9 of the verifier's tool calls opened only the named source, that run's drafts, and the draft final reply |
| Output folder already containing reports | New reports went to a new subfolder; the earlier files' SHA-256 hashes were unchanged |
| Git repository, no location, host allows a private folder outside the repository | Reports written outside the repository; HEAD, index, working tree, and the remote were unchanged |
| Git repository, user-specified location inside the repository | Reports written there as untracked files; nothing staged, committed, or pushed |
| Git repository, writes outside the repository denied by permission rules | No files written anywhere; reports delivered in chat. The run described the home folder as blocked based on a denied listing, not an attempted write, and its example location was inside the repository. Candidate 3 adds rules for both points |

In the candidate 2 git-repository runs, a second copy of the same instructions (identical body, reformatted description) was also installed at user level; which copy was loaded could not be distinguished.

### Candidate 1 (earlier revision; evidence not counted for candidates 2 or 3)

These areas were tested on candidate 1, one run per case. Later candidates did not change the rules for these areas, but these cases were **not rerun** on candidate 2 or 3.

| Check | Candidate 1 result |
| --- | --- |
| Natural-language triggering | Chinese and English requests triggered the skill; a summarize-only control did not. Runs were stopped after 4 turns, so only triggering and source access were assessed |
| Source scope | The main agent opened only the named file. No agents were launched except one authorized verifier, whose calls were later re-inspected with sub-agent-aware tooling: among the input files, it opened only the named source |
| Missing inputs (no file, URL only, mistyped path) | The skill asked one question without opening other files or substituting a similarly named file |
| Fact preservation (past participation, team awards, ambiguous figures, negative current-status inferences) | Two full runs preserved all planted cases in copy and analysis |

### Not tested

Agent mode for the seven reviewers; interactive sessions, including permission prompts for writing outside a repository; a write attempted and failed with an error; labeling of in-repository location examples; Target Role Audit; supplementary-evidence updates; scanned PDFs; macOS or Windows; repeated runs for reliability; blind first-impression review (not achieved in simulated mode); LinkedIn access, complete exports, and platform character limits.

Source comparison is not external corroboration. PDF-reading tools and extraction quality vary by environment, and users must review every proposed profile edit before publishing. Public documentation describes only the workflow, test scope, and limitations, without disclosing a tester's personal experience, source text, revised copy, or individual confirmation items. Private inputs and personal reports are not distributed.

## Feedback

Open a GitHub Issue describing your environment/model, skill version, input format and supplied sections, reviewer mode, expected behavior, observed behavior, and a minimal synthetic or redacted example. Please remove names, contact details, employer-confidential material, and personal career plans. Do not upload a real profile or report without the person's authorization.

Useful test questions: Were only the named sources opened? Were facts preserved? Were missing sections handled correctly? Did views differ meaningfully? Were naming relationships checked? Did new evidence update old findings? Were all three outputs complete and saved where expected?

## Attribution and license

Independent LinkedIn-focused adaptation of [Hiring Panel Skill](https://github.com/alexyc9381/hiring-panel-skill), created by [Alex Chen](https://github.com/alexyc9381) (known as `@nocodealex`; [chen.media](https://chen.media)). The original introduced a multi-reviewer résumé review and fact-preserving rebuild process.

This adaptation reworks the process for LinkedIn positioning and adds snapshot coverage checks, evidence-state tracking, naming relationship checks, bounded research, and LinkedIn-specific review/output rules. Adaptation and maintenance: Jeter Chou. The adaptation was developed with AI assistance. This does not imply participation, affiliation, or endorsement by the original author, LinkedIn, Anthropic, OpenAI, or an employer.

MIT licensed. The original copyright notice and permission terms are retained in [LICENSE](LICENSE). Keep attribution with redistributed copies. If distributing the skill folder alone, keep its `LICENSE` copy alongside SKILL.md; the SKILL.md attribution paragraph is not a substitute for the license text.
