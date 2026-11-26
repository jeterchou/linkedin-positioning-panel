# Submission preparation — v0.1.3 candidate

Updated 2026-11-26. This is a preparation record, not an attestation, legal opinion, release, or submission. Latest published tag remains v0.1.2. This candidate revises the external-lookup rules; historical runtime tests do not validate it.

## Scope and evidence

- Continue the existing privacy-notice PR #4; do not merge, tag, publish, accept terms, or submit for review as part of this preparation.
- User authorization, 2026-11-26: proceed with the proposed preparation: fix external-query authorization, align privacy documents and declarations, and disclose unresolved policy 1G and host-tool questions with ticket #155319255 before deciding whether to submit.
- Sources: repository main `eccb830`, the existing PR #4, current official [Directory Policy](https://support.claude.com/en/articles/13145358-anthropic-software-directory-policy) and [Directory Terms](https://support.claude.com/en/articles/13145338-anthropic-software-directory-terms), existing compliance-page capture supplied on 2026-11-13, and the inquiry sent on 2026-11-13.
- Ticket #155319255 belongs to **Anthropic**, not OpenAI. The email thread inspected on 2026-11-26 contains the inquiry and receipt acknowledgement, not a substantive policy ruling. The acknowledgement is not approval.
- Live portal access on 2026-11-26 redirected to sign-in. Current saved draft, required-field state and latest scan results could not be inspected. The captured wording below is historical, not claimed as today's UI.

## Declaration comparison

| Item | Candidate behavior / evidence | Preparation status |
| --- | --- | --- |
| External tools, policy 2D | Explicit request or approved lookup scope required; applies to URL retrieval, deeper research and agents. General review and perceived usefulness do not authorize lookups. Without authorization, complete the source-based audit and queue optional checks. | Instructions and both READMEs/privacy notice aligned; Claude runtime retest outstanding. This change is not an Anthropic ruling. |
| Personal data | User-supplied professional profile content is read and processed by Claude. It can include third-party personal information. | Disclose **yes**, not “no personal data.” |
| Files and retention | Complete audits still write three Markdown reports by default where permitted; chat-only delivery prevents report files. Host processing can create temporary PDF text/images even in chat-only mode. Host controls retention. | Disclose both report and temporary files; no claim of zero storage. Default delivery is unchanged, not silently switched to opt-in. |
| External services | No declared connectors or author backend. Authorized host web tools can send minimal search terms and requested URLs to external services. | Do not answer “no external transmission” without this qualification. Actual recipient services depend on the host; identify them before any sensitive lookup. |
| Privacy-policy accuracy checkbox | Revised bilingual PRIVACY.md covers inputs, Claude processing, authorized agents/lookups, reports, temporary files, retention, support, and possible directory statistics. | Draft only. The manifest's main-branch policy URL does not resolve until the PR is merged. Verify the published URL and exact saved candidate before attesting. |
| Terms/policy checkbox | Submission entails representations about intended use and compliance; uploaded-profile analysis and default reports remain subject to the 1G interpretation question. | Unresolved; no unqualified compliance assurance prepared. Disclosure does not override the terms or replace an attestation. |
| Credential/code checkbox | Historical UI: “The plugin does not exfiltrate credentials or execute code outside its declared MCP servers.” The package has no MCP servers, hooks, commands, scripts, or executable code. Claude host tools may extract PDFs, inspect git state, and write files. | Credential exfiltration is not instructed; whether host-tool execution fits the latter half is unresolved. Do not treat the whole combined checkbox as established. Cite ticket #155319255. |
| Contact permission checkbox | Historical UI allows Anthropic to contact the publisher about the submission and future policy changes. | Publisher action; no new consent recorded here. |

## Prepared data-handling answers

**Reads or stores personal data:** Yes. Claude reads the professional profile content the user supplies for the requested review. This instructions-only plugin operates no backend. A complete audit normally writes three reports containing profile content and analysis, subject to host permissions; users can request chat-only report delivery. The host may create temporary processing files, including extracted PDF text or page images. Chat-only delivery does not guarantee zero temporary files.

**Sends data beyond declared connectors:** The plugin declares no connectors and runs no network code. Supplied content is processed by Claude under the user's account. External web searches or page retrieval require an explicit user request or approval of the lookup scope, also for agents. Those lookups use host-provided web tools and may transmit minimal necessary search terms and requested URLs to their services. Sensitive transmission requires a prior explanation of the data and destination and specific authorization. The plugin does not automatically send profiles or reports to the author; material users voluntarily post in public Issues is public and visible to the author.

**Retention:** The plugin runs no storage service. Claude conversations, generated report files and temporary processing files are retained or removed according to the host and account settings. Reports can contain personal data; users should copy files they need to retain and delete copies they no longer need. No fixed retention duration is promised.

**Under-18 targeting:** No new answer inferred. Reuse a previously confirmed publisher answer if available; otherwise obtain the publisher's intended audience decision before filling this field. The earlier draft's “adults only” suggestion was not proof of a decision.

## Reviewer note draft (not sent)

LinkedIn Positioning Panel is an instructions-only plugin with one skill and no hooks, commands, scripts, MCP/LSP servers, connectors, or author-operated backend. It reviews only professional profile sources the user supplies or explicitly approves; external lookups require a separate explicit request or approved lookup scope. It does not instruct retrieval from Claude memory, chat history, or conversation summaries, and does not build cross-session user profiles.

For transparency, its intended function includes reading an explicitly supplied profile PDF, pasted text, or screenshots. A complete audit normally creates three Markdown reports through the Claude host when permitted; chat-only report delivery is available, but host temporary processing files may still be created. The host may use built-in tools for PDF extraction, git-location checks, and file writing; those tools are not declared MCP servers belonging to this plugin.

Please refer to Anthropic support ticket #155319255, opened on November 13, 2026, for the unresolved questions about policy 1G's application to user-requested attachment analysis and generated reports, and the compliance acknowledgement concerning code execution outside declared MCP servers. We have not received a substantive ruling in the email thread inspected on November 26. We disclose these behaviors rather than claiming that the ticket, the lack of a reply, or this note establishes compliance. If the required acknowledgements cannot accommodate these facts, the exact acknowledgement needs clarification before submission.

## Verification and remaining gates

- This preparation does not incorporate the separate local v0.1.4 candidate or its unmerged tool/delivery experiments.
- Structural/content checks and independent AI review are separate from Claude runtime tests, directory security/policy scans, publisher attestations, and user acceptance.
- Claude CLI is absent from this execution environment; actual Claude tests were not run for this revision. Retest the revised lookup gate with fictional data: ordinary audit (no web), supplied URL without an open request (no fetch), explicit scoped lookup (only that scope), source-only request (no web), and an authorized verifier without web authorization (no web).
- Before submission: resolve independent-review findings, verify the exact saved revision and public privacy URL after an authorized merge, run applicable validation/scans and the revised cases, inspect the current form after sign-in, resolve any missing publisher-only answer, and obtain accurate attestations. If 1G or the combined code checkbox still requires an unsupported guarantee, record that specific blocker and seek Anthropic clarification; do not submit by guessing.
