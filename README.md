# Orito Codex Plugins

株式会社織翔が公開するCodex PluginのMarketplaceです。

## Installation

Marketplaceを追加します。

```bash
codex plugin marketplace add orito-inc/codex-plugins --ref main
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

## License

[MIT License](LICENSE)
