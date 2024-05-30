# Probability-and-Statistics-Thesis

Repository for the codes of the thesis of Probability and Statistics, Spring 2024

## 论文简介

拼音输入法已经成了我们日常生活中不可分割的一部分。为了简化问题，我们只考虑全拼，即每个汉字对应的拼音串是合法的、完整的汉语拼音。现在的任务是，给定一个由全拼组成的拼音串，需要找到一个汉字串，使得这个汉字串的拼音是给定的拼音串，同时该串在语料库中出现的概率最大。概率越大，说明这个汉字串越有可能是用户想要输入的内容。

我们可以使用在《概率论与数理统计》这门课中学到的“条件概率”相关知识来解决这个问题。

## 程序的运行方式和文件结构

### 文件结构

```
Probability-and-Statistics-Thesis/
│  .gitignore
│  LICENSE
│  README.md
│
├─data
│  │  input.txt
│  │  output.txt
│  │
│  ├─lexicon
│  │      1st_2nd_order_characters.txt
│  │      pinyin2word.json
│  │      pinyin2word_all.txt
│  │
│  ├─sina_news_gbk
│  │      2016-04.txt
│  │      2016-05.txt
│  │      2016-06.txt
│  │      2016-07.txt
│  │      2016-08.txt
│  │      2016-09.txt
│  │      2016-10.txt
│  │      2016-11.txt
│  │      bi_word_count.json
│  │      README.txt
│  │      tri_word_count.json
│  │      uni_word_count.json
│  │
│  └─std_data
│          std_input.txt
│          std_output.txt
│
├─src
│      pinyin.py
│      preprocess.py
│      test.py
│
└─thesis
        thesis.tex
        thesis.toc
```

其中 `Probability-and-Statistics-Thesis/data` 文件夹可以从 [GitHub Release](https://github.com/LeverImmy/Probability-and-Statistics-Thesis/releases/download/data/data.zip) 中下载得到，或是通过将下发文件按照上图结构进行放置而得到：图中的 `1st_2nd_order_characters.txt` 即为下发文件中的 `一二级汉字表.txt`，`pinyin2word_all.txt` 即为下发文件中的 `拼音汉字表.txt`。

### 运行方式

假设当前处于 `Probability-and-Statistics-Thesis/src` 文件夹下：

- 对数据进行预处理：

  ```bash
  py ./preprocess.py
  ```

  该命令将重新生成 `uni_word_count.json`、`bi_word_count.json` 和 `tri_word_count.json`，预计完成时间为 $10.5$ 分钟。

- 对测试集进行测试：

  ```bash
  py ./pinyin.py < ../data/std_data/std_input.txt > test_output.txt
  ```

  该命令将会在 `Pinyin/Hand-in/src/` 下生成 `test_output.txt`，为测试集对应输出。

  也可以直接使用 `test.py` 进行测试：

  ```bash
  py ./test.py
  ```

  该命令将会以对比的形式，展示输出与标准答案不同的部分，同时统计句正确率、字正确率、平均单次响应时长和总响应时长。
