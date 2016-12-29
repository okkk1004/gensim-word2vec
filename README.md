# 使用 gensim 中的 word2vec 訓練中文詞向量

## [教學文件](http://zake7749.github.io/2016/08/28/word2vec-with-gensim/)

## 套件需求

* jieba
```
pip3 install jieba
```
* gensim
```
pip3 install -U gensim
```

## 訓練流程

1.取得資料集，我這裡所採用的是愛評網的一部分食記內容(comment.txt)，若有其他需求，請自行爬蟲維基文章或任何大量文本資料來訓練

2.建立`userdict`使用者自訂字典以及`stopwords`停用詞字典

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
