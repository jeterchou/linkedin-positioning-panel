# Privacy Notice — LinkedIn Positioning Panel

English | [繁體中文](#隱私權說明--linkedin-positioning-panel)

Effective: 2026-11-13 · Applies to plugin version 0.1.3 and the skill instructions released as v0.1.2. Changes to this notice are tracked in this repository's history.

LinkedIn Positioning Panel is an instructions-only Claude plugin. It contains one skill (written instructions) and no code, hooks, scripts, MCP servers, or connectors. The author does not run any service for it. It is not affiliated with or endorsed by LinkedIn.

## What the plugin reads

- **Only what you supply for the review you request.** The skill opens only sources you name, attach, or paste in the conversation, such as a LinkedIn Profile PDF export, pasted profile text, screenshots, or a job description. It does not open other files in the same folder unless you approve them.
- **Personal data.** These sources normally contain personal data about you, such as your name, employment history, and achievements. They can also contain information about other people, such as names in recommendations. Supply only what you are entitled to share and need reviewed.
- **Context the host provides.** The skill does not instruct Claude to search or retrieve Claude's memory, your chat history, or conversation summaries, and it does not build a profile of you across sessions. Your Claude application may still include such context in a conversation on its own, depending on your settings. That context is handled by the application under your account's terms, not by this plugin.

## How the content is processed

- **By Claude, under your account.** The content you supply is processed by Claude as part of your conversation, under the terms and data settings of your Claude account. See [Anthropic's Privacy Policy](https://www.anthropic.com/legal/privacy).
- **Agents, only if you authorize them.** If you explicitly authorize separate reviewer or verifier agents, they receive the in-scope sources and drafts within the same session.

## Report files

- **When they are written.** When the environment supports file writing, a complete review writes three Markdown reports by default. The reports contain your profile content and the analysis.
- **Where they go.** Reports go to a location you specify. Otherwise they go to a private location outside any git repository. If neither is possible, they are delivered in chat. The skill never stages, commits, or pushes reports.
- **How long they are kept.** Retention depends on the host Claude application, not on this plugin. Files in cloud sessions or temporary locations may be removed. Download or copy reports you want to keep, and delete them when you no longer need them.
- **Avoiding files.** Ask for chat-only delivery ("show the reports only in chat") if you do not want report files written.

## Optional external lookups

- **When they happen.** Unless you ask the skill to use only the supplied sources, it may check external claims when you ask for verification, or when it judges that accessible authoritative sources materially affect the review.
- **What is sent.** Such lookups use only the web search or fetch tools provided by your Claude application. They send search terms, such as employer, award, or credential names, to those services, under their own terms.
- **Preventing them.** Say "use only the supplied sources; do not browse."
- **Credentials.** The skill never asks for passwords, cookies, or session tokens, and does not bypass access controls.

## What the author receives

- **Nothing sent automatically.** The plugin has no backend and does not automatically send your profile, your reports, or your conversations to the author.
- **What you choose to share.** If you contact the author, for example by opening a GitHub issue, the author receives whatever you include. For a public issue, so does anyone who can view the repository. Do not include private profiles, reports, or contact details.
- **Usage statistics, if listed.** If the plugin is listed in Anthropic's plugin directory, Anthropic's developer portal may show the author usage statistics, such as install counts, versions, how often the skill runs, and error rates. Anthropic determines what those statistics include.

## Support and issues

- **Issues are public.** Report problems at [GitHub Issues](https://github.com/jeterchou/linkedin-positioning-panel/issues). **Do not post private profiles, reports, contact details, employer-confidential material, or personal career plans there.** Use a minimal fictional or redacted example instead, such as the samples in `examples/`.
- **Security concerns.** Open an issue that describes the concern without sensitive details, and ask for a private channel to share more.

---

# 隱私權說明 — LinkedIn Positioning Panel

[English](#privacy-notice--linkedin-positioning-panel) | 繁體中文

生效日期：2026-11-13。適用於 plugin 版本 0.1.3，以及以 v0.1.2 發布的 Skill 指令。本說明的變更記錄在本儲存庫的歷史中。

LinkedIn Positioning Panel 是只包含指令的 Claude plugin：內含一個 Skill（文字指令），沒有程式碼、hooks、腳本、MCP 伺服器或連接器。作者沒有為它營運任何服務。本 plugin 不隸屬於 LinkedIn，也未獲其背書。

## Plugin 讀取的內容

- **只讀取你為所要求的審查而提供的資料。**Skill 只開啟你在對話中指定、附加或貼上的來源，例如 LinkedIn Profile PDF、貼上的個人檔案文字、截圖或職缺描述。除非你同意，不會開啟同一資料夾中的其他檔案。
- **個人資料。**這些來源通常包含你的個人資料，例如姓名、工作經歷與成就，也可能包含他人的資訊，例如推薦文中的姓名。請只提供你有權分享、且需要審查的內容。
- **主機提供的上下文。**Skill 不會指示 Claude 主動搜尋或擷取 Claude 的記憶、你的對話紀錄或對話摘要，也不會跨工作階段建立關於你的檔案。依你的設定，Claude 應用程式仍可能自行把這類上下文帶入對話；這類上下文由應用程式依你帳號的條款處理，不屬於本 plugin 的處理範圍。

## 內容的處理方式

- **由 Claude 在你的帳號下處理。**你提供的內容會作為對話的一部分由 Claude 處理，依你 Claude 帳號的條款與資料設定辦理。請參閱 [Anthropic 隱私權政策](https://www.anthropic.com/legal/privacy)。
- **代理只在你授權時使用。**如果你明確授權使用個別的審查或事實檢查代理，代理會在同一工作階段中取得授權範圍內的來源與草稿。

## 報告檔案

- **何時寫檔。**環境支援寫檔時，完整審查預設會寫出三份 Markdown 報告，內容包含你的個人檔案與分析。
- **存放位置。**報告寫到你指定的位置；沒有指定時，寫到任何 git 儲存庫以外的私人位置；兩者都不可行時，改在對話中交付。Skill 一律不 stage、commit 或 push 報告。
- **保存期限。**保存期限由主機 Claude 應用程式決定，而不是本 plugin。雲端工作階段或暫存位置中的檔案可能被清除。需要保留的報告請下載或複製，不再需要時請自行刪除。
- **不要寫檔。**如果不希望寫出報告檔，請要求只在對話中呈現（「結果只在對話呈現」）。

## 可選的外部查詢

- **何時查詢。**除非你要求只使用提供的來源，Skill 在你要求查證，或判斷可取得的權威來源會實質影響審查時，可能查核外部資訊。
- **送出的內容。**查詢只透過你的 Claude 應用程式提供的網路搜尋或讀取工具進行，並會把雇主、獎項、證照名稱等搜尋字詞送到這些服務，依各服務自己的條款處理。
- **避免查詢。**請說明「只使用提供的來源，不要上網」。
- **帳號憑證。**Skill 不會要求密碼、Cookie 或工作階段權杖，也不會繞過存取限制。

## 作者會收到什麼

- **不會自動傳送。**本 plugin 沒有後端，不會自動把你的個人檔案、報告或對話傳送給作者。
- **你主動提供的資料。**如果你主動聯絡作者，例如在 GitHub 開 issue，作者會收到你提供的所有內容；公開的 issue 則任何能檢視本儲存庫的人都看得到。請勿附上私人個人檔案、報告或聯絡資訊。
- **上架後的使用統計。**如果本 plugin 在 Anthropic 的 plugin 目錄上架，Anthropic 的開發者入口網站可能向作者顯示使用統計，例如安裝數、版本、Skill 執行次數與錯誤率。統計包含哪些內容，由 Anthropic 決定。

## 支援與問題回報

- **Issues 是公開的。**問題請回報到 [GitHub Issues](https://github.com/jeterchou/linkedin-positioning-panel/issues)。**請勿在其中張貼私人個人檔案、報告、聯絡資訊、雇主機密或個人職涯規劃。**請改用最小的虛構或去識別範例，例如 `examples/` 中的範例。
- **安全疑慮。**請開一個 issue 描述問題，但不要附上敏感細節，並請求以私人管道提供更多資訊。
