# 月とあたしとCWL

2019/09/21 Mishima.syk#14

なんでもがかり a.k.a. Dr.Bono

Note:
合計30分で

---

# お前誰やねん

- [坊農秀雅](http://bonohu.jp/) / Hidemasa Bono, PhD. /  [@bonohu](https://twitter.com/bonohu)
- 非プログラマなバイオ系
- Bio->Writer
    - [Dr. Bonoの生命科学データ解析](http://bonohu.jp/blog/category/drbonobon.html) 上梓 (2017/09)
    - [生命科学データベース・ウェブツール](http://bonohu.jp/blog/category/togotv18.html) 分担執筆＆監修 (2018/11)
    - [生命科学データ解析を支える情報技術](http://bonohu.jp/blog/category/it4bda.html) 分担執筆＆監修 (2019/02)
- Bio->Researcher
    - [PubMed](https://www.ncbi.nlm.nih.gov/pubmed?cmd=search&term=Bono%20H[au]%20AND%201995%3A2100[dp]%20NOT%20jpn[la]), [GoogleScholar](https://scholar.google.co.jp/citations?user=e6OaeXQAAAAJ&hl=ja)


---

# はなすこと

- CWLって?
- あたしとCWL
- これから

---

## CWLって?

- そうだ、Allieに聞こう！
    - http://allie.dbcls.jp/short/exact/Any/CWL.html

+++


### What is CWL

The Common Workflow Language (CWL) is an open standard for describing analysis workflows and tools in a way that makes them portable and scalable across a variety of software and hardware environments, from workstations to cluster, cloud, and high performance computing (HPC) environments.

From http://www.commonwl.org/
- hash tag [#CommonWL](https://twitter.com/hashtag/commonwl?f=tweets&vertical=default)

+++

### 64秒で分かる Common Workflow Language

https://youtu.be/86eY8xs-Vo8

+++

### CWL in use

- [NCBIがProkaryotic Genome Annotation Pipeline (PGAP)](https://ncbiinsights.ncbi.nlm.nih.gov/2019/03/13/run-prokaryotic-genome-annotation-pipeline/)
- [EBI Metagenomics](https://github.com/EBI-Metagenomics/ebi-metagenomics-cwl)
- [DDBJ human genome resequencing workflow](https://github.com/ddbj/human-reseq)

+++

## CWL in brief

- CommandLineTool
- Workflow
    - CommandLineToolを組み合わせて

---

## あたしとCWL


- なれそめ
- なぜに?


---

### いつから？

- そもそもワークフロー作成とか興味あった
- 2018年12月 [Biohackathon2018で洗脳^H^H感化](http://bonohu.jp/blog/biohackathon2018-hackathon-day2.html)されて
    - Docker使わないワークフロー作成を学さんから学ぶ
    - 同期生にHさん

+++

### meetupへの参加

- [2019年4月からworkflow meetup](http://bonohu.jp/blog/15th-workflow-meetup.html)に毎月行くように
    - Docker使うやり方で、`kallisto`や`salmon`を動かしたい
- 参加してたら何となく動かせるようになった→中上級講習会で
    - 2019年6月 [Shizuoka.ngs#2](https://shizuoka-ngs.connpass.com/event/128816/)では[kallisto](http://bonohu.jp/blog/running-kallisto-via-cwl.html)
    - 2019年7月 [AJACSa6河内](https://dbcls.rois.ac.jp/ja/2019/06/25/post1.html)では[salmon](https://github.com/AJACS-training/AJACSa6/tree/master/03_bono)


+++

### 見よう見まねでCWL書き

- [Trim GaloreのCommandLineTool](http://bonohu.jp/blog/bh197.html) at 国内版バイオハッカソン(BH19.7)
- [kallisto BUStoolsのチュートリアルを襷リレーでCWL化](http://bonohu.jp/blog/19th-workflow-meetup-3.html) at お盆ソン

+++

### 支援ツール

- [Rabix](https://rabix.io/)
    - [大阪大学医学部Python会: Common Workflow Language入門](https://pythonoum.wordpress.com/2018/12/07/common-workflow-language入門/)
- [Common Workflow Language Viewer](https://view.commonwl.org)
    - ex: `https://github.com/dbcls/AOE/blob/master/gethoge-and-pigz.cwl`

---
### なぜに？

- シェルスクリプトで書いているワークフローをなんとかしたい
  - 再利用できる形で
- Dockerも使いたい
  - しかも使い分けられるように
- 同じ条件で他の共同研究者にしてもらいたい
  - 大規模なメタ解析

+++

### ええとこ

- 個別のプログラムインストール不要
    - Dockerと`cwltool`が入っていればいい
    - ライブラリが他のソフトとぶつからない
- バージョン固定なので、絶対再現する（はず）

+++

### あかんとこ

- コンテナサイズが巨大
   - 回線が細いとダウンロードに手間取る
- メモリが多く必要
   - マシンによっては厳しい

---

### これから

- CWLを使うために
- 何でもCWLで書く？
- CWLを書こう
-
+++

### CWLを使うために

- 物理メモリは満タンでマシンを買う
- [Dockerへの割り当てメモリを増やす](http://bonohu.jp/blog/docker-setting-for-genomer.html)


+++

### 何でもCWLで書く？

- でもやっぱりシェルスクリプトも併用
    - まだまだ開発途上のワークフロー多数
    - いろんな環境で動かす必要のないものが多く
- でも、広く使ってもらうためのものはCWLで
    - [Shizuoka.ngs#2](https://shizuoka-ngs.connpass.com/event/128816/)でのハンズオン
    - [AJACSa6河内](https://dbcls.rois.ac.jp/ja/2019/06/25/post1.html)講習会でのハンズオン

+++

### CWLを書こう

- ハッシュタグ `#CommonWL` をつけてtweetすると
    - すぐに[Michael](https://twitter.com/biocrusoe)に捕捉されます
- 日本語でもOK。日本語nativeな極東のCWL書きがきっといい答えをくれますが、以下のドキュメントは日本語なので、読んどこうね
    - [雑に始める CWL！](https://qiita.com/tm_tn/items/4956f5ca523f7f49f386)
    - [続・雑に始める CWL！](https://qiita.com/tm_tn/items/83ce4c826135d78ba98f)
    - [CWLのワークフローを、ステップバイステップで書く。](https://qiita.com/manabuishiirb/items/e16baded333c9630bbdb)

---

## コマーシャル

[生命科学者のためのDr.Bonoデータ解析実践道場](https://amzn.to/30GaPLW)
2019年9月27日発売。booking in progress

![drbonobon](https://images-na.ssl-images-amazon.com/images/I/5174pENbQrL.jpg)


---
