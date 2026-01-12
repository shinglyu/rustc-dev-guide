# Appendix T: Terminology (zh-TW)

以英文版 rustc-dev-guide (<https://github.com/shinglyu/rustc-dev-guide.git>) 為基準，彙整本書出現的專有名詞並提供台灣常用譯名。若原文未給出對應中文，則參考台灣社群與官方文件的慣例（避免中國大陸用語）。後續如有新增章節或更新譯名，請同步維護本表。

| English term | Translation (繁體臺灣) | Notes / Source |
| --- | --- | --- |
| rustc | Rust 編譯器（rustc） | 原文章節標題；保留二進位名稱 |
| compiler frontend | 編譯器前端 | rustc-dev-guide 範疇 |
| compiler backend | 編譯器後端 | rustc-dev-guide 範疇 |
| bootstrapping | 自舉（引導編譯） | 來自 Bootstrapping 章節 |
| query system | 查詢系統 | rustc 查詢模型 |
| incremental compilation | 增量編譯 | Incremental compilation 章節 |
| parser | 剖析器 / 解析器 | 語法階段；台灣常用「剖析」 |
| lexer / tokenization | 詞彙分析 / 標記化 | 語法前處理 |
| AST (Abstract Syntax Tree) | 抽象語法樹 | Syntax / AST 章節 |
| AST validation | 抽象語法樹驗證 | rustc 驗證步驟 |
| HIR (High-level IR) | 高階中介表示 | HIR 章節 |
| THIR (Typed HIR) | 型別化高階中介表示 | THIR 章節 |
| MIR (Mid-level IR) | 中階中介表示 | MIR 章節 |
| MIR borrow checker | MIR 借用檢查器 | Borrow check 章節 |
| ownership | 擁有權 | Rust 核心概念 |
| borrow | 借用 | Rust 核心概念 |
| lifetime / region | 生命週期 / 區域 | Region inference 章節 |
| region inference | 生命週期推論 | Borrow check 子章節 |
| trait solver | 特徵求解器 | Trait solving 章節 |
| coherence | 一致性檢查 | Coherence 章節 |
| type inference | 型別推論 | Type inference 章節 |
| normalization | 正規化 | Normalization 章節 |
| monomorphization | 單型化 | Backend monomorph 章節 |
| code generation / codegen | 程式碼生成 | Backend codegen |
| LLVM backend | LLVM 後端 | Backend updating/debugging 章節 |
| const evaluation | 常數求值 | Const-eval 章節 |
| sanitizer | 偵錯強化器（Sanitizer） | Sanitizers 章節；保留英名 |
| profile-guided optimization (PGO) | 剖析導向最佳化 | PGO 章節 |
| debuginfo | 除錯資訊 | Debug Info 章節 |
| rustdoc | rustdoc 文件工具 | Rust 官方工具名保留 |
| Clippy | Clippy 靜態檢查器 | 官方工具名保留 |
| diagnostic | 診斷訊息 | Diagnostics 章節 |
| lint | 靜態檢查（lint） | Diagnostics / lintstore |
| error code | 錯誤代碼 | Error codes 子章節 |
| feature gate | 功能閘 / 特性開關 | Feature gates 章節 |
| unstable feature | 不穩定功能 | 稳定流程相關 |
| bootstrap feature cfg(bootstrap) | 自舉功能旗標 | cfg(bootstrap) 章節 |
| target triple | 平台三元組 | 新增目標章節 |
| codegen unit | 生成單元 | Backend codegen 章節 |
| crate | crate 套件（crate） | Rust 術語；保留英文音譯 |
| module | 模組 | 語法章節 |
| attribute | 屬性（attribute） | Attributes 章節 |
| macro expansion | 巨集展開 | Macro expansion 章節 |
| name resolution | 名稱解析 | Name resolution 章節 |
| inline assembly | 行內組合語言 | asm 章節 |
| lintstore | lint 儲存庫 | Diagnostics / lintstore |
| rustc driver | rustc_driver（驅動程式） | rustc-driver 章節 |
| rustc interface | rustc_interface（介面層） | rustc-interface 章節 |
| query cache | 查詢快取 | Query evaluation 模型 |
| salsa | Salsa 查詢框架 | Queries / salsa 章節 |
| borrow checker two-phase borrows | 兩階段借用 | Borrow check 子章節 |
| const generics | 常數泛型 | Const-generics 章節 |
| implicit caller location | 隱含呼叫端位址 | Backend / implicit-caller-location |
| rust-analyzer | rust-analyzer 分析器 | 工具名保留 |
| Zulip | Zulip 聊天服務 | 社群資源 |
| triagebot | triagebot 自動分派機器人 | triagebot 章節 |
| @bors | bors 合併機器人 | 社群流程 |

> 註：若需新增或修正譯名，請在 PR 中說明資訊來源（如 rustc-dev-guide 原文章節、官方部落格、台灣社群文章或教學），以維持一致性。
