# Claude用指示：StudioJinsei docs リポジトリ運用ルール

このファイルは、Claude Code がこのリポジトリで作業する際の運用ルールを記載しています。

---

## 📁 このリポジトリについて

**StudioJinsei の経営・事業に関するドキュメント管理リポジトリ**

- 経営判断・事業方針の記録
- フェーズごとのTODO管理
- 運用マニュアル・ガイドライン

---

## 🎯 フェーズ管理の運用方針（重要）

### 基本構成：3ディレクトリ運用

```
docs/
├── [現在のフェーズ]/      # 今やっていること
├── [次のフェーズ]/         # 次にやること（準備中・任意）
├── past-phases/           # 過去のフェーズ（アーカイブ）
└── manuals/               # 常に最新の運用ルール
```

### フェーズの移行手順

#### 1. 現在のフェーズが完了したら
- 現在のディレクトリを `past-phases/` に移動
- ディレクトリ名に完了日を追記
  - 例：`opening-preparation/` → `past-phases/opening-preparation-2025-03/`
- **Claude への指示：ユーザーが「フェーズ完了」と言ったら、このルールに従って移動を実行してください**

#### 2. 次のフェーズを開始
- 新しいディレクトリを作成
  - 例：`business-expansion/`（事業拡大フェーズ）
- 新しいフェーズのREADME・TODOを作成
- `docs/README.md` の「現在のフェーズ」セクションを更新
- **Claude への指示：新フェーズ開始時は、既存フェーズの構造を参考に同様の構成で作成してください**

#### 3. マニュアルは常に更新
- `manuals/` は過去フェーズに移動しない
- 常に最新の運用ルールを反映
- 古いルールは履歴として残す（更新日を記載）

---

## 📂 ディレクトリ命名規則

### フェーズディレクトリ
- `[フェーズ名]-[期間]` 形式
- 英語・小文字・ハイフン区切り
- 例：
  - `opening-preparation` - 開業準備
  - `business-expansion` - 事業拡大
  - `incorporation` - 法人化
  - `early-stage-operation` - 初期事業運営

### アーカイブ
- 完了時に `past-phases/[元のディレクトリ名]-YYYY-MM/` へ移動
- 例：`past-phases/opening-preparation-2025-03/`

---

## 📝 ドキュメント作成ガイドライン

### 新しいドキュメントを作る際の必須事項

1. **必ず関連資料へのリンクを設置**
   - 他のフェーズ、マニュアルへのリンク
   - 親ディレクトリのREADMEへの戻るリンク
   ```markdown
   📂 [開業準備ロードマップに戻る](./README.md)
   ```

2. **更新日を記載**
   ```markdown
   **作成日：YYYY/MM/DD**
   または
   **最終更新：YYYY/MM/DD**
   ```

3. **Markdown形式で統一**
   - 見出しレベルを適切に使う
   - リストやテーブルを活用
   - 絵文字は控えめに（見出しのみ）

4. **各TODOファイルの最後に関連資料リンクセクションを追加**
   ```markdown
   ## 🔗 関連資料

   ### 事業計画
   - [事業目標・売上計画（お金稼ぐ計画）](./business-goals.md)
   - [資金調達計画（お金借りる計画）](./funding-plan.md)

   ### マニュアル・運用
   - [事業用お金管理・運用計画](../manuals/business-finance-plan.md)
   - [GitHub運用方針](../manuals/github-workflow.md)

   ### その他フェーズ
   - [フェーズ1：12月TODO](./phase1-december.md)
   - [フェーズ2：1月TODO](./phase2-january.md)
   ```

---

## 🔐 セキュリティ・機密情報管理

### docsリポジトリ（このディレクトリ）
- ✅ 経営判断・事業方針など
- ✅ 一般的な計画レベルの内容
- ❌ 具体的な金額・機密情報は含まない
- Privateリポジトリで管理

### financial-recordsリポジトリ
- 会計・経理の実データ
- 領収書・請求書のスキャンデータ
- `.gitignore`で機密ファイルを除外

**Claude への指示：具体的な金額や機密情報を含むドキュメントを作成する場合は、ユーザーに確認してください**

---

## 🔄 GitHub運用方針

### コミット方針
- このリポジトリは「経営判断・会社方針」を扱う
- 原則として `main` ブランチへ直接コミット可
- レビューは必須としない（スピード優先）
- コミットメッセージは明確に（何を決定したか）

### コミットメッセージ例
```
Add: 2025年3月の資金調達方針を決定
Update: フェーズ1のTODOに進捗を反映
Decision: PayPay銀行を事業用口座として決定
```

詳細は `manuals/github-workflow.md` を参照

---

## 💡 運用のコツ（Claudeへの指示）

### 1. TODOの更新
- ユーザーが「〇〇を完了した」と言ったら、該当TODOにチェックを入れる
- 完了日を記載する（例：`- [x] 開業届提出（2025/12/13完了）`）

### 2. フェーズ構成の踏襲
- 新しいフェーズを作る際は、`opening-preparation/` の構成を参考にする
- 同様のファイル構成（README, phase1/2/3, business-goals, funding-plan等）

### 3. リンクの一貫性
- すべてのファイルが相互にリンクされている状態を維持
- 新ファイル作成時は必ず親READMEにリンクを追加

### 4. 日付の形式
- `YYYY/MM/DD` 形式で統一（例：2025/12/14）
- 曜日を入れる場合は `(土)` のように括弧で

---

## 🔍 よくある作業パターン

### パターン1：TODOの進捗更新
```markdown
ユーザー：「開業届出してきた」
↓
Claude：phase1-december.md を開いて該当項目にチェック
- [x] 開業届提出（2025/12/13完了）
```

### パターン2：新しいドキュメント追加
```markdown
ユーザー：「サービス料金表を作りたい」
↓
Claude：
1. 適切なフェーズディレクトリに作成
2. 親READMEにリンク追加
3. 関連資料リンクセクションを追加
```

### パターン3：フェーズ完了・移行
```markdown
ユーザー：「開業準備フェーズ完了」
↓
Claude：
1. opening-preparation/ を past-phases/opening-preparation-YYYY-MM/ に移動
2. 新フェーズディレクトリ作成
3. docs/README.md の「現在のフェーズ」を更新
4. フェーズ履歴テーブルを更新
```

---

## 📞 ユーザーへの確認が必要なケース

1. **機密情報を含む可能性がある場合**
   - 具体的な金額、個人情報等

2. **フェーズ移行時**
   - 新フェーズの名称・期間の確認

3. **大きな構造変更**
   - ディレクトリ構成の変更等

---

## 🔗 主要ファイルへのパス

### ルート
- `README.md` - 全体説明・フェーズ管理運用方針

### 現在のフェーズ（opening-preparation）
- `opening-preparation/README.md` - 開業準備ロードマップ
- `opening-preparation/phase1-december.md` - 12月TODO
- `opening-preparation/phase2-january.md` - 1月TODO
- `opening-preparation/phase3-incorporation.md` - 2月〜3月TODO
- `opening-preparation/business-goals.md` - お金稼ぐ計画
- `opening-preparation/funding-plan.md` - お金借りる計画

### マニュアル
- `manuals/README.md` - マニュアル一覧
- `manuals/business-finance-plan.md` - お金の運用計画
- `manuals/github-workflow.md` - GitHub運用ルール
- `manuals/GITHUB_ACCOUNT_PLAN.md` - GitHubアカウント設計

---

**最終更新：2025/12/14 - 初版作成**
