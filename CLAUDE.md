# Instagram Reels 制作 — Claude Code 用指示

**クライアントはフォルダを開いて「スタート」だけ。** 記入済みファイルは不要（空でOK）。

API 設定は不要。参考は **テキスト** か **動画ファイル** の2パターン。

| 合図 | 動作 |
|------|------|
| **スタート** | ヒアリング → 記憶 → 分析 → 台本・撮影・編集プラン |
| **編集スタート** | 撮影素材を編集 → 完成動画 |

---

## スタート — 必ずこの順番で実行

### 0. 状態確認

**提案済み**とみなす条件（すべて満たすときだけ）:

- `02_proposal/executive_summary.md` の「結論3行」に **実際の文** が入っている（空欄・「1.」だけは不可）
- `02_proposal/script.md` のフックに **セリフまたはテロップ** が書かれている

上記以外（テンプレートのみ、「未生成」表記、空欄）は **未完了** → ヒアリングから実行。

### 1. ヒアリング（最優先・対話で完結）

`00_brief/client_info.md` が空またはテンプレのみのとき、**いきなり分析しない**。  
丁寧な日本語で、**一度に1〜2問**ずつ聞く。答えを受け取るたびに **即 `client_info.md` に追記保存**（記憶＝ファイルに書く）。

**必ず聞く項目（最低限）**

1. **目的** — この Reels で何を達成したいか  
2. **ターゲット** — 誰に見てほしいか  
3. **NG** — 避けたい表現・映像（なければ「なし」）  
4. **参考** — 次のどれか  
   - B: 動画ファイル（チャット添付 or `00_brief/reference/`）  
   - A: 言葉で説明（後で `reference_text.md` に整理）  
   - URLメモのみ → `instagram_urls.txt` に保存し、「保存した動画を reference/ に入れるか、内容をテキストで」と案内  

**任意で聞く**

- サービス名・業種  
- 自分の Instagram  
- 尺の希望（15秒/30秒）  
- 顔出し可否  

ヒアリング中の生回答は `00_brief/hearing_log.md` にも Q&A 形式で残す。

**ヒアリング完了の条件**

- 目的・ターゲット・NG が `client_info.md` に書かれている  
- 参考が **A または B** で手に入る（動画パス or `reference_text.md` に実質的な内容）

未完了なら次の質問に進み、完了したら「ヒアリング完了。参考を分析します」と伝えて **2. 分析** へ。

### 2. 分析（API 不要）

**パターンA** — `00_brief/reference_text.md`  
**パターンB** — `00_brief/reference/` の動画（`ffprobe` 可能なら尺を記録）  
チャットで届いた動画・テキストは該当ファイルに保存してから分析。

- `01_research/research_rationale.md` — なぜこの参考か、ヒアリング内容との接続  
- `01_research/reference_analysis.md` — 入力ソース（A/B）を明記  
- `01_research/account_analysis.md` — 業界の一般的パターンで補足可  

**使わない**: gemini-gen、Instagram 自動取得、API キー要求。

### 3. 提案（`02_proposal/`）

日本語。撮影だけで済む粒度。

- `executive_summary.md`
- `creative_direction.md`
- `script.md`（秒数付き）
- `shot_list.md`
- `shooting_checklist.md`
- `caption_draft.md`
- `editing_plan.md`（必須）

### 4. 完了

```
ヒアリング内容を client_info.md に保存しました。
提案は 02_proposal/ です。script と shot_list を見て撮影してください。
撮影したら 03_footage/raw/ に入れて「編集スタート」。
```

`README.md` を **撮影待ち** に更新。

---

## 編集スタート（Phase C）

1. `03_footage/raw/` に動画があるか確認。なければ促す  
2. `02_proposal/editing_plan.md` と `script.md` を読む  
3. `05_edit/editor_choice.md` に video-use / Remotion / hybrid と理由  
4. video-use 時は **カット前に戦略を短く確認**  
5. `06_delivery/final_reels_9x16.mp4` + `caption_final.md`  
6. `README.md` を **完了** に更新  

---

## 禁止

- ヒアリング前に提案だけ生成する  
- クライアントに API 設定を求める  
- フォルダ構造の長い説明（`02_proposal/` だけ見ればよいと伝える）  
- スタート完了前に編集  

---

## 参照スキル（あれば・なくても可）

video-use / remotion-best-practices / social-content
