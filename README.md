# 使用 gensim 中的 word2vec 訓練中文詞向量

## 簡介

一般初學自然語言處理的時候，處理文字最簡單的模型就是把每個詞當作一個單位，比如說用個 id 來表示他。然後再去算詞與詞之間的統計關係。或者是利用句子的文法結構來進行其他處理。如果把每個詞出現的次數當作一個維度的話，也可以把句子或文件用一個向量來表示，如此一來就可以計算餘弦相似度cosine。

不過 word2vec 是把每個詞本身用一個多維向量來表示，把詞投影到一個向量空間裡。而且投影出來的空間有些特殊性質，比如說相同屬性的詞可能會靠得很近，甚至部份的向量有邏輯上的線性關係等等：

vector('King') - vector('Man') + vector('Woman') ~= vector('Queen')

因為 word2vec 的輸入必須是以空白隔開的詞，所以有了一堆文本以後，我們還得先對文本進行斷詞。通常中文斷詞系統最常使用的為中研院CKIP及Jieba，我這裡會以Jieba作為範例。

## 套件需求

* jieba
```
pip3 install jieba
```
* gensim
```
pip3 install -U gensim
```

## 流程

1.取得資料集，我這裡所採用的是愛評網的一部分食記內容(comment.txt)，若有其他需求，請自行爬蟲維基文章或任何大量文本資料來訓練

2.因為`jieba`斷詞後的結果不一定符合我們的預期，所以可以建立`userdict`使用者自訂字典以及`stopwords`停用詞字典

3.使用`jieba`對文本斷詞，並去除停用詞
```
python3 segment.py
```
4.使用`gensim`的`word2vec`模型，訓練出一個模型
```
python3 train.py
```
5.測試
```
python3 demo.py
```
"# gensim-word2vec" 
