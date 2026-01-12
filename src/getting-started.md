# 入門指南

感謝你對 Rust 貢獻的興趣！
貢獻的方法很多，我們都十分感謝。

如果這是你第一次參與貢獻，[實作導覽][walkthrough] 章節會帶你走過一次典型流程。

本文件並非面面俱到；
它是一份快速指南，聚焦最常用的資訊。
若想了解更多，請參考 [如何建置與執行編譯器](building/how-to-build-and-run.md)。

[internals]: https://internals.rust-lang.org
[rust-zulip]: https://rust-lang.zulipchat.com
[coc]: https://www.rust-lang.org/policies/code-of-conduct
[walkthrough]: ./walkthrough.md
[Getting Started]: ./getting-started.md

## 詢問問題

如果有疑問，請在 [Rust Zulip 伺服器][rust-zulip] 或 [internals.rust-lang.org][internals] 發文。
更多資源可參考官方網站上的 [團隊與工作小組列表][governance] 與 [社群頁面][community]。

[governance]: https://www.rust-lang.org/governance
[community]: https://www.rust-lang.org/community

提醒：所有貢獻者都應遵守我們的 [行為準則][coc]。

編譯器團隊（`t-compiler`）通常在 Zulip 的 [#t-compiler 頻道][z-t-compiler] 出沒；
關於編譯器運作的問題可以發在 [#t-compiler/help][z-help]。

[z-t-compiler]: https://rust-lang.zulipchat.com/#narrow/channel/131828-t-compiler
[z-help]: https://rust-lang.zulipchat.com/#narrow/channel/182449-t-compiler.2Fhelp

**請大方發問！** 很多人會擔心「耽誤專家的時間」，但 `t-compiler` 並不這麼覺得。
貢獻者對我們而言很重要。

如果你覺得舒適，盡量使用公開討論，這樣其他人也能看到問答，甚至把答案回饋到本指南。

**小提示**：若你不是母語英語者，對寫作不太放心，可以用翻譯工具幫忙。
但請避免用會產生冗長、複雜語句的 LLM 工具。
日常合作時，**簡單清楚的用詞** 最容易讓大家理解。
即使有些小錯字或語法瑕疵，也能讓人感覺更有人味。

### 尋找領域專家

並非所有 `t-compiler` 成員都熟悉 `rustc` 的每個部分；
這是個很大的專案。
如果想找出特定區域的專家，可以參考 [triagebot 分派群組][map]。
`triagebot.toml` 中所有以 `[assign*` 開頭的區塊即是。
如果還是不確定該 @ 誰，也儘管發問。

另一個方法是看看最近有哪些人對該區域提交過 commit。
例如想找自 1.68.2 版之後處理名稱解析的人，可以執行 `git shortlog -n 1.68.2.. compiler/rustc_resolve/`。
忽略所有以 "Rollup merge" 開頭或作者是 `@bors` 的 commit（這些請參考 [CI 貢獻流程](./contributing.md#ci)）。

[map]: https://github.com/rust-lang/rust/blob/HEAD/triagebot.toml

### 提問禮節

我們希望你在提問時盡量提供有用的資訊，但也理解對新手來說不容易判斷。

只 @ 別人而沒有上下文可能會造成噪音，因此請留意 `t-compiler` 每天會收到不少通知。

## 我該做什麼？

Rust 專案很大，有時難以判斷哪些部分需要幫忙，或哪些適合新手。
以下是一些推薦的起點。

### 簡單或有指導的 issue

如果想找入門點，可以先看看這個 [issue 搜尋][help-wanted-search]。
各標籤的說明見 [Triage] 小節。
你也可以依興趣篩選，例如：

- `repo:rust-lang/rust-clippy` 只看 clippy 的 issue
- `label:T-compiler` 只看與編譯器相關的 issue
- `label:A-diagnostics` 只看診斷相關的 issue

不是所有重要或初階的工作都有標籤，請繼續往下看其他找工作的方式。

[help-wanted-search]: https://github.com/issues?q=is%3Aopen%20is%3Aissue%20org%3Arust-lang%20no%3Aassignee%20label%3AE-easy%2CE-medium%2CE-help-wanted%2CE-mentor%20-label%3AS-blocked%20-linked%3Apr
[Triage]: ./contributing.md#issue-triage

### 重複性工作

有些工作太大，無法由一人完成。
這類情況通常會有「追蹤 issue」協調貢獻者。
以下是一些範例，方便你在小時間投入：

- *請在此加入重複性工作項目。*

如果找到更多重複性工作，歡迎直接補充！

### Clippy issue

[Clippy] 專案投入許多心力讓貢獻流程對新手友善。
可以先從這裡開始，熟悉流程和編譯器內部。

詳情請看 [Clippy 貢獻指南][clippy-contributing]。

[Clippy]: https://doc.rust-lang.org/clippy/
[clippy-contributing]: https://github.com/rust-lang/rust-clippy/blob/master/CONTRIBUTING.md

### 診斷相關的 issue

許多診斷類的 issue 相對獨立，不需要太多背景知識。
相關列表在 [這裡][diagnostic-issues]。

[diagnostic-issues]: https://github.com/rust-lang/rust/issues?q=is%3Aissue+is%3Aopen+label%3AA-diagnostics+no%3Aassignee

### 接手被放棄的 PR

有時貢獻者送出 PR 後，因時間或興趣不足而無法繼續。
這些 PR 最終會被關閉並加上 `S-inactive` 標籤。
你可以查看 [清單][abandoned-prs]，嘗試接手。

如果該功能已透過其他方式實作，`S-inactive` 標籤應該會被移除。
否則且仍有興趣，可將 PR rebase 到最新的 `main`，並送出新的 PR 繼續此工作。

[abandoned-prs]: https://github.com/rust-lang/rust/pulls?q=is%3Apr+label%3AS-inactive+is%3Aclosed

### 撰寫測試

已修正但缺少回歸測試的 issue 會標註 `E-needs-test`。
撰寫單元測試風險低、優先度相對低，適合新手熟悉測試基礎建設與貢獻流程。
列表在 [這裡][needs-test-issues]。

[needs-test-issues]: https://github.com/rust-lang/rust/issues?q=is%3Aissue%20is%3Aopen%20label%3AE-needs-test%20no%3Aassignee

### 貢獻 std（標準函式庫）

請參考 [std-dev-guide](https://std-dev-guide.rust-lang.org/)。

### 向其他 Rust 專案貢獻程式碼

除了 `rust-lang/rust`，還有許多專案可以貢獻，例如 `cargo`、`miri`、`rustup` 等。

這些儲存庫可能有自己的貢獻指南與流程。
許多由工作小組維護；更多資訊請閱讀各 repo 的 README。

### 其他貢獻方式

如果不想直接跳進 `rust-lang/rust` 這麼大的程式碼庫，還有許多其他方式：

- [撰寫文件][wd]：若想挑戰自己，可以閱讀部分原始碼並撰寫文件註解。這不僅幫助你熟悉編譯器，也能留下有用的成果！
- [issue 分級][triage]：分類、重現、縮小問題範圍對維護者很有幫助。
- [工作領域][wa]：Rust 有許多不同主題的工作群組。
- 在 [users.rust-lang.org][users] 或 [Stack Overflow][so] 回答問題。
- 參與 [RFC 流程](https://github.com/rust-lang/rfcs)。
- 找到一個 [社群想要的函式庫][community-library]，實作並發布到 [Crates.io](http://crates.io)。說來簡單，但價值很高！

[users]: https://users.rust-lang.org/
[so]: http://stackoverflow.com/questions/tagged/rust
[community-library]: https://github.com/rust-lang/rfcs/labels/A-community-library
[wd]: ./contributing.md#writing-documentation
[wa]: https://forge.rust-lang.org/compiler/working-areas.html
[triage]: ./contributing.md#issue-triage

## 取得原始碼並建置

請參考「[如何建置與執行編譯器](./building/how-to-build-and-run.md)」。

## 貢獻流程

此區內容已移至「[貢獻流程](./contributing.md)」章節。

## 其他資源

此區內容已移至「[關於本指南][more-links]」章節。

[more-links]: ./about-this-guide.md#other-places-to-find-information# Getting Started

Thank you for your interest in contributing to Rust!
There are many ways to contribute, and we appreciate all of them.

If this is your first time contributing, the [walkthrough] chapter can give you a good example of
how a typical contribution would go.

This documentation is _not_ intended to be comprehensive;
it is meant to be a quick guide for the most useful things.
For more information,
see [How to build and run the compiler](building/how-to-build-and-run.md).

[internals]: https://internals.rust-lang.org
[rust-zulip]: https://rust-lang.zulipchat.com
[coc]: https://www.rust-lang.org/policies/code-of-conduct
[walkthrough]: ./walkthrough.md
[Getting Started]: ./getting-started.md

## Asking Questions

If you have questions, please make a post on the [Rust Zulip server][rust-zulip] or
[internals.rust-lang.org][internals].
See the [list of teams and working groups][governance] and [the Community page][community] on the
official website for more resources.

[governance]: https://www.rust-lang.org/governance
[community]: https://www.rust-lang.org/community

As a reminder, all contributors are expected to follow our [Code of Conduct][coc].

The compiler team (or `t-compiler`) usually hangs out in Zulip in
[the #t-compiler channel][z-t-compiler];
questions about how the compiler works can go in [#t-compiler/help][z-help].

[z-t-compiler]: https://rust-lang.zulipchat.com/#narrow/channel/131828-t-compiler
[z-help]: https://rust-lang.zulipchat.com/#narrow/channel/182449-t-compiler.2Fhelp

**Please ask questions!** A lot of people report feeling that they are "wasting
expert's time", but nobody on `t-compiler` feels this way.
Contributors are important to us.

Also, if you feel comfortable, prefer public topics, as this means others can
see the questions and answers, and perhaps even integrate them back into this guide :)

**Tip**: If you're not a native English speaker and feel unsure about writing, try using a translator to help.
But avoid using LLM tools that generate long, complex words.
In daily teamwork, **simple and clear words** are best for easy understanding.
Even small typos or grammar mistakes can make you seem more human, and people connect better with humans.

### Experts

Not all `t-compiler` members are experts on all parts of `rustc`;
it's a pretty large project.
To find out who could have some expertise on
different parts of the compiler, [consult triagebot assign groups][map].
The sections that start with `[assign*` in `triagebot.toml` file.
But also, feel free to ask questions even if you can't figure out who to ping.

Another way to find experts for a given part of the compiler is to see who has made recent commits.
For example, to find people who have recently worked on name resolution since the 1.68.2 release,
you could run `git shortlog -n 1.68.2.. compiler/rustc_resolve/`.
Ignore any commits starting with
"Rollup merge" or commits by `@bors` (see [CI contribution procedures](./contributing.md#ci) for
more information about these commits).

[map]: https://github.com/rust-lang/rust/blob/HEAD/triagebot.toml

### Etiquette

We do ask that you be mindful to include as much useful information as you can
in your question, but we recognize this can be hard if you are unfamiliar with contributing to Rust.

Just pinging someone without providing any context can be a bit annoying and
just create noise, so we ask that you be mindful of the fact that the
`t-compiler` folks get a lot of pings in a day.

## What should I work on?

The Rust project is quite large and it can be difficult to know which parts of the project need
help, or are a good starting place for beginners.
Here are some suggested starting places.

### Easy or mentored issues

If you're looking for somewhere to start, check out the following [issue
search][help-wanted-search].
See the [Triage] for an explanation of these labels.
You can also try filtering the search to areas you're interested in.
For example:

- `repo:rust-lang/rust-clippy` will only show clippy issues
- `label:T-compiler` will only show issues related to the compiler
- `label:A-diagnostics` will only show diagnostic issues

Not all important or beginner work has issue labels.
See below for how to find work that isn't labelled.

[help-wanted-search]: https://github.com/issues?q=is%3Aopen%20is%3Aissue%20org%3Arust-lang%20no%3Aassignee%20label%3AE-easy%2CE-medium%2CE-help-wanted%2CE-mentor%20-label%3AS-blocked%20-linked%3Apr
[Triage]: ./contributing.md#issue-triage

### Recurring work

Some work is too large to be done by a single person.
In this case, it's common to have "Tracking issues" to co-ordinate the work between contributors.
Here are some example tracking issues where
it's easy to pick up work without a large time commitment:

- *Add recurring work items here.*

If you find more recurring work, please feel free to add it here!

### Clippy issues

The [Clippy] project has spent a long time making its contribution process as friendly to newcomers
as possible.
Consider working on it first to get familiar with the process and the compiler internals.

See [the Clippy contribution guide][clippy-contributing] for instructions on getting started.

[Clippy]: https://doc.rust-lang.org/clippy/
[clippy-contributing]: https://github.com/rust-lang/rust-clippy/blob/master/CONTRIBUTING.md

### Diagnostic issues

Many diagnostic issues are self-contained and don't need detailed background knowledge of the
compiler.
You can see a list of diagnostic issues [here][diagnostic-issues].

[diagnostic-issues]: https://github.com/rust-lang/rust/issues?q=is%3Aissue+is%3Aopen+label%3AA-diagnostics+no%3Aassignee

### Picking up abandoned pull requests

Sometimes, contributors send a pull request, but later find out that they don't have enough
time to work on it, or they simply are not interested in it anymore.
Such PRs are often eventually closed and they receive the `S-inactive` label.
You could try to examine some of these PRs and pick up the work.
You can find the list of such PRs [here][abandoned-prs].

If the PR has been implemented in some other way in the meantime, the `S-inactive` label
should be removed from it.
If not, and it seems that there is still interest in the change,
you can try to rebase the pull request on top of the latest `main` branch and send a new
pull request, continuing the work on the feature.

[abandoned-prs]: https://github.com/rust-lang/rust/pulls?q=is%3Apr+label%3AS-inactive+is%3Aclosed

### Writing tests

Issues that have been resolved but do not have a regression test are marked with the `E-needs-test` label.
Writing unit tests is a low-risk,
lower-priority task that offers new contributors a great opportunity to familiarize themselves
with the testing infrastructure and contribution workflow.
You can see a list of needs test issues [here][needs-test-issues].

[needs-test-issues]: https://github.com/rust-lang/rust/issues?q=is%3Aissue%20is%3Aopen%20label%3AE-needs-test%20no%3Aassignee

### Contributing to std (standard library)

See [std-dev-guide](https://std-dev-guide.rust-lang.org/).

### Contributing code to other Rust projects

There are a bunch of other projects that you can contribute to outside of the
`rust-lang/rust` repo, including `cargo`, `miri`, `rustup`, and many others.

These repos might have their own contributing guidelines and procedures.
Many of them are owned by working groups.
For more info, see the documentation in those repos' READMEs.

### Other ways to contribute

There are a bunch of other ways you can contribute, especially if you don't
feel comfortable jumping straight into the large `rust-lang/rust` codebase.

The following tasks are doable without much background knowledge but are incredibly helpful:

- [Writing documentation][wd]: if you are feeling a bit more intrepid, you could try
  to read a part of the code and write doc comments for it.
  This will help you to learn some part of the compiler while also producing a useful artifact!
- [Triaging issues][triage]: categorizing, replicating, and minimizing issues is very helpful to the Rust maintainers.
- [Working areas][wa]: there are a bunch of working areas on a wide variety
  of rust-related things.
- Answer questions on [users.rust-lang.org][users], or on [Stack Overflow][so].
- Participate in the [RFC process](https://github.com/rust-lang/rfcs).
- Find a [requested community library][community-library], build it, and publish
  it to [Crates.io](http://crates.io).
  Easier said than done, but very, very valuable!

[users]: https://users.rust-lang.org/
[so]: http://stackoverflow.com/questions/tagged/rust
[community-library]: https://github.com/rust-lang/rfcs/labels/A-community-library
[wd]: ./contributing.md#writing-documentation
[wa]: https://forge.rust-lang.org/compiler/working-areas.html
[triage]: ./contributing.md#issue-triage

## Cloning and Building

See ["How to build and run the compiler"](./building/how-to-build-and-run.md).

## Contributor Procedures

This section has moved to the ["Contribution Procedures"](./contributing.md) chapter.

## Other Resources

This section has moved to the ["About this guide"][more-links] chapter.

[more-links]: ./about-this-guide.md#other-places-to-find-information
