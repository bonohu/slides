## PythonとJavaScriptによる生命科学データ解析における可視化サービスの構築

2018/06/04 at 東京

坊農秀雅 a.k.a. Dr.Bono

Note:
概論

---

## お前誰やねん

- 坊農秀雅 / Hidemasa Bono, PhD. /  [@bonohu](https://twitter.com/bonohu)
- [温泉インフォマティクス研究会](https://twitter.com/kubor_/status/860448923441221632) 主催
- [Dr. Bonoの生命科学データ解析](http://bonohu.jp/blog/category/drbonobon.html) 上梓 (2017/9)

![drbonobon](https://images-na.ssl-images-amazon.com/images/I/51gwooGvqYL.jpg)

+++

### ライフサイエンス統合データベースセンター所属

- [Database Center for Life Science (DBCLS)](https://dbcls.rois.ac.jp/)

![DBCLS](http://leading.lifesciencedb.jp/wordpress/wp-content/uploads/2014/06/logo_en_c.png)

+++

### DBCLS

- 2007年4月設立の研究所
  -  現在、柏の葉と三島の2拠点で活動
- ライフサイエンス分野DBとサービスの専門機関
- 国内を中心にDBの統合化と保全に努める
- 利用者の利便性を高めるための情報技術の研究開発やサービスの開発を行う
  - DNA配列や遺伝子発現データベースを使いやすくする技術開発

---

## はなすこと
- 生命科学データ
- 生命科学における可視化手段
- その実例紹介（[大石さん](https://twitter.com/oec014)から）

---

## 生命科学データ

- 文字データ
  - 塩基(DNA)配列、アミノ酸配列
  - 研究やサンプルに関する記述（メタデータ）
  - 個体差（バリアント）
- 数値データ
  - 遺伝子の発現量
  - タンパク質立体構造の座標

**原則、無料。誰でも自由に使える！**

+++

### 塩基配列データ

```
>NM_007262.4 Homo sapiens Parkinsonism associated deglycase (PARK7), transcript variant 1, mRNA
TGAGTCTGCGCAGTGTGGGGCTGAGGGAGGCCGGACGGCGCGCGTGCGTGCTGGCGTGCGTTCATTTTCA
GCCTGGTGTGGGGTGAGTGGTACCCAACGGGCCGGGGCGCCGCGTCCGCAGGAAGAGGCGCGGGGTGCAG
GCTTGTAAACATATAACATAAAAATGGCTTCCAAAAGAGCTCTGGTCATCCTGGCTAAAGGAGCAGAGGA
AATGGAGACGGTCATCCCTGTAGATGTCATGAGGCGAGCTGGGATTAAGGTCACCGTTGCAGGCCTGGCT
GGAAAAGACCCAGTACAGTGTAGCCGTGATGTGGTCATTTGTCCTGATGCCAGCCTTGAAGATGCAAAAA
AAGAGGGACCATATGATGTGGTGGTTCTACCAGGAGGTAATCTGGGCGCACAGAATTTATCTGAGTCTGC
TGCTGTGAAGGAGATACTGAAGGAGCAGGAAAACCGGAAGGGCCTGATAGCCGCCATCTGTGCAGGTCCT
ACTGCTCTGTTGGCTCATGAAATAGGTTTTGGAAGTAAAGTTACAACACACCCTCTTGCTAAAGACAAAA
TGATGAATGGAGGTCATTACACCTACTCTGAGAATCGTGTGGAAAAAGACGGCCTGATTCTTACAAGCCG
GGGGCCTGGGACCAGCTTCGAGTTTGCGCTTGCAATTGTTGAAGCCCTGAATGGCAAGGAGGTGGCGGCT
CAAGTGAAGGCTCCACTTGTTCTTAAAGACTAGAGCAGCGAACTGCGACGATCACTTAGAGAAACAGGCC
GTTAGGAATCCATTCTCACTGTGTTCGCTCTAAACAAAACAGTGGTAGGTTAATGTGTTCAGAAGTCGCT
GTCCTTACTACTTTTGCGGAAGTATGGAAGTCACAACTACACAGAGATTTCTCAGCCTACAAATTGTGTC
TATACATTTCTAAGCCTTGTTTGCAGAATAAACAGGGCATTTAGCAAACTAAAAAAAAAAAAAAAAAAA
```

+++
### メタデータ（研究）

![Bioproject](images/bioproject.png)

+++
### メタデータ（サンプル）

![Biosample](images/biosample.png)

+++
### 個体差

- ヒト30億塩基対に1000塩基に1つ
  - 一塩基多型が多い
- それを記述する形式:
  - VCF(Variant Call Format)

```
#CHROM POS     ID        REF ALT    QUAL FILTER INFO                              FORMAT      NA00001        NA00002        NA00003
20     14370   rs6054257 G      A       29   PASS   NS=3;DP=14;AF=0.5;DB;H2           GT:GQ:DP:HQ 0|0:48:1:51,51 1|0:48:8:51,51 1/1:43:5:.,.
20     17330   .         T      A       3    q10    NS=3;DP=11;AF=0.017               GT:GQ:DP:HQ 0|0:49:3:58,50 0|1:3:5:65,3   0/0:41:3
20     1110696 rs6040355 A      G,T     67   PASS   NS=2;DP=10;AF=0.333,0.667;AA=T;DB GT:GQ:DP:HQ 1|2:21:6:23,27 2|1:2:0:18,2   2/2:35:4
20     1230237 .         T      .       47   PASS   NS=3;DP=13;AA=T                   GT:GQ:DP:HQ 0|0:54:7:56,60 0|0:48:4:51,51 0/0:61:2
20     1234567 microsat1 GTCT   G,GTACT 50   PASS   NS=3;DP=9;AA=G                    GT:GQ:DP    0/1:35:4       0/2:17:2       1/1:40:3
```
---

## ヒトデータの可視化手段

例：配列の場合、典型的には

1. Reference(参照)ゲノム配列にマッピング
2. ゲノムブラウザで可視化

数値データの場合は、多次元のデータが多いので、主成分分析して第1,2主成分で散布図なんてこともしばしば

+++

### Reference ゲノム配列

- 2003年に完全解読したヒトゲノム、その更新版
- そのありか
  - Ensembl `http://asia.ensembl.org/info/data/ftp/index.html`
  - UCSC `http://hgdownload.soe.ucsc.edu/downloads.html`

**これらも、無料で誰でも無制限に使える！**

+++

### ゲノムマッピング

- 入力: 100-150塩基 x 約1億
- 検索対象: ヒトゲノム配列(30億塩基)
  - Burrows Wheeler Transform
    - 検索対象文字列の出現位置を高速に検索できるように
  - その実装
    - [Bowtie](http://bowtie-bio.sourceforge.net/)
    - [BWA](http://bio-bwa.sourceforge.net/)

**すべてフリーウェア**

---

## ゲノムブラウザ

http://genome-asia.ucsc.edu

[詳しくは統合TVにて動画で使い方を紹介](http://doi.org/10.7875/togotv.2017.105)

---
