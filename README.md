# readme
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
 
