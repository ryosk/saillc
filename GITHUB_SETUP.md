# GitHubリポジトリのセットアップ手順

## リポジトリは作成済みです

リポジトリURL: https://github.com/ryosk/saillc

## コードをプッシュする方法

### 方法1: GitHub CLIを使用（推奨）

1. GitHub CLIで認証情報を設定（初回のみ）:
   ```bash
   gh auth login
   ```

2. リポジトリを確認:
   ```bash
   gh repo view ryosk/saillc
   ```

3. コードをプッシュ:
   ```bash
   git push -u origin main
   ```

### 方法2: 手動でプッシュ

1. GitHubのリポジトリページ（https://github.com/ryosk/saillc）にアクセス
2. リモートリポジトリのURLを確認
3. 以下のコマンドでプッシュ:
   ```bash
   git remote set-url origin https://github.com/ryosk/saillc.git
   git push -u origin main
   ```
   
   認証情報を求められた場合は、GitHubのPersonal Access Tokenを使用してください。

### 方法3: SSHキーを設定してプッシュ

1. SSHキーを生成（まだ持っていない場合）:
   ```bash
   ssh-keygen -t ed25519 -C "your_email@example.com"
   ```

2. SSHキーをGitHubに追加:
   - 公開鍵をコピー: `cat ~/.ssh/id_ed25519.pub`
   - GitHubのSettings → SSH and GPG keys → New SSH key に追加

3. リモートURLをSSHに変更:
   ```bash
   git remote set-url origin git@github.com:ryosk/saillc.git
   git push -u origin main
   ```

## Cloudflare PagesとGitHubを連携させる

GitHubリポジトリとCloudflare Pagesを連携させることで、自動デプロイが可能になります：

1. Cloudflare Dashboardにログイン
2. Workers & Pages → Pages → `sai-llc`プロジェクトを選択
3. 「設定」タブ → 「ビルドとデプロイ」セクション
4. 「GitHubと接続」をクリック
5. GitHubアカウントを認証
6. リポジトリ `ryosk/saillc` を選択
7. ブランチ `main` を選択
8. ビルド設定:
   - ビルドコマンド: （空欄のまま）
   - ビルド出力ディレクトリ: （空欄のまま）
   - ルートディレクトリ: `/`（デフォルト）
9. 「保存してデプロイ」をクリック

これで、GitHubにプッシュするたびに自動的にCloudflare Pagesにデプロイされます。

