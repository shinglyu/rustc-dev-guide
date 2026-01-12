# 入門指南
<ORIGINAL># Getting Started</ORIGINAL>

感謝你對 Rust 貢獻的興趣！
<ORIGINAL>Thank you for your interest in contributing to Rust!</ORIGINAL>
貢獻的方法很多，我們都十分感謝。
<ORIGINAL>There are many ways to contribute, and we appreciate all of them.</ORIGINAL>

如果這是你第一次參與貢獻，[實作導覽][walkthrough] 章節會帶你走過一次典型流程。
<ORIGINAL>If this is your first time contributing, the [walkthrough] chapter can give you a good example of
how a typical contribution would go.</ORIGINAL>

本文件並非面面俱到；
<ORIGINAL>This documentation is _not_ intended to be comprehensive;</ORIGINAL>
它是一份快速指南，聚焦最常用的資訊。
<ORIGINAL>it is meant to be a quick guide for the most useful things.</ORIGINAL>
若想了解更多，請參考 [如何建置與執行編譯器](building/how-to-build-and-run.md)。
<ORIGINAL>For more information,
see [How to build and run the compiler](building/how-to-build-and-run.md).</ORIGINAL>

[internals]: https://internals.rust-lang.org
[rust-zulip]: https://rust-lang.zulipchat.com
[coc]: https://www.rust-lang.org/policies/code-of-conduct
[walkthrough]: ./walkthrough.md
[Getting Started]: ./getting-started.md
<ORIGINAL>[internals]: https://internals.rust-lang.org
[rust-zulip]: https://rust-lang.zulipchat.com
[coc]: https://www.rust-lang.org/policies/code-of-conduct
[walkthrough]: ./walkthrough.md
[Getting Started]: ./getting-started.md</ORIGINAL>

## 詢問問題
<ORIGINAL>## Asking Questions</ORIGINAL>

如果有疑問，請在 [Rust Zulip 伺服器][rust-zulip] 或 [internals.rust-lang.org][internals] 發文。
<ORIGINAL>If you have questions, please make a post on the [Rust Zulip server][rust-zulip] or
[internals.rust-lang.org][internals].</ORIGINAL>
更多資源可參考官方網站上的 [團隊與工作小組列表][governance] 與 [社群頁面][community]。
<ORIGINAL>See the [list of teams and working groups][governance] and [the Community page][community] on the
official website for more resources.</ORIGINAL>

[governance]: https://www.rust-lang.org/governance
[community]: https://www.rust-lang.org/community
<ORIGINAL>[governance]: https://www.rust-lang.org/governance
[community]: https://www.rust-lang.org/community</ORIGINAL>

提醒：所有貢獻者都應遵守我們的 [行為準則][coc]。
<ORIGINAL>As a reminder, all contributors are expected to follow our [Code of Conduct][coc].</ORIGINAL>

