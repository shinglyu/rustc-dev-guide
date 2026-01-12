# 關於本指南

本指南旨在說明 Rust 編譯器 rustc 的運作方式，並協助新貢獻者參與 rustc 的開發。

本書分成數個部分：

1. [建置與除錯 `rustc`][p1]：不論你想怎麼貢獻，都會用到的資訊，涵蓋建置、除錯、效能分析等。
1. [對 Rust 的貢獻][p2]：同樣適用於所有貢獻者，內容包含貢獻流程、git 與 GitHub 的使用、功能穩定化等。
1. [自舉流程][p3]：介紹 Rust 編譯器如何利用先前版本建構自己，並說明自舉流程與除錯方法。
1. [編譯器高階架構][p4]：討論編譯器的高階架構與各個編譯階段。
1. [原始碼表示法][p5]：描述將使用者原始碼轉換為編譯器可處理的各種表示形式的過程。
1. [支援基礎設施][p6]：涵蓋命令列參數慣例、rustc_driver 與 rustc_interface 等進入點，以及錯誤與 lint 的設計與實作。
1. [程式分析][p7]：討論編譯器用來檢查程式各種性質的分析（例如型別檢查），以及如何支援後續步驟。
1. [從 MIR 到二進位檔][p8]：說明如何產生連結後的可執行機器碼。
1. [附錄][p9]：收錄各種參考資料，其中包含一份詞彙表。

[p1]: ./building/how-to-build-and-run.html
[p2]: ./contributing.md
[p3]: ./building/bootstrapping/intro.md
[p4]: ./part-2-intro.md
[p5]: ./part-3-intro.md
[p6]: ./cli.md
[p7]: ./part-4-intro.md
[p8]: ./part-5-intro.md
[p9]: ./appendix/background.md

### 時時變動

請記得，`rustc` 是一個實際運作的產品，有一群貢獻者持續開發。
因此程式碼會不斷變動，也難免有技術債。
此外，指南中談到的許多構想是理想化的設計，尚未完全落實。
以上都讓本指南不容易時時保持完全最新！

本指南也是開源的，原始碼放在 [GitHub 儲存庫]。
若發現內容有誤，請提出 issue，或更好的是直接送出修正 PR！

如果你打算貢獻本指南，請參考[本指南關於撰寫文件的子章節]。

[subsection on writing documentation in this guide]: contributing.md#contributing-to-rustc-dev-guide

> 「諸行無常」，觀之以慧，離苦得樂。
> ——《法句經》偈 277

## 其他資訊來源

你現在閱讀的本指南，介紹編譯器各部分如何運作，以及如何貢獻編譯器。

你可能還會需要以下網站：

- [rustc API 文件]：編譯器、開發工具與內部工具的 rustdoc 文件
- [Forge]：描述 Rust 基礎設施、團隊流程等
- [compiler-team]：編譯器團隊的主站，包含流程、活躍工作小組與團隊行事曆
- [std-dev-guide]：標準函式庫開發指南
- [rust-analyzer book]：rust-analyzer 的文件
- [t-compiler Zulip][z]
- [Rust Internals 論壇][rif]：討論與提問的地方
- [Rust 參考手冊][rr]：雖未聚焦編譯器內部，但仍是極佳的資料來源
- 雖然已過時，[Tom Lee 的文章][tlgba] 仍很有幫助
- [Rust Compiler Testing Docs][rctd]
- 對於 [@bors]，可參考[這張小抄][cheatsheet]
- Google 仍是最好的朋友。你可以[搜尋所有 Rust 文件][gsearchdocs]（標準函式庫、編譯器、書籍、參考手冊與指南），快速找到想要的資訊。
- Rustdoc 內建的搜尋也很好用，可以在關注的 crate 中搜尋型別與函式，也可以用型別簽章搜尋！
  例如搜尋 `* -> vec` 可以找到所有回傳 `Vec<T>` 的函式。
  **提示：** 在任何 Rustdoc 頁面按 `?` 可以查看更多技巧與快捷鍵。


[rustc dev guide]: about-this-guide.md
[gsearchdocs]: https://www.google.com/search?q=site:doc.rust-lang.org+your+query+here
[stddocs]: https://doc.rust-lang.org/std
[rif]: http://internals.rust-lang.org
[rr]: https://doc.rust-lang.org/book/
[rustforge]: https://forge.rust-lang.org/
[tlgba]: https://tomlee.co/2014/04/a-more-detailed-tour-of-the-rust-compiler/
[ro]: https://www.rustaceans.org/
[rctd]: tests/intro.md
[cheatsheet]: https://bors.rust-lang.org/
[Miri]: https://github.com/rust-lang/miri
[@bors]: https://github.com/bors
[a GitHub repository]: https://github.com/rust-lang/rustc-dev-guide/
[rustc API docs]: https://doc.rust-lang.org/nightly/nightly-rustc/rustc_middle
[Forge]: https://forge.rust-lang.org/
[compiler-team]: https://github.com/rust-lang/compiler-team/
[std-dev-guide]: https://std-dev-guide.rust-lang.org/
[rust-analyzer book]: https://rust-analyzer.github.io/book/
[z]: https://rust-lang.zulipchat.com/#narrow/stream/131828-t-compiler# About this guide

