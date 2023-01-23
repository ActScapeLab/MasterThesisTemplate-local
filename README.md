> 本リポジトリが提示するテンプレートはフォーク元が提供するものをベースに作成しています
> 
> フォーク元のREADMEにも環境構築に関する言及があるため，合わせて確認してください


# LaTeXによる卒論執筆（ローカルPC版）

大山研では卒論の執筆にLaTeXを使用しており，EditerにはOverleafの利用を推奨しています（2022年現在）

一方，無料版のOverleafではサイズの大きなPDFを作成しようとすると，コンパイルに失敗する（タイムアウトする）問題を抱えています

有料版を無料で1ヵ月だけ利用することもできるため，それを使っても良いですが，自身のPCにLaTeXの環境を構築することは以下のような利点があります

- ネット環境や有償コンテンツの有無に左右されずに卒論を執筆可能

- 編集にVSCodeを利用できる

- コンパイルエラーの原因を探りやすい

- コンパイルエラーになっても直前のPDFが残る

- Gitでの変更の差分管理が可能

本リポジトリはローカルPCにて卒論を作成した際の環境を残します



# 筆者の環境

|項目|値|
|:---:|:---:|
|OS|Windows 11|
|Editer|Visual Studio Code|

Macでもほぼ同じ設定内容で行けると思いますが，保証はしません

EditerはVSCodeを指定します．それ以外のやり方は各自で調べてください．



# 環境構築

本リポジトリはあくまで目安用なので，詳細については自身で調べてください

1. [Tex Live](https://www.tug.org/texlive/)のインストール（非常に時間がかかります）

1. VSCodeに「LaTeX Workshop」という拡張機能を入れる

1. VSCode上で「Ctrl + ,」を押すと設定が開くため，右上の中で一番左のアイコンをクリックして設定用のJsonを開く

1. `vscode-settings.json`に記載された内容を開いた設定用のJsonに追記する

1. `main.tex`を開き，右上の再生ボタンを押して，PDFをコンパイルする

1. コンパイルがうまくいけば右側にPDFが表示される

※ 十中八九，どこかでエラーになって躓くと思います．躓いたポイントはその都度共有し，このドキュメントをアップデートして下さい



# エラーの読み方

コンパイルエラーになった際には`out`ディレクトリ内の`main.log`を読むことを推奨します

1. **コンパイル中に**`main.log`を開く

1. コンパイルが終了し，エラーが出たときに`main.log`を一番下までスクロール

1. 下の方のどこかに以下のようにエラー原因が書かれているため，その原因に沿ってエラーを修正

    ※ この場合は，「163行目にある`\degree`コマンドは存在しません」と言われているため，`\degree`を削除する

    ```
    ./contents/5.BTPM.tex:163: Undefined control sequence.
    \degree ->\ERROR 
                    
    l.163 ...q:check_b2l}によって定式化される．\degree

    （以下，ダラダラと色々書いてあるがエラーの判読とは関係なし）
    （この上に書いてある数行がエラーの直接原因）

    Here is how much of TeX's memory you used:
        27519 strings out of 479466
        511957 string characters out of 5873881
        789770 words of memory out of 5000000
        44672 multiletter control sequences out of 15000+600000
        463119 words of font info for 129 fonts, out of 8000000 for 9000
        934 hyphenation exceptions out of 8191
        102i,30n,102p,525b,1023s stack positions out of 5000i,500n,10000p,200000b,80000s
    ```