編譯器團隊（`t-compiler`）通常在 Zulip 的 [#t-compiler 頻道][z-t-compiler] 出沒；
<ORIGINAL>The compiler team (or `t-compiler`) usually hangs out in Zulip in</ORIGINAL>
關於編譯器運作的問題可以發在 [#t-compiler/help][z-help]。
<ORIGINAL>[the #t-compiler channel][z-t-compiler];
questions about how the compiler works can go in [#t-compiler/help][z-help].</ORIGINAL>

[z-t-compiler]: https://rust-lang.zulipchat.com/#narrow/channel/131828-t-compiler
[z-help]: https://rust-lang.zulipchat.com/#narrow/channel/182449-t-compiler.2Fhelp
<ORIGINAL>[z-t-compiler]: https://rust-lang.zulipchat.com/#narrow/channel/131828-t-compiler
[z-help]: https://rust-lang.zulipchat.com/#narrow/channel/182449-t-compiler.2Fhelp</ORIGINAL>

**請大方發問！** 很多人會擔心「耽誤專家的時間」，但 `t-compiler` 並不這麼覺得。
<ORIGINAL>**Please ask questions!** A lot of people report feeling that they are "wasting
expert's time", but nobody on `t-compiler` feels this way.</ORIGINAL>
貢獻者對我們而言很重要。
<ORIGINAL>Contributors are important to us.</ORIGINAL>

如果你覺得舒適，盡量使用公開討論，這樣其他人也能看到問答，甚至把答案回饋到本指南。
<ORIGINAL>Also, if you feel comfortable, prefer public topics, as this means others can
see the questions and answers, and perhaps even integrate them back into this guide :)</ORIGINAL>

**小提示**：若你不是母語英語者，對寫作不太放心，可以用翻譯工具幫忙。
<ORIGINAL>**Tip**: If you're not a native English speaker and feel unsure about writing, try using a translator to help.</ORIGINAL>
但請避免用會產生冗長、複雜語句的 LLM 工具。
<ORIGINAL>But avoid using LLM tools that generate long, complex words.</ORIGINAL>
日常合作時，**簡單清楚的用詞** 最容易讓大家理解。
<ORIGINAL>In daily teamwork, **simple and clear words** are best for easy understanding.</ORIGINAL>
即使有些小錯字或語法瑕疵，也能讓人感覺更有人味。
<ORIGINAL>Even small typos or grammar mistakes can make you seem more human, and people connect better with humans.</ORIGINAL>

### 尋找領域專家
<ORIGINAL>### Experts</ORIGINAL>

並非所有 `t-compiler` 成員都熟悉 `rustc` 的每個部分；
<ORIGINAL>Not all `t-compiler` members are experts on all parts of `rustc`;</ORIGINAL>
這是個很大的專案。
<ORIGINAL>it's a pretty large project.</ORIGINAL>
如果想找出特定區域的專家，可以參考 [triagebot 分派群組][map]。
<ORIGINAL>To find out who could have some expertise on
different parts of the compiler, [consult triagebot assign groups][map].</ORIGINAL>
`triagebot.toml` 中所有以 `[assign*` 開頭的區塊即是。
<ORIGINAL>The sections that start with `[assign*` in `triagebot.toml` file.</ORIGINAL>
如果還是不確定該 @ 誰，也儘管發問。
<ORIGINAL>But also, feel free to ask questions even if you can't figure out who to ping.</ORIGINAL>

另一個方法是看看最近有哪些人對該區域提交過 commit。
<ORIGINAL>Another way to find experts for a given part of the compiler is to see who has made recent commits.</ORIGINAL>
例如想找自 1.68.2 版之後處理名稱解析的人，可以執行 `git shortlog -n 1.68.2.. compiler/rustc_resolve/`。
<ORIGINAL>For example, to find people who have recently worked on name resolution since the 1.68.2 release,
you could run `git shortlog -n 1.68.2.. compiler/rustc_resolve/`.</ORIGINAL>
忽略所有以 "Rollup merge" 開頭或作者是 `@bors` 的 commit（這些請參考 [CI 貢獻流程](./contributing.md#ci)）。
<ORIGINAL>Ignore any commits starting with
"Rollup merge" or commits by `@bors` (see [CI contribution procedures](./contributing.md#ci) for
more information about these commits).</ORIGINAL>

[map]: https://github.com/rust-lang/rust/blob/HEAD/triagebot.toml
<ORIGINAL>[map]: https://github.com/rust-lang/rust/blob/HEAD/triagebot.toml</ORIGINAL>

### 提問禮節
<ORIGINAL>### Etiquette</ORIGINAL>

我們希望你在提問時盡量提供有用的資訊，但也理解對新手來說不容易判斷。
<ORIGINAL>We do ask that you be mindful to include as much useful information as you can
in your question, but we recognize this can be hard if you are unfamiliar with contributing to Rust.</ORIGINAL>

只 @ 別人而沒有上下文可能會造成噪音，因此請留意 `t-compiler` 每天會收到不少通知。
<ORIGINAL>Just pinging someone without providing any context can be a bit annoying and
just create noise, so we ask that you be mindful of the fact that the
`t-compiler` folks get a lot of pings in a day.</ORIGINAL>

## 我該做什麼？
<ORIGINAL>## What should I work on?</ORIGINAL>

Rust 專案很大，有時難以判斷哪些部分需要幫忙，或哪些適合新手。
<ORIGINAL>The Rust project is quite large and it can be difficult to know which parts of the project need
help, or are a good starting place for beginners.</ORIGINAL>
以下是一些推薦的起點。
<ORIGINAL>Here are some suggested starting places.</ORIGINAL>

### 簡單或有指導的 issue
<ORIGINAL>### Easy or mentored issues</ORIGINAL>

如果想找入門點，可以先看看這個 [issue 搜尋][help-wanted-search]。
<ORIGINAL>If you're looking for somewhere to start, check out the following [issue
search][help-wanted-search].</ORIGINAL>
各標籤的說明見 [Triage] 小節。
<ORIGINAL>See the [Triage] for an explanation of these labels.</ORIGINAL>
你也可以依興趣篩選，例如：
<ORIGINAL>You can also try filtering the search to areas you're interested in.
For example:</ORIGINAL>

- `repo:rust-lang/rust-clippy` 只看 clippy 的 issue
<ORIGINAL>- `repo:rust-lang/rust-clippy` will only show clippy issues</ORIGINAL>
- `label:T-compiler` 只看與編譯器相關的 issue
<ORIGINAL>- `label:T-compiler` will only show issues related to the compiler</ORIGINAL>
- `label:A-diagnostics` 只看診斷相關的 issue
<ORIGINAL>- `label:A-diagnostics` will only show diagnostic issues</ORIGINAL>

不是所有重要或初階的工作都有標籤，請繼續往下看其他找工作的方式。
<ORIGINAL>Not all important or beginner work has issue labels.
See below for how to find work that isn't labelled.</ORIGINAL>

[help-wanted-search]: https://github.com/issues?q=is%3Aopen%20is%3Aissue%20org%3Arust-lang%20no%3Aassignee%20label%3AE-easy%2CE-medium%2CE-help-wanted%2CE-mentor%20-label%3AS-blocked%20-linked%3Apr
[Triage]: ./contributing.md#issue-triage
<ORIGINAL>[help-wanted-search]: https://github.com/issues?q=is%3Aopen%20is%3Aissue%20org%3Arust-lang%20no%3Aassignee%20label%3AE-easy%2CE-medium%2CE-help-wanted%2CE-mentor%20-label%3AS-blocked%20-linked%3Apr
[Triage]: ./contributing.md#issue-triage</ORIGINAL>

### 重複性工作
<ORIGINAL>### Recurring work</ORIGINAL>

有些工作太大，無法由一人完成。
<ORIGINAL>Some work is too large to be done by a single person.</ORIGINAL>
這類情況通常會有「追蹤 issue」協調貢獻者。
<ORIGINAL>In this case, it's common to have "Tracking issues" to co-ordinate the work between contributors.</ORIGINAL>
以下是一些範例，方便你在小時間投入：
<ORIGINAL>Here are some example tracking issues where
it's easy to pick up work without a large time commitment:</ORIGINAL>

- *請在此加入重複性工作項目。*
<ORIGINAL>- *Add recurring work items here.*</ORIGINAL>

如果找到更多重複性工作，歡迎直接補充！
<ORIGINAL>If you find more recurring work, please feel free to add it here!</ORIGINAL>

### Clippy issue
<ORIGINAL>### Clippy issues</ORIGINAL>

[Clippy] 專案投入許多心力讓貢獻流程對新手友善。
<ORIGINAL>The [Clippy] project has spent a long time making its contribution process as friendly to newcomers
as possible.</ORIGINAL>
可以先從這裡開始，熟悉流程和編譯器內部。
<ORIGINAL>Consider working on it first to get familiar with the process and the compiler internals.</ORIGINAL>

詳情請看 [Clippy 貢獻指南][clippy-contributing]。
<ORIGINAL>See [the Clippy contribution guide][clippy-contributing] for instructions on getting started.</ORIGINAL>

[Clippy]: https://doc.rust-lang.org/clippy/
[clippy-contributing]: https://github.com/rust-lang/rust-clippy/blob/master/CONTRIBUTING.md
<ORIGINAL>[Clippy]: https://doc.rust-lang.org/clippy/
[clippy-contributing]: https://github.com/rust-lang/rust-clippy/blob/master/CONTRIBUTING.md</ORIGINAL>

### 診斷相關的 issue
<ORIGINAL>### Diagnostic issues</ORIGINAL>

許多診斷類的 issue 相對獨立，不需要太多背景知識。
<ORIGINAL>Many diagnostic issues are self-contained and don't need detailed background knowledge of the
compiler.</ORIGINAL>
相關列表在 [這裡][diagnostic-issues]。
<ORIGINAL>You can see a list of diagnostic issues [here][diagnostic-issues].</ORIGINAL>

[diagnostic-issues]: https://github.com/rust-lang/rust/issues?q=is%3Aissue+is%3Aopen+label%3AA-diagnostics+no%3Aassignee
<ORIGINAL>[diagnostic-issues]: https://github.com/rust-lang/rust/issues?q=is%3Aissue+is%3Aopen+label%3AA-diagnostics+no%3Aassignee</ORIGINAL>

### 接手被放棄的 PR
<ORIGINAL>### Picking up abandoned pull requests</ORIGINAL>

有時貢獻者送出 PR 後，因時間或興趣不足而無法繼續。
<ORIGINAL>Sometimes, contributors send a pull request, but later find out that they don't have enough
time to work on it, or they simply are not interested in it anymore.</ORIGINAL>
這些 PR 最終會被關閉並加上 `S-inactive` 標籤。
<ORIGINAL>Such PRs are often eventually closed and they receive the `S-inactive` label.</ORIGINAL>
你可以查看 [清單][abandoned-prs]，嘗試接手。
<ORIGINAL>You could try to examine some of these PRs and pick up the work.
You can find the list of such PRs [here][abandoned-prs].</ORIGINAL>

如果該功能已透過其他方式實作，`S-inactive` 標籤應該會被移除。
<ORIGINAL>If the PR has been implemented in some other way in the meantime, the `S-inactive` label
should be removed from it.</ORIGINAL>
否則且仍有興趣，可將 PR rebase 到最新的 `main`，並送出新的 PR 繼續此工作。
<ORIGINAL>If not, and it seems that there is still interest in the change,
you can try to rebase the pull request on top of the latest `main` branch and send a new
pull request, continuing the work on the feature.</ORIGINAL>

[abandoned-prs]: https://github.com/rust-lang/rust/pulls?q=is%3Apr+label%3AS-inactive+is%3Aclosed
<ORIGINAL>[abandoned-prs]: https://github.com/rust-lang/rust/pulls?q=is%3Apr+label%3AS-inactive+is%3Aclosed</ORIGINAL>

### 撰寫測試
<ORIGINAL>### Writing tests</ORIGINAL>

已修正但缺少回歸測試的 issue 會標註 `E-needs-test`。
<ORIGINAL>Issues that have been resolved but do not have a regression test are marked with the `E-needs-test` label.</ORIGINAL>
撰寫單元測試風險低、優先度相對低，適合新手熟悉測試基礎建設與貢獻流程。
<ORIGINAL>Writing unit tests is a low-risk,
lower-priority task that offers new contributors a great opportunity to familiarize themselves
with the testing infrastructure and contribution workflow.</ORIGINAL>
列表在 [這裡][needs-test-issues]。
<ORIGINAL>You can see a list of needs test issues [here][needs-test-issues].</ORIGINAL>

[needs-test-issues]: https://github.com/rust-lang/rust/issues?q=is%3Aissue%20is%3Aopen%20label%3AE-needs-test%20no%3Aassignee
<ORIGINAL>[needs-test-issues]: https://github.com/rust-lang/rust/issues?q=is%3Aissue%20is%3Aopen%20label%3AE-needs-test%20no%3Aassignee</ORIGINAL>

### 貢獻 std（標準函式庫）
<ORIGINAL>### Contributing to std (standard library)</ORIGINAL>

請參考 [std-dev-guide](https://std-dev-guide.rust-lang.org/)。
<ORIGINAL>See [std-dev-guide](https://std-dev-guide.rust-lang.org/).</ORIGINAL>

### 向其他 Rust 專案貢獻程式碼
<ORIGINAL>### Contributing code to other Rust projects</ORIGINAL>

除了 `rust-lang/rust`，還有許多專案可以貢獻，例如 `cargo`、`miri`、`rustup` 等。
<ORIGINAL>There are a bunch of other projects that you can contribute to outside of the
`rust-lang/rust` repo, including `cargo`, `miri`, `rustup`, and many others.</ORIGINAL>

這些儲存庫可能有自己的貢獻指南與流程。
<ORIGINAL>These repos might have their own contributing guidelines and procedures.</ORIGINAL>
許多由工作小組維護；更多資訊請閱讀各 repo 的 README。
<ORIGINAL>Many of them are owned by working groups.
For more info, see the documentation in those repos' READMEs.</ORIGINAL>

### 其他貢獻方式
<ORIGINAL>### Other ways to contribute</ORIGINAL>

如果不想直接跳進 `rust-lang/rust` 這麼大的程式碼庫，還有許多其他方式：
<ORIGINAL>There are a bunch of other ways you can contribute, especially if you don't
feel comfortable jumping straight into the large `rust-lang/rust` codebase.</ORIGINAL>

- [撰寫文件][wd]：若想挑戰自己，可以閱讀部分原始碼並撰寫文件註解。這不僅幫助你熟悉編譯器，也能留下有用的成果！
<ORIGINAL>- [Writing documentation][wd]: if you are feeling a bit more intrepid, you could try
  to read a part of the code and write doc comments for it.
  This will help you to learn some part of the compiler while also producing a useful artifact!</ORIGINAL>
- [issue 分級][triage]：分類、重現、縮小問題範圍對維護者很有幫助。
<ORIGINAL>- [Triaging issues][triage]: categorizing, replicating, and minimizing issues is very helpful to the Rust maintainers.</ORIGINAL>
- [工作領域][wa]：Rust 有許多不同主題的工作群組。
<ORIGINAL>- [Working areas][wa]: there are a bunch of working areas on a wide variety
  of rust-related things.</ORIGINAL>
- 在 [users.rust-lang.org][users] 或 [Stack Overflow][so] 回答問題。
<ORIGINAL>- Answer questions on [users.rust-lang.org][users], or on [Stack Overflow][so].</ORIGINAL>
- 參與 [RFC 流程](https://github.com/rust-lang/rfcs)。
<ORIGINAL>- Participate in the [RFC process](https://github.com/rust-lang/rfcs).</ORIGINAL>
- 找到一個 [社群想要的函式庫][community-library]，實作並發布到 [Crates.io](http://crates.io)。說來簡單，但價值很高！
<ORIGINAL>- Find a [requested community library][community-library], build it, and publish
  it to [Crates.io](http://crates.io).
  Easier said than done, but very, very valuable!</ORIGINAL>

[users]: https://users.rust-lang.org/
[so]: http://stackoverflow.com/questions/tagged/rust
[community-library]: https://github.com/rust-lang/rfcs/labels/A-community-library
[wd]: ./contributing.md#writing-documentation
[wa]: https://forge.rust-lang.org/compiler/working-areas.html
[triage]: ./contributing.md#issue-triage
<ORIGINAL>[users]: https://users.rust-lang.org/
[so]: http://stackoverflow.com/questions/tagged/rust
[community-library]: https://github.com/rust-lang/rfcs/labels/A-community-library
[wd]: ./contributing.md#writing-documentation
[wa]: https://forge.rust-lang.org/compiler/working-areas.html
[triage]: ./contributing.md#issue-triage</ORIGINAL>

## 取得原始碼並建置
<ORIGINAL>## Cloning and Building</ORIGINAL>

請參考「[如何建置與執行編譯器](./building/how-to-build-and-run.md)」。
<ORIGINAL>See ["How to build and run the compiler"](./building/how-to-build-and-run.md).</ORIGINAL>

## 貢獻流程
<ORIGINAL>## Contributor Procedures</ORIGINAL>

此區內容已移至「[貢獻流程](./contributing.md)」章節。
<ORIGINAL>This section has moved to the ["Contribution Procedures"](./contributing.md) chapter.</ORIGINAL>

## 其他資源
<ORIGINAL>## Other Resources</ORIGINAL>

此區內容已移至「[關於本指南][more-links]」章節。
<ORIGINAL>This section has moved to the ["About this guide"][more-links] chapter.</ORIGINAL>

[more-links]: ./about-this-guide.md#other-places-to-find-information
<ORIGINAL>[more-links]: ./about-this-guide.md#other-places-to-find-information</ORIGINAL>
