# Death Clock - GitHub Pages Setup

## フォルダ構成

```
GitHub_Pages/
├── _config.yml              # Jekyll設定
├── privacy-policy.html      # プライバシーポリシー（HTML版）
├── privacy-policy.md        # プライバシーポリシー（Markdown版）
├── terms-of-service.html    # 利用規約（HTML版）
├── terms-of-service.md      # 利用規約（Markdown版）
├── assets/                  # 静的ファイル（CSS、画像など）
└── templates/               # テンプレートファイル
```

## GitHub Pages設定手順

### 1. リポジトリ設定
1. GitHubリポジトリの「Settings」タブに移動
2. 左サイドバーの「Pages」をクリック

### 2. ソース設定
以下のいずれかの方法を選択：

#### 方法A: カスタムフォルダ指定
- Source: "Deploy from a branch"
- Branch: "main" (または現在のブランチ)
- Folder: "/ (root)" → 後でパス指定

#### 方法B: 専用ブランチ作成
```bash
# gh-pagesブランチを作成
git checkout -b gh-pages
git add GitHub_Pages/*
git commit -m "Add GitHub Pages legal documents"
git push origin gh-pages
```

### 3. 公開URL
設定完了後、以下のURLでアクセス可能：
- `https://[username].github.io/[repository-name]/GitHub_Pages/privacy-policy.html`
- `https://[username].github.io/[repository-name]/GitHub_Pages/terms-of-service.html`

### 4. カスタムドメイン（オプション）
独自ドメインを使用する場合：
1. 「Custom domain」欄にドメインを入力
2. DNSレコードを設定
3. HTTPS証明書を有効化

## アプリ内連携

### URL更新が必要な箇所
1. `PrivacyConsentView.swift` の172-173行目、182-183行目
2. TODOコメントを実際のURL処理に置き換え

### 実装例
```swift
Button("プライバシーポリシー") {
    if let url = URL(string: "https://[your-domain]/privacy-policy.html") {
        UIApplication.shared.open(url)
    }
}
```

## 多言語対応（将来的）
`templates/`フォルダに各言語版のテンプレートを配置可能

## 更新手順
1. Markdownファイルを編集
2. 必要に応じてHTMLファイルも更新
3. Gitにコミット・プッシュ
4. GitHub Pagesが自動更新（数分後）

## 注意事項
- 公開されるページは全世界からアクセス可能
- 法的文書の内容は専門家による確認を推奨
- 定期的な内容見直しが必要