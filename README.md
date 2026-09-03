# Orito Codex Plugins

株式会社織翔が公開するCodex PluginのMarketplaceです。

## Installation

Marketplaceを追加します。

```bash
codex plugin marketplace add orito-inc/codex-plugins
```

利用するPluginをインストールします。

```bash
codex plugin add implementation-brief@orito
```

インストール後に新しいCodexセッションを開始してください。

## Implementation Brief

`implementation-brief`は、grilling、要件整理、意思決定の会話で確定した内容を、実装担当者へ渡せるMarkdown形式のbriefへ変換します。

### Usage

要件整理が終わった同じ会話で、明示的に呼び出します。

```text
$implementation-brief
```

別の会話で使う場合は、確定事項や意思決定メモも一緒に渡してください。

### Behavior

- 確定事項、推奨事項、未決事項を区別します。
- 受け入れ条件と検証方法を含む固定構造で出力します。
- briefはCodexのターミナル応答へ直接出力します。
- brief用ファイルの作成、リポジトリ変更、実装開始は行いません。
- 自動呼び出しは無効です。`$implementation-brief`で明示的に呼び出してください。

## ELI New

`eli-new`（Explain Like I'm New）は、前提知識のない大人が未知の話題について正しいメンタルモデルを作れるよう、具体例と図を使って説明するSkillです。目標は完全な技術理解ではなく、目的と仕組みを高いレベルで正しく捉えられることです。

`eli5`は「Explain Like I'm 5」に由来し、前提知識なしの説明を図と少ない言葉で作るSkillでしたが、「5歳向け」という対象レベルでは説明が抽象的すぎたり、具体例や実装詳細へ進みすぎたりすることがありました。`eli-new`は対象を「前提知識のない大人」と明確にし、幼児向けではなく知識ゼロからの理解を表します。

### Installation

```bash
codex plugin add eli-new@orito
```

### Usage

説明してほしい話題とともに呼び出します。

```text
$eli-new を使って、OAuth 2.0を前提知識のない大人向けに説明してください。
```

### Behavior

- 目的、具体例または有用なたとえ、実際の用語との対応、3〜5要素の図、重要な限界・境界の順で説明します。
- 実装手順、網羅的な派生、例外一覧は本編に含めず、必要な場合だけ「One level deeper」へ分離します。
- HTML/CSSまたはインラインSVGを使い、外部アセットやCDNに依存しない自己完結したHTMLファイルを1つ生成します。
- 同名の既存ファイルを上書きせず、ブラウザを自動起動しません。
- 明示的な依頼がない限り、生成物を公開・アップロードしません。

## YAGNI Review

`yagni-review`は、PRD、設計書、Implementation Brief、実装計画、ソースコードを対象に、現在の目的に不要なスコープや複雑性をYAGNI/KISSの観点で見直すSkillです。

### Installation

```bash
codex plugin add yagni-review@orito
```

### Usage

レビュー対象とともに明示的に呼び出します。

```text
$yagni-review を使って、この実装計画を現在の目的に必要な最小構成へ見直してください。
```

### Behavior

- 現在の目的、成功条件、利用者、規模、期限、拘束条件をレビューの基準にします。
- 各要素を`Keep`、`Simplify`、`Remove`、`Verify`のいずれかに分類します。
- 確定済み要件も現在の必要性を示す根拠と照合し、将来向けの汎用性や投機的な規模対応を除きます。
- 必要な安全性や正しさを維持しつつ、未要求の仕組みを追加しない最小版を提示します。
- 結果は推奨事項として返し、明示依頼がない限り対象の編集や実装は行いません。
- 自動呼び出しは無効です。`$yagni-review`で明示的に呼び出してください。

## Publication scope

このリポジトリでの公開は、GitHubでホストするOrito Codex Plugins Marketplaceへの掲載です。OpenAI公式のUniversal Plugin Directoryへの申請・掲載とは別であり、このMarketplaceへの追加だけで公式Directory掲載済みになるものではありません。

OpenAI公式仕様は2026-09-03に確認しています。

- [Build skills](https://developers.openai.com/plugins/build/skills)
- [Package your plugin](https://developers.openai.com/plugins/build/plugins)
- [Submit plugins](https://developers.openai.com/plugins/deploy/submission)

## License

[MIT License](LICENSE)
