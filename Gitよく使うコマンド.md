Gitよく使うコマンド

## 基本
add -> commit -> push の流れ

git add . // セーブ対象に追加


git commit -m "コメント" //セーブ

git push // リモートにプッシュ

## 初回設定時

git init // ローカルリポジトリ作成

git branch -M main // 現在のブランチをmainブランチに強制変更

git remote add origin URL // リモート名 URL

git push -u origin main // GitHubにアップロード、上流を origin/
mainに固定

## ブランチ系

git branch // 現在のブランチ表示

git branch -a // リモート追跡ブランチも表示

git branch ブランチ名 // ブランチ作成

git switch ブランチ名 // ブランチ名変更

git switch -c ブランチ名 // ブランチ作成+変更


## 補足系

git status // 未コミットの状態確認

git log // コミット履歴

git log --oneline // 1行表示

git log --graph // グラフ表示

git config // 設定

git --version // バージョン

git show // コミット状況表示 (logの1件)

git diff // コミット後の差分確認

git diff remotes/origin/main

git diff <ブランチ名> <ブランチ名>

## ダウンロード系

git clone URL // 丸ごとダウンロード

git clone -b <ブランチ名> URL // ブランチ指定してダウンロード

git clone URL <フォルダ名> // 指定フォルダ名でダウンロード

git clone -b <ブランチ名> URL <フォルダ名> 指定フォルダ名+ブランチ指定

git pull origin main　// 差分ダウンロード + マージ

git config pull.rebase false // pull時の挙動設定

git fetch origin main // 差分ダウンロード リモート追跡リポジトリを更新

git merge // fetch後マージ

## 取消系

### addされていないファイルを取り消し

git clear -f <フォルダ/ファイル>

git restore <フォルダ/ファイル>

git restore .

### addを取消

git restore

git reset

### commitを取消

git reset --soft HEAD^ // コミット前に戻る

git reset --mixed HEAD^ // add追加前に戻る

git reset --hard HEAD^ // 前回コミットまで戻る (ファイル変更も取消)
(コミットIDで指定するなら1つ前)

### pushを取消

git revert <コミットID> // 打消しコミット作成

git push origin main // 打消しコミットのプッシュ

git reset --soft HEAD^ // コミットの取り消し

git push -f origin main // 強制プッシュ

### pull requestを取消

git push --delete origin <ブランチ名> // プルリク削除


### local mergeを取消

git revert -m 1 <コミットID>

git reset --hard ORIG_HEAD

### commitコメントの修正

git commit --amend -m "修正後のコメント"

## コンフリクト

git stash // スタッシュ (コンフリクト発生時)

git stash save -u "コメント" コメント付きスタッシュ作成


git stash pop // スタッシュを適用+削除

git stash pop stash@{0} // スタッシュを指定

git stash drop // スタッシュを削除

git stash apply // スタッシュを適用

## タグ

git tag -a <タグ名> -m <コメント> <コミットID> // タグをコミットに付与

git tag // タグ一覧表示

git push origin <タグ名> // タグをpush

git tag -d <タグ名> // タグの削除
