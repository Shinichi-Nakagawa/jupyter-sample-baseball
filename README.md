# 日本プロ野球の成績Jupyterとpandasとmatplotlibで前処理・分析・可視化するサンプル

## 参考文献

こちらの書籍のテクニックを元に作成しました.

**[PythonユーザのためのJupyter[実践]入門](http://amzn.to/2hGnNaZ)**

## 何ができるのか

* [Scrapyのアプリケーション](https://github.com/Shinichi-Nakagawa/scrapy-sample-baseball)で集めた野球データ（打撃成績）の分析と可視化を行うサンプルです.
* こちらを真似・Fork・コピることにより,以下の事ができるようになります.
  * Jupyterの使い方を覚える
  * pandasの使い方と前処理・かんたんな統計分析
  * matplotlibで可視化
  * 野球のデータセットの使い方

## 動作環境

作者(shinyorke)の動作環境より.

* gitクライアント(何でもOK)
    * ソースコードを取得するために使う
    * 面倒くさい方は直接ダウンロードしてもらってもOK
* Python 3系の最新Ver
    * 3.6以上を推奨
    * 試してはいませんが,3.3.x以上なら動くと思う
    * 2.7.x系は未検証ですが多分動くと思います(がオススメしません&対応する気は無いです)
* Anacondaのインストール
    * [PythonユーザのためのJupyter[実践]入門](http://amzn.to/2hGnNaZ)での推奨方法
    * Anacondaへの抵抗がある方はpipで入れても構いません（どっちでもいい）

## セットアップ

Anaconda前提での解説です.

### 1. リポジトリをclone or ダウンロードする

#### クローンの場合

```bash
$ git clone https://github.com/Shinichi-Nakagawa/jupyter-sample-baseball.git
```

#### ダウンロードの場合

```bash
$ wget https://github.com/Shinichi-Nakagawa/jupyter-sample-baseball/archive/master.zip
$ unzip master.zip
```

### 2. Anacondaをインストール

* [公式サイト](https://repo.continuum.io/archive/)からお使いのOS・プラットフォームに合うイメージをダウンロード
* Anaconda3-4.3.1が推奨バージョンです
* 詳細はこの本に乗ってるので自信がないかたはご参考に→[PythonユーザのためのJupyter[実践]入門](http://amzn.to/2hGnNaZ)

### 3. 環境を作る

condaコマンドまでのパスを通したら以下のコマンドを実施

```bash
$ conda create -n jupyter-sample-baseball python=3.6
$ source activate jupyter-sample-baseball
$ conda install -y jupyter pandas notebook matplotlib bokeh
```

なお,bokehは使っていないので外しても大丈夫です(最初は使う想定でした...).

これでセットアップは完了です.

### 【補足】Anacondaを使いたくない方は

ご自身でPython 3の環境を用意,pip installしてください

```bash
$ pip install -r requirements.txt
```

## 使い方

### 1. ディレクトリに移動

Scrapyのエンドポイントにcdします.

```bash
$ cd jupyter-sample-baseball
```

なお,ダウンロードで手に入れた人は最初のディレクトリ名が変わるので注意

```bash
$ cd jupyter-sample-baseball-master
```

### 2. DBをコピー

[Scrapyのアプリケーション](https://github.com/Shinichi-Nakagawa/scrapy-sample-baseball)で集めた野球データをDirectory配下にコピります.

```bash
$ cp {Scrapyアプリのエンドポイント}/baseball/baseball/baseball.db .
```

### 3. Jupyterを起動

```bash
$ jupyter notebook
```

あとは好きなように遊んでみましょう！

## データについて

### 構造

[baseball/baseball/item.py](https://github.com/Shinichi-Nakagawa/scrapy-sample-baseball/blob/master/baseball/baseball/items.py)に乗っているカラムと解説が全てです.

カラムの名称は一般的に使われる野球英語の略称を用いています.

詳細は各Itemのコメントを参照ください.

### Table Scheme

[baseball/baseball/pipelines.py](https://github.com/Shinichi-Nakagawa/scrapy-sample-baseball/blob/master/baseball/baseball/pipelines.py)にCreate Table文があります.

カラムの意味と解説はItemと全く同じです(id値とcreate_date/update_dateがあるぐらいの違い)

なお,indexは全く貼っていないので必要な方は随時書き換えてもらえると.
