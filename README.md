# Web通知テスト（GitHub Pages / Android向け）

## ファイル
- `index.html` — UI、許可要求、テスト通知
- `sw.js` — Service Worker。Android向けの永続通知表示とタップ処理
- `manifest.webmanifest` — Webアプリのメタデータ
- `icon-192.png` / `icon-512.png` — アイコン

## GitHub Pagesへの公開
1. GitHubで新しいリポジトリを作成する（公開設定）。
2. 上記ファイルをすべてリポジトリのルート（最上位）にアップロードする。
3. リポジトリの **Settings → Pages** を開く。
4. Build and deploymentで `Deploy from a branch`、ブランチ `main`、フォルダー `/(root)` を選び保存する。
5. 公開された `https://<ユーザー名>.github.io/<リポジトリ名>/` をAndroidのChromeで開く。

## Androidでのテスト
1. HTTPSの公開URLをChromeで開く。
2. 「通知を許可する」→「続ける」を押し、Chromeの通知許可を承認する。
3. 「テスト通知を送る」を押す。
4. 通知シェードに表示された通知をタップしてサイトに戻ることを確認する。

## 重要な制限
- 通知APIとService WorkerにはHTTPS（またはlocalhost）が必要です。GitHub PagesのHTTPS URLでテストしてください。
- このプロジェクトは**手動テスト通知のみ**です。サーバーからのWeb Push配信、定期通知、サイトを閉じた後に自動で届く通知は実装していません。
- 通知表示はブラウザ、Androidの通知設定、サイレントモード、電池設定などに左右されます。
- 通知をブロック済みの場合、ページから許可ダイアログを強制表示できません。Chromeのサイト設定で通知を許可してください。
- リポジトリのルートに置くことで、プロジェクトページのサブパスでも相対パスで動作する構成です。
- HTTPSの公開URLでない状態（Acodeの `content://` など）では正しく動作しない場合があります。

## セキュリティ
- 外部ライブラリ、追跡コード、APIキー、バックエンドは使っていません。
- 通知の許可はボタン操作からのみ要求します。
- 通知はユーザーの明示的な許可を前提にします。
