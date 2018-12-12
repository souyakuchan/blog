---
layout: post
title: souyakuchan 詠唱(bot)機能まとめ
---

[創薬アドベントカレンダー 2018](https://adventar.org/calendars/3041) 12 日目記事  
[#souyakuAC2018](https://twitter.com/search?q=%23souyakuAC2018)  
  
# souyakuchan_magic
今日はお馴染み、創薬ちゃんツイッターアカウントに実装されている構造式および立体分子構造の描画機能についておさらいがてら御紹介しておこう。  
  
基本的な用法は次の３つだ。  
  
- SMILES 記法による構造式描画  
> @souyakuchan c1ccccc1 #smiles
  
- IUPAC 名による構造式描画
> @souyakuchan benzene #iupac
  
- PDB ID による立体構造描画
> @souyakuchan 1emb #pdb

### SMILES 記法による構造式描画

<blockquote class="twitter-tweet" data-lang="ja"><p lang="und" dir="ltr">&quot;c1ccccc1&quot; <a href="https://twitter.com/hashtag/souyakuchan_magic?src=hash&amp;ref_src=twsrc%5Etfw">#souyakuchan_magic</a> <a href="https://t.co/f1xHZY9pAU">pic.twitter.com/f1xHZY9pAU</a></p>&mdash; 創薬ちゃん【レイドバトル開催中】 (@souyakuchan) <a href="https://twitter.com/souyakuchan/status/1072856947441848320?ref_src=twsrc%5Etfw">2018年12月12日</a></blockquote>
<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>  
  
このように、@souyakuchan にメンションする形で、呪文（SMILES 記法）に続けて #smiles と術式（ハッシュタグ）を指定することで二次元の構造式を詠唱（描画）したツイートを返す。  

SMILES 記法の書き方については、良いまとめ記事があったのでリンクを貼っておこう。  
- [SMILES記法は化学構造の線形表記法 -化学の新しいカタチ- 有機合成化学者のための計算化学・ケモインフォマティクス入門](https://future-chem.com/smiles-smarts/)  

元々、この詠唱機能は皆さんの自由な発想で任意の分子構造をツイートしてもらうために実装したものだが、SMILES 記法をマスターしていれば自力で書き下すのもできなくはないと思われるが、いきなり書き下すのはなかなか難しいと思われる。  
既知の分子であればデータベースなどから SMILES をそのまま取ってきてコピペすればよいが、一方、任意の構造式を描こうと思うと、通常は構造式エディタを使って描くのがやはり簡便だろう。  

<blockquote class="twitter-tweet" data-lang="ja"><p lang="ja" dir="ltr">化合物エディタ TL 埋め込みテスト。<br>動くかな？ PC ブラウザならページ遷移無しに TL 内で展開できるはずだ。<a href="https://t.co/bhvPprAyOH">https://t.co/bhvPprAyOH</a></p>&mdash; 創薬ちゃん【レイドバトル開催中】 (@souyakuchan) <a href="https://twitter.com/souyakuchan/status/990744010053464064?ref_src=twsrc%5Etfw">2018年4月30日</a></blockquote>
<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>  
  
これは JavaScript ベースの古典的な構造式エディタを流用したものだ。([JSME](http://peter-ertl.com/jsme/))  
  
また、PubChem などにも [構造式エディタ](https://pubchem.ncbi.nlm.nih.gov/search/#draw=true) は組み込まれており、構造式を描いたら SMILES を吐き出させることもできるので、容易に活用できるだろう。  
  
ちなみに、[PyMOL](https://pymol.org/2/) 使いであれば、PyMOL で構造式を描くこともできる。  
  
![Builder](https://user-images.githubusercontent.com/33997698/49877696-52dc7180-fe69-11e8-842f-145337995b83.png)

三次元空間内で構造式を描けるので、立体性の高い分子を描く場合などには便利に使うことができるだろう。  

### IUPAC 名による構造式描画

<blockquote class="twitter-tweet" data-lang="ja"><p lang="und" dir="ltr">&quot;c1ccccc1&quot; <a href="https://twitter.com/hashtag/souyakuchan_magic?src=hash&amp;ref_src=twsrc%5Etfw">#souyakuchan_magic</a> <a href="https://t.co/482x2Nhu0G">pic.twitter.com/482x2Nhu0G</a></p>&mdash; 創薬ちゃん【レイドバトル開催中】 (@souyakuchan) <a href="https://twitter.com/souyakuchan/status/1072857499785723904?ref_src=twsrc%5Etfw">2018年12月12日</a></blockquote>
<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>  
  
このように、@souyakuchan にメンションする形で、呪文（IUPAC 名）に続けて #iupac と術式（ハッシュタグ）を指定することで二次元の構造式を詠唱（描画）したツイートを返す。  
IUPAC 命名法をマスターして自力で書き下すのは敷居が高いと思われるが、これも既知の分子であればデータベースなどから IUPAC 名をそのまま取ってきてコピペすれば使うことができるだろう。  
また、暗記できているレベルの常識的な IUPAC 名（例: benzene）を入れてパパッと描画させるといった用法であれば SMILES 記法より使いやすいかもしれない。  

### PDB ID による立体構造描画

<blockquote class="twitter-tweet" data-lang="ja"><p lang="und" dir="ltr"><a href="https://t.co/2pwj88px7Z">https://t.co/2pwj88px7Z</a> <a href="https://twitter.com/hashtag/1emb?src=hash&amp;ref_src=twsrc%5Etfw">#1emb</a> <a href="https://twitter.com/hashtag/souyakuchan_magic?src=hash&amp;ref_src=twsrc%5Etfw">#souyakuchan_magic</a></p>&mdash; 創薬ちゃん【レイドバトル開催中】 (@souyakuchan) <a href="https://twitter.com/souyakuchan/status/1072858311526137856?ref_src=twsrc%5Etfw">2018年12月12日</a></blockquote>
<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>  
  
このように、@souyakuchan にメンションする形で、呪文（PDB ID）に続けて #PDB と術式（ハッシュタグ）を指定することで該当分子の立体構造を詠唱（描画）するツイートを返す。  
これは、TL に表示させたい分子を PDB から拾ってきて、ID をそのまま入力して頂く形になる。  

#### 実装者
これらの術式は、**ソーシャル創薬美少女** [@kubor_](https://twitter.com/kubor_) 氏によって実装されたものだ。Many thanks!  
  
みんなも是非、思い付いた新規な分子を TL に詠唱してみよう！