This guide is meant to help document how rustc – the Rust compiler – works,
as well as to help new contributors get involved in rustc development.

There are several parts to this guide:

1. [Building and debugging `rustc`][p1]:
   Contains information that should be useful no matter how you are contributing,
   about building, debugging, profiling, etc.
1. [Contributing to Rust][p2]:
   Contains information that should be useful no matter how you are contributing,
   about procedures for contribution, using git and Github, stabilizing features, etc.
1. [Bootstrapping][p3]:
   Describes how the Rust compiler builds itself using previous versions, including
   an introduction to the bootstrap process and debugging methods.
1. [High-level Compiler Architecture][p4]:
   Discusses the high-level architecture of the compiler and stages of the compile process.
1. [Source Code Representation][p5]:
   Describes the process of taking raw source code from the user
   and transforming it into various forms that the compiler can work with easily.
1. [Supporting Infrastructure][p6]:
   Covers command-line argument conventions, compiler entry points like rustc_driver and
   rustc_interface, and the design and implementation of errors and lints.
1. [Analysis][p7]:
   Discusses the analyses that the compiler uses to check various properties of the code
   and inform later stages of the compile process (e.g., type checking).
1. [MIR to Binaries][p8]: How linked executable machine code is generated.
1. [Appendices][p9] at the end with useful reference information.
   There are a few of these with different information, including a glossary.

[p1]: ./building/how-to-build-and-run.html
[p2]: ./contributing.md
[p3]: ./building/bootstrapping/intro.md
[p4]: ./part-2-intro.md
[p5]: ./part-3-intro.md
[p6]: ./cli.md
[p7]: ./part-4-intro.md
[p8]: ./part-5-intro.md
[p9]: ./appendix/background.md

### Constant change

Keep in mind that `rustc` is a real production-quality product,
being worked upon continuously by a sizeable set of contributors.
As such, it has its fair share of codebase churn and technical debt.
In addition, many of the ideas discussed throughout this guide are idealized designs
that are not fully realized yet.
All this makes keeping this guide completely up to date on everything very hard!

The guide itself is of course open source as well,
and the sources are hosted on [a GitHub repository].
If you find any mistakes in the guide, please file an issue.
Even better, open a PR with a correction!

If you do contribute to the guide,
please see the corresponding [subsection on writing documentation in this guide].

[subsection on writing documentation in this guide]: contributing.md#contributing-to-rustc-dev-guide

> “‘All conditioned things are impermanent’ —
> when one sees this with wisdom, one turns away from suffering.”
> _The Dhammapada, verse 277_

## Other places to find information

This guide, the one you are currently reading,
contains information about how various parts of the compiler work,
and how to contribute to the compiler.

You might also find the following sites useful:

- [rustc API docs] -- rustdoc documentation for the compiler, devtools, and internal tools
- [Forge] -- contains documentation about Rust infrastructure, team procedures, and more
- [compiler-team] -- the home-base for the Rust compiler team, with description
  of the team procedures, active working groups, and the team calendar.
- [std-dev-guide] -- a similar guide for developing the standard library.
- [rust-analyzer book] -- documentation for the rust-analyzer.
- [The t-compiler Zulip][z]
- The [Rust Internals forum][rif], a place to ask questions and discuss Rust's internals
- The [Rust reference][rr], even though it doesn't specifically talk about
  Rust's internals, is a great resource nonetheless
- Although out of date, [Tom Lee's great blog article][tlgba] is very helpful
- The [Rust Compiler Testing Docs][rctd]
- For [@bors], [this cheat sheet][cheatsheet] is helpful
- Google is always helpful when programming.
  You can [search all Rust documentation][gsearchdocs] (the standard library,
  the compiler, the books, the references, and the guides) to quickly find
  information about the language and compiler.
- You can also use Rustdoc's built-in search feature to find documentation on
  types and functions within the crates you're looking at.
  You can also search by type signature!
  For example, searching for `* -> vec` should find all functions that return a `Vec<T>`.
  _Hint:_ Find more tips and keyboard shortcuts by typing `?` on any Rustdoc page!


[rustc dev guide]: about-this-guide.md
[gsearchdocs]: https://www.google.com/search?q=site:doc.rust-lang.org+your+query+here
[stddocs]: https://doc.rust-lang.org/std
[rif]: http://internals.rust-lang.org
[rr]: https://doc.rust-lang.org/book/
[rustforge]: https://forge.rust-lang.org/
[tlgba]: https://tomlee.co/2014/04/a-more-detailed-tour-of-the-rust-compiler/
[ro]: https://www.rustaceans.org/
[rctd]: tests/intro.md
[cheatsheet]: https://bors.rust-lang.org/
[Miri]: https://github.com/rust-lang/miri
[@bors]: https://github.com/bors
[a GitHub repository]: https://github.com/rust-lang/rustc-dev-guide/
[rustc API docs]: https://doc.rust-lang.org/nightly/nightly-rustc/rustc_middle
[Forge]: https://forge.rust-lang.org/
[compiler-team]: https://github.com/rust-lang/compiler-team/
[std-dev-guide]: https://std-dev-guide.rust-lang.org/
[rust-analyzer book]: https://rust-analyzer.github.io/book/
[z]: https://rust-lang.zulipchat.com/#narrow/stream/131828-t-compiler
