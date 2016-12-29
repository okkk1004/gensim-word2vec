# 使用 gensim 中的 word2vec 訓練中文詞向量

## 簡介

一般初學自然語言處理的時候，處理文字最簡單的模型就是把每個詞當作一個單位，比如說用個 id 來表示他。然後再去算詞與詞之間的統計關係。或者是利用句子的文法結構來進行其他處理。如果把每個詞出現的次數當作一個維度的話，也可以把句子或文件用一個向量來表示，如此一來就可以計算餘弦相似度cosine或做其他後續處理。

不過 word2vec 是把每個詞本身用一個多維向量來表示，把詞投影到一個向量空間裡。而且投影出來的空間有些特殊性質，比如說相同屬性的詞可能會靠得很近，甚至部份的向量有邏輯上的線性關係等等，最常見的例子為
```
vector('King') - vector('Man') + vector('Woman') ~= vector('Queen')
```
因為 word2vec 的輸入必須是以空白隔開的詞，所以有了一堆文本以後，我們還得先對文本進行斷詞。通常中文斷詞系統最常使用的為中研院CKIP及Jieba，我這裡會以Jieba作為範例。

### CKIP v.s Jieba
CKIP - 有點慢，準確率高，詞性可細分為40多種

Jieba - 準確率略低一點，但較方便，可自定義使用者字典及停用詞，詞性僅粗分成5種

## 套件需求

* jieba
```
pip3 install jieba
```
* gensim
```
pip3 install -U gensim
```

###開發環境
Windows8 Jupyter notebook

## 流程

1.取得資料集，我這裡所採用的是愛評網的一部分食記內容(comment.txt)，若有其他需求，請自行爬蟲維基文章或任何大量文本資料來訓練

2.因為`jieba`斷詞後的結果不一定符合我們的預期，所以可以建立`userdict`使用者自訂字典以及`stopwords`停用詞字典
```
scrapy_data_jieba.ipynb   #將愛評網食記斷詞後輸出至comment1229.txt中
```

3.使用`gensim`的`word2vec`模型，訓練出一個模型
```
word2vec.ipynb   #會訓練出一個name為med250.model.bin的模型
```
###word2vec參數設定
* sentences:當然了，這是要訓練的句子集，沒有他就不用跑了
* size:這表示的是訓練出的詞向量會有幾維
* alpha:機器學習中的學習率，這東西會逐漸收斂到 min_alpha
* sg:這個不是三言兩語能說完的，sg=1表示採用skip-gram,sg=0 表示採用cbow
* window:還記得孔乙己的例子嗎？往左往右看幾個字的意思，印象中原作者論文裡寫 cbow 採用 5 是不錯的選擇
* workers:執行緒數目，除非電腦不錯，不然建議別超過 4
* min_count:若這個詞出現的次數小於min_count，那他就不會被視為訓練對象

4.測試

"# gensim-word2vec" 
