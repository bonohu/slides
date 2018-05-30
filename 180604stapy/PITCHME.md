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
- 生命科学における可視化
- その実例紹介（大石さんから）

---

## 生命科学のデータ

- 文字データ
  - 塩基(DNA)配列、アミノ酸配列
  - 研究やサンプルに関する記述（メタデータ）
- 数値データ
  - 遺伝子の発現量
  - 立体構造の座標

**原則、無料で誰でも無制限に使える！**

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

---

## 可視化手段

- Reference(参照)ゲノム配列にマッピング
- ゲノムブラウザで可視化

+++

### Reference ゲノム配列

- 2003年に完全解読したヒトゲノム、その更新版
- そのありか
  - Ensembl `http://asia.ensembl.org/info/data/ftp/index.html`
  - UCSC `http://hgdownload.soe.ucsc.edu/downloads.html`

**これらも、無料で誰でも無制限に使える！**

+++

### ゲノムマッピング

- Suffix array
- その実装
  - [Bowtie](http://bowtie-bio.sourceforge.net/)
    - Splice mapping用: TopHat → [HISAT2](https://ccb.jhu.edu/software/hisat2/)
  - [BWA](http://bio-bwa.sourceforge.net/)

**すべてフリーウェア**

---

## ゲノムブラウザ

---
