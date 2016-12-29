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

1.取得資料集(https://dumps.wikimedia.org/zhwiki/20160820/zhwiki-20160820-pages-articles.xml.bz2)，本次實驗是採用 2016/8/20 的資料，若需更新的資料可以前往[維基百科:資料庫下載](https://zh.wikipedia.org/wiki/Wikipedia:%E6%95%B0%E6%8D%AE%E5%BA%93%E4%B8%8B%E8%BD%BD)下載

2.使用`wiki_to_txt.py`從xml格式裡提取出維基文章

```
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
