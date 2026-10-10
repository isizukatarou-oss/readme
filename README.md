## Git基本操作

・リモートリポジトリを取得する。
	
	git clone リポジトリURL

・最新のmainを取得する。

	git switch main
	git pull origin main

・自作業ブランチをローカルリポジトリで作成する。

	git switch -c 作業ブランチ名

・変更コードをローカルリポジトリにコミットする。

	git add . // 特定ファイルのみ追加する場合、git add ファイル名 とする。
	git status // 意図しないファイルを追加する可能性もあるので、コミット前に確認する。
	git commit -m "コミットコメント"

・リモートリポジトリにコミットした変更をプッシュする。

	git push -u origin 作業ブランチ名 // -u origin 作業ブランチ名 はリモートブランチを追跡先として設定するため、初回プッシュで -u を指定すれば、以降は git push だけでプッシュできる。

・GitHubのリポジトリ画面からPull Requestを作成する。

・マージ後にリポジトリの取得、最新のmainの取得、自作業ブランチの作成する。

・古いローカルのブランチを削除する。

	git branch // ローカルブランチ一覧が出力される。
	git branch -d 削除するローカルブランチ

## チーム開発流れ

１．現在のブランチを`git switch main`でmainブランチにする。

２．最新のコードを`git pull origin main`で取得する。

３．自分の作業ブランチを`git switch -c feature/workBranch`で作成する。

４．コードを変更した後、`git status`、`git diff`で変更内容を確認する。

５．変更を`git add .`、`git commit -m "機能追加"`でコミットする。

６．GitHubにブランチを`git push -u origin feature/workBranch`でアップロードする。

## 初回注意点

・ローカルリポジトリを初回作成し、GitHubにプッシュする。

`git init` //作業するディレクトリで実行する。

`git add .`

`git commit -m "コメント"` // 初回はこの後にユーザ名とメールアドレス登録が必要となる。

	git config --global user.name "GitHubのユーザ名"
	git config --global user.email "GitHubに登録したメールアドレス"

`git branch -M main` // mainブランチ

`git remote add origin https://github.com/ユーザ名/リポジトリ名.git`

`git push -u origin main` // アップロード前にReadme.mdを変更していれば、リベースを`git pull --rebase origin main`でする。

