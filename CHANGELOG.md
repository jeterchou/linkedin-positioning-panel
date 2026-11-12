# Changelog

## v0.1.2 — Prepared 2026-11-12

Early testing release prepared for publication; the GitHub tag and release are created separately by the maintainer.

### Changed

- Seven reviewer perspectives now run in simulated mode by default. Separate reviewer agents are used only when the user explicitly asks for them for that run; having agent tools available is not authorization.
- The factual verifier agent also requires explicit authorization. Without it, the author runs a labeled self-check and tells the user how to authorize a verifier.
- Execution is disclosed with exactly one of two fixed labels. The skill no longer asserts which model or model family an agent used; it records model information only where the host reports it.
- Section 3 is renamed "Seven reviewer perspectives."
- A complete audit now writes the three reports by default when file writing is supported, with a short chat summary. Chat-only output is used when the user asks for it.
- Output location: a user-specified location is used as given. Without one, reports are not written into a git repository by default; a private location outside it is used where permitted, otherwise the reports are delivered in chat. Reports are never staged, committed, or pushed.
- Default output folders include date, time, and an id. Existing folders and report files are never reused, overwritten, or mixed with new reports.

### Added

- Source scope rules: only sources the user names, attaches, pastes, or approves are opened, by the author and by any agent. If no source is supplied, a path does not exist, only a URL is supplied, or the sources describe different people, the skill asks one question and does not substitute files.
- Negative current-status claims from silence (for example, "not currently a manager") are prohibited in copy and analysis and included in the verifier checklist.
- Text changed after the verifier's recheck is labeled "Changed after recheck; not verifier-checked," and the final response states this first.
- Acceptance checks for source scope, delivery, and execution labels.
- Candidate 3: write-permission status is reported only as observed (write explicitly prohibited, write attempted and failed, only listing or reading denied, or not attempted). A denied listing is not reported as a write failure, and explicit prohibitions are not circumvented.
- Candidate 3: after chat delivery, location suggestions start with a location outside the repository. Any in-repository example is labeled as such.

### Validation

Tests used fictional profiles only, in Claude Code 2.1.322 on Linux in non-interactive mode, one run per case. Evidence is recorded per revision and is not carried forward. See README Test status for details.

- **Candidate 3** (SKILL.md SHA-256 `2e81d84c403da47be9335bbeff28045ecea6451fc9aefc4c8f7a2520d434ff24`): two git-repository cases were tested, each in an isolated configuration where only one skill of this name was available, matching this candidate's SHA-256. The actual load path was not directly recorded, so attribution to that file is an inference. Written files, chat explanations, and git state were checked directly. (1) Writes outside the repository denied by permission rules: alternative delivery behaved as expected (no files written, reports in chat, denial not circumvented, git state unchanged), but the reason for the denial could not be confirmed, because the one denied command combined several operations. (2) Outside listing denied, writing allowed: the write was attempted, and three nonempty reports were written outside the repository with git state unchanged. Not exercised: a denial confirmed to have been caused by a write, a write that failed with an error, and labeling an in-repository example.
- **Candidate 2** (SKILL.md SHA-256 `05e9be5a68683454edd673c149dff3f18143ffa5d997a49952e6511d46e48838`): default file delivery, chat-only delivery, verifier source scope, existing output folders, and three git-repository delivery cases. Not rerun on candidate 3.
- **Candidate 1**: source scope, missing-input handling, natural-language triggering, and fact preservation. Not rerun on candidate 2 or 3.
- **Release file** (SKILL.md SHA-256 `59efb0a511e4a31df450b97cc537acfab997f378ba8aae51b05b99b981e3dcf2`): only the revision/status paragraph changed from tested candidate 3 (`2e81d84c403da47be9335bbeff28045ecea6451fc9aefc4c8f7a2520d434ff24`); workflow instructions are identical. The release-labelled file was not separately runtime-tested.
- Agent mode for the seven reviewers, interactive sessions, Target Role Audit, supplementary-evidence updates, scanned PDFs, other operating systems, and repeat reliability remain untested.

## v0.1.1 — Prepared 2026-11-12

Early testing release prepared for publication; the GitHub tag is created separately by the maintainer.

### Changed

- Add Traditional Chinese usage contexts to the skill description; natural-language discovery remains untested.
- Preserve time scope, combined staffing groups, award attribution, metric subjects, transaction categories, and explicit confirmation scope across all outputs and alternatives.
- Trace synthesis opinions to recorded reviewer statements instead of inventing disagreements.
- Separate unsupported rewrite additions from demonstrated falsehoods in supplied profiles.
- Use Ready to edit / Confirmation required labels separately from provenance and external corroboration.
- Respect a user-specified output directory and record observable revision/hash information.

### Added

- A separate factual verifier when supported and authorized, additional to the seven positioning perspectives.
- One bounded repair pass and one focused recheck, with unresolved blockers disclosed in the existing reports.
- An explicit self-check fallback when an independent verifier is unavailable or prohibited.

### Validation

- Candidate 3 completed one maintainer-reported Claude Code 2.1.322 run on macOS 26.7.1: seven simulated positioning views plus one fresh-context factual verifier, one repair and one recheck.
- The verifier reported no remaining material blockers, with two minor risks retained and disclosed. This is not external fact-checking or evidence of general reliability.
- Only the revision/status paragraph changed between tested candidate 3 and the prepared release; workflow instructions are identical. The release-labelled file was not separately runtime-tested.
- Seven independent positioning reviewers, blind first-impression review, natural-language discovery, Target Role Audit runtime behavior, and broad reliability remain unvalidated.

## v0.1.0 — Prepared 2026-11-12

Initial early testing release. Publication date and GitHub release tag are assigned when the maintainer publishes; this file does not claim a release has already been published.

### Included

- General Audit and Target Role Audit.
- Seven reviewer perspectives with independent-versus-simulated execution disclosure.
- Profile Snapshot inputs from PDFs, text, and screenshots; URLs as supplementary sources.
- Section coverage checks, source/evidence ledger, conflict and naming relationship handling.
- Separate unavailable evidence, supplied claims, and demonstrated errors.
- Reassessment when users provide new evidence, with superseded findings withdrawn.
- Bounded verification queue, fact-preserving rewrites, full supplied Experience coverage, and three report outputs.
- Original Hiring Panel attribution and retained MIT copyright/permission terms.

### Known limitations

- One private real-profile development run with simulated views does not establish cross-industry or cross-model reliability.
- Seven independent reviewers and a blind first-impression workflow have not been validated end to end.
- Native Claude Code installation and execution have not been runtime-tested.
- PDF exports may omit sections, and profile URLs may be inaccessible.
- Historical record claims require comparison scope, dates, and comparable transaction data.
- No automated LinkedIn editing, scraping integration, search-ranking prediction, or employment guarantees.

### Feedback requested

Test fact preservation, missing-section handling, meaningful differences between views, naming relationships, updates after new evidence, and completeness of all three reports. Use synthetic or appropriately redacted examples when reporting issues.
