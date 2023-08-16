# linux
コマンド
ls
cd 
cat ファイルの中身確認
mkdir ディレクトリの作成
rm ファイル名 ファイルの削除
rm -r ディレクトリの削除
mv file file1 ファイル名の変更
mv file dir/ ファイルの移動 /は着けなくても問題なし
mv -i file file1 file1が上書きされるので確認

cp file new_file ファイルをコピー -iオプションで上書きするかの確認
cp file dir ディレクトリ内にコピー
cp -r dir new_dir ディレクトリのコピー

## ハードリンク
1つのファイルの実態に複数の名前を付ける機能
もとのファイルを削除しても消えない
すべてのハードリンクがなくなったときに削除される
→あるファイルに複数の名前を付けているようなもの
## シンボリックリンク
リンク先のパス名がかかれた特殊ファイル
リンク先がファイルの実態
リンク先のファイルを削除したり移動したりすると実行できなくなる
windowsでいうショートカット
シンボリックリンクの方が制限が少ないので使われる

ln file1 file2 file1にアクセスするハードリンクfile2を作成
ln file1 file3 file1にアクセスするシンボリックリンクfile3を作成

## findコマンド
find 検索開始ディレクトリ 検索条件 アクション
例：find . -name README.md -print
-name 名前の検索
ワイルドカードが使える
例：find . -name "*.html" -print

-iname ファイル名の大文字小文字の区別なし

-type 
-type f は通常ファイル
-type l はシンボリックリンク
-type d はディレクトリ
-a 複数の検索条件を指定
find . type -d -a -name images -print


## 標準入出力
### リダイレクト
* キーボードの代わりにファイルから入力をする
cat < /etc/hosts
* 画面表示をする代わりにファイルへと保存する
ls > output.txt
cat > output.txt
* エラー出力
2を使う
ls /hoge 2> error.txt
出力とエラー出力をまとめるとき
ls /hoge > output.txt 2>&1
リダイレクトの追記 2つ重ねると追記
echo Hello!! >> output.txt

* /dev/null
ブラックホールだね．結果の出力先として指定することが多く，結果を非表示にしたいときに使用する．
例：ls > /dev/null
ちなみにls /hoge > /dev/nullはエラーなので出力される
ls /hoge 2> /dev/nullは出力されなくなる

### パイプライン
|を使う
* ls/bin | less
* ls/bin | grep systemd | less
## パーミッション
ls -lで確認ができる
オーナーとグループが見える（自分のubuntu内だとmoribe moribe）
ls -l /bin/lessだとroot,root

cat /etc/passwdで全ユーザのidが見れる