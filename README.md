# 初回リポジトリ作成とコミット
１．カレントディレクトリでコマンドプロンプトを開く。

２．Gitリポジトリを`git init`で初期化する。

３．アップロードするファイルを`git add .`で登録する。

４．最初のコミットを`git commit -m "コメント"`で作成する。

※もし、`Author identity unknown`と出力された場合、以下のコマンドでユーザ名とメールアドレスを設定する。

　`git config --global user.name "GitHubのユーザー名"`
 
　`git config --global user.email "GitHubに登録したメールアドレス"`
 
 ５．ブランチ名を`git branch -M main`で main にする。
 
 ６．GitHubリポジトリへ`git remote add origin https://github.com/ユーザー名/リポジトリ名.git`で接続する。

 ７．Gitに初めてのアップロードを`git push -u origin main`でする。

 ※もし、アップロード前にReadme.mdを変更している場合、以下のコマンドでリベースを実行する。
 
`git pull --rebase origin main`
 

# チーム開発で使うコマンドの流れ
１．現在のブランチを`git switch main`でmainブランチにする。

２．最新のコードを`git pull origin main`で取得する。

３．自分の作業ブランチを`git switch -c feature/workBranch`で作成する。

４．コードを変更した後、`git status`、`git diff`で変更内容を確認する。

５．変更を`git add .`、`git commit -m "機能追加"`でコミットする。

６．GitHubにブランチを`git push -u origin feature/workBranch`でアップロードする。