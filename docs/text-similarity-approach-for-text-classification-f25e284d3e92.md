# 文本相似性度量对文本分类问题有帮助吗？

> 原文：<https://medium.com/analytics-vidhya/text-similarity-approach-for-text-classification-f25e284d3e92?source=collection_archive---------7----------------------->

![](img/81fa2c80691c277880a5183fabbf47dc.png)

图片由来自 [Pixabay](https://pixabay.com/?utm_source=link-attribution&utm_medium=referral&utm_campaign=image&utm_content=1204029) 的 [Lubos Houska](https://pixabay.com/users/luboshouska-198496/?utm_source=link-attribution&utm_medium=referral&utm_campaign=image&utm_content=1204029) 拍摄

曾经有一则新闻传遍网络，“消毒剂无助于对抗冠状病毒”。这条新闻在社交媒体上被分享，理由是因为冠状病毒是一种病毒，抗菌洗手液不会做任何事情。据 FactCheck.org 称，2020 年 3 月 1 日，当一位自称“科学家”的人在推特上发布他们的理论时，谣言就开始了。然而，根据 CDC 的说法，如果没有肥皂和水，使用含至少 60%酒精的洗手液是一种合适的替代品。

还有一个故事流传，“联邦政府已经下令工作场所关闭两周，以避免冠状病毒的传播”。然而，没有作出这样的授权。根据 FactCheck.org 的说法，这些被分享的帖子原本是一个笑话，当用户点击链接“阅读更多”时，会有一个笑点等着他们其他的帖子也把“政府”的提法换成了密歇根、佛罗里达、阿拉巴马和其他州的说法。该国一些地区已经宣布进入紧急状态，但并没有扩大到迫使工作场所关闭。这两个是有代表性的故事。我们每天都能在社交媒体平台上看到这类故事。因为这些故事制造了轰动效应，人们倾向于认同它并开始分享它。他们没有意识到的一点是，这些故事是假的。

尽管人们很容易接触到真实的事实和事实核查人员，但他们还是会相信假新闻。假新闻之所以成为一个问题，部分原因是人们确实会听信这些故事，而向他们展示事实无助于纠正这个问题。这是由于人类思维的一个特征，叫做认知偏差。认知偏差是推理、记忆或评估某件事情时的差距，会导致错误的结论。它们是普遍的。每个人都有。认知偏差影响我们使用信息的方式。四种类型的认知偏差与假新闻及其对社会的影响特别相关:首先，我们倾向于根据标题和标签采取行动，而不阅读与它们相关的文章。其次，社交媒体传达的信号会影响我们对信息受欢迎程度的感觉，从而让我们更容易接受。第三，假新闻利用了最常见的政治心理捷径:党派偏见。第四，有一种奇怪的趋势，虚假信息会一直存在，即使在它被纠正之后。

自然语言理解的主要问题之一是文本中语言的复杂性。因为这些文章都有不同的新闻写作方法，我们得出结论，在如此多样化的语言表达中应用相似性度量和概括结果不是一个好主意。因此，我们决定尽可能简化语言表示。项目的第四阶段集中于简化真实的新闻文章。在这个阶段，我们还试图通过改变文本数据中的一些词语，从那些真实的新闻中生成假新闻。前三篇，我们只是简单的把一个正面的词反过来变成一个负面的词，把一个真实的新闻转换成假新闻。例如，第三篇文章指出，“在 2020 年 5 月新冠肺炎冠状病毒疾病疫情期间，美国联邦和州政府正在努力解决的主要问题之一是保持社交距离和商业关闭限制以保护生命的权衡，以及对个人、企业和整个国家的持续(可能是永久)经济损害的权衡。”这个故事变成了一个虚假的故事，只不过是把下划线的单词改成了“我们没有摔跤”。

同样，在最后四篇文章中，我们试图改变文章的结构，将其转换为一个虚假的故事，但保留了文章的上下文。例如，第六篇文章谈到奥巴马政府向中国科学院武汉病毒研究所提供了 370 万美元的拨款，冠状病毒的起源就是从那里推测的。我们添加了我们自己的额外信息，即奥巴马总统直接指示释放病毒以破坏唐纳德·特朗普总统任期，这是错误的。转换后的虚假故事如下。“2020 年 4 月，有报道称，美国国家卫生研究院(NIH)在奥巴马总统在任期间直接下令向中国科学院武汉病毒研究所提供了 370 万美元的拨款。报告还指出，奥巴马总统明确指示泄露一种致命病毒，给即将上任的唐纳德·特朗普总统造成问题。这些报道支持了新型冠状病毒从这个病毒学实验室逃脱的传言。”

我用 python 编程语言和 google colab 作为我们的工作空间。我们主要研究了三种相似性度量:Jaccardian 相似性、余弦相似性和软余弦相似性。先详细讨论一下。

## Jaccardian 相似性

Jaccard 相似性(系数)，一个由 Paul Jaccard 创造的术语，用于度量集合之间的相似性。Jaccardian 相似性可以针对两种表示来计算:基于集合的表示和基于向量的表示。它被定义为交集的大小除以两个数据的并集的大小。它比较两个数据集的成员，以查看哪些成员是共享的，哪些是不同的。这是对两组数据相似性的度量，范围从 0%到 100%。百分比越高，两个种群越相似。虽然它很容易解释，但它对小样本非常敏感，可能会给出错误的结果，特别是对于非常小的样本或缺失观测值的数据集。

让我们看一个基于集合表示的 Jaccard 相似性的例子。考虑以下两句话:

哈里是一名学生。

上述两个集合 Jaccard 相似性的数学表示为:

现在，| A ⋂ B | = | {是，a，学生} | = 3 和| A U B | = | {哈利，是，a，学生，他，学校，去} | = 7。

因此，J(A，B)= | A ⋂ B | / | A U B | = 3/7 = 0.43

让我们从向量表示的角度来分析这个例子

考虑两个集合 x={x1，x2，…，xn}和 y={y1，y2，…..，yn}在向量空间表示中。那么它们之间的 Jaccard 系数为:

让我们考虑上面的两个句子 A 和 b。在基于向量的表示中，我们在单词包(BoW)模型中表示这两个句子。在单词袋方法中，完整数据中的所有单词在列中表示，句子或文档在行中表示。现在，我们开始计算每个单词在所有文档/数据集中的出现次数，并填充这些值。下表显示了我们的两个例句的单词包表示。

根据上面的公式，分子是由每一列中的最小值之和计算出来的。这导致分子= (0+1+0+0+1+0) = 3。类似地，分母通过每列中最大值的总和来计算。这导致分母= (1+1+1+1+1+1+1+ = 7，因此 Jaccard 相似性=分子/分母= 3/7 = 0.43

Jaccard 相似性只对少量数据有用。考虑一个包含数千个文档的数据集。为如此大量的数据表示一个单词包模型可能不切实际。此外，当我们有一个相似的句子，但有一组不同的单词时，Jaccard 相似性就失效了。考虑以下句子:

A = {俄成功测试新冠肺炎疫苗} B = {冠状病毒解毒剂人体试验现已完成}

这两个句子推断出相似的意思，尽管 B 句中的信息可能不完整。但是如果我们分析这些句子之间的相似度，雅克第相似度将会是 0，因为句子 A 和 b 之间没有共同的单词。

| A ⋂ B | = | { } | = 0 因此 Jaccard 的系数(a，B ) = 0。

## 第一条

```
from __future__ import division
import string
import math

tokenize = lambda doc: doc.lower().split(" ")document_1_0 = "Circulating on social networks a video that shows an excerpt from a Spanish television show, supposedly issued December 24, 2019, in which it appears a woman (who claims to be psychic) to make predictions. In this video, the woman describes a set of events that have been interpreted as a detailed forecast of Covid-19 pandemic that has hit the world. It is, however, a fake video, at least as regards the date of issue. The video has been being disseminated on the Internet with a date and not tampered with the real."
document_1_1 = "Circulating on social networks a video that shows an excerpt from a Spanish television show, supposedly issued December 24, 2019, in which it is not appearing  a woman (who claims to be psychic) to make predictions. In this video, the woman does not describe a set of events that have not  been interpreted as a detailed forecast of Covid-19 pandemic that has not hit the world record. It is, however, a fake video, at least as regards the date of issue. The video has not been disseminated on the Internet with a date and not tampered with the real news."

document_2_0="On Feb. 28, 2020, the website PJ Media published an article claiming that U.S. President Barack Obama had waited until millions were infected and thousands were dead from swine flu, the H1N1 virus, before declaring a public health emergency in 2009\. The article, which was presented as a    fact check,    got several simple details wrong."
document_2_1="On Feb. 28, 2020, the website PJ Media published an article claiming that U.S. President Barack Obama has not waited until millions were not infected and thousands were not dead from swine flu, the H1N1 virus, before declaring a public health emergency in 2009\. The article, which was not  presented as a    fact check,    got several simple details True."

document_3_0="One of the primary issues that the U.S. federal and state governments were wrestling with during the COVID-19 coronavirus disease pandemic in May 2020 was the trade-off of keeping social distancing and business closure restrictions in place to protect lives, versus the trade-off of ongoing (and possibly permanent) economic harm to individuals, businesses, and the country as a whole."
document_3_1="One of the primary issues that the U.S. federal and state governments were not wrestling with during the COVID-19 coronavirus disease pandemic in May 2020 was not the trade-off of keeping social distancing and business closure restrictions in place to protect lives, versus the trade-off of ongoing (and possibly permanent) economic harm to individuals, businesses, and the country as a whole."

document_4_0="A number of countries have agreed to speed up the development of tests, drugs and vaccines against COVID-19 and share them globally. Countries like France, Germany and South Africa joined the virtual conference to launch a fight against  COVID-19\. We are facing a common threat which we can only defeat with a common approach, WHO Director General Tedros Adhanom Ghebreyesus said pointing out that the tools should be equally available to all. European Commission President Ursula von der Leyen said that the objective would be to raise 8.1 billion dollars to speed up prevention, diagnostics and treatment. Despite the support from many other countries, the USA was not present in the virtual conference after the country discontinued regular funds to WHO claiming it was helping China to hide the information about the origin of the virus."
document_4_1="The USA has been on the frontline to assist WHO in the fight against COVID-19\. While many other countries like France, Germany and South Africa have not shown interest in this initiative, the USA has supported the objective to raise 50 billion dollars to speed up prevention. The WHO director  Tedros Adhanom Ghebreyesus stated that the treatment would be only provided to the country who contributes more to speed up diagnostics and prevention of the virus. European Commission President Ursula von der Leyen has strongly disagreed to the WHO director's statement saying that cure should be available to all equally. US officials have not responded in this matter."

document_5_0="The government of China has donated medical equipment to Rwanda for fighting the COVID-19 pandemic. The equipment including N95 face masks, surgical masks, protective clothing, infrared thermometers, and surgical gloves were handed over to the Ministry of Health. Ambassador of China to Rwanda said that the donation represents China’s determination on assisting other countries during this pandemic."
document_5_1="The government of China has denied Rwanda’s request to assist the country with medical equipment to fight with the COVID-19 pandemic. The request was made during a diplomatic meeting between the Health Minister of Rwanda and Ambassador of China to Rwanda. The ambassador in response said that demand for medical equipment is huge in China and it cannot assist any other countries in the current situation."

document_6_0="In April 2020, reports started to circulate  that the National Institutes of Health (NIH) had provided the Wuhan Institute of Virology a $3.7 million grant in 2015, while former U.S. President Obama was still in office. These reports were often accompanied by the evidence-free suggestion that the novel coronavirus that causes COVID-19 had escaped from this lab."
document_6_1="In April 2020, there were reports that the National Institute of Health(NIH) provided a grant of 3.7 million dollars to Wuhan Institute of Virology under direct order of President Barack Obama while he was in office. The reports also state that President Obama gave clear instructions to leak a deadly virus to cause problems for the upcoming president Donald Trump. These reports support rumors that the novel coronavirus has escaped from this virology lab."

document_7_0="The Food and Drug Administration issued a warning about the use of hydroxychloroquine, an antimalarial drug, after it became aware of heart risks. The drug has widely been encouraged by United States President Donald Trump as a potential treatment. FDA said that they became aware of reports of serious heart rhythm problems in patients with COVID-19 treated with hydroxychloroquine often in combination with azithromycin."
document_7_1="The Food and Drug Administration has issued a press release encouraging health officials to use hydroxychloroquine, an antimalarial drug, as potential treatment of COVID-19\. The press release states that the clinical trial is now complete and use of the drug cured COVID-19 patients of all age groups within a week. The drug was also encouraged by United States President Donald Trump after he claimed in a press conference that he was taking hydroxychloroquine as a preventive measure against COVID-19\. This press release has now encouraged millions of health workers in the US and all around the world to go forward with the use of the drug as a cure against COVID-19."all_documents = [document_1_0, document_1_1]

tokenized_documents = [tokenize(d) for d in all_documents] # tokenized docs
all_tokens_set = set([item for sublist in tokenized_documents for item in sublist])all_tokens_set{'',
 '(who',
 '2019,',
 '24,',
 'a',
 'an',
 'and',
 'appearing',
 'appears',
 'as',
 'at',
 'be',
 'been',
 'being',
 'circulating',
 'claims',
 'covid-19',
 'date',
 'december',
 'describe',
 'describes',
 'detailed',
 'disseminated',
 'does',
 'events',
 'excerpt',
 'fake',
 'forecast',
 'from',
 'has',
 'have',
 'hit',
 'however,',
 'in',
 'internet',
 'interpreted',
 'is',
 'is,',
 'issue.',
 'issued',
 'it',
 'least',
 'make',
 'networks',
 'news.',
 'not',
 'of',
 'on',
 'pandemic',
 'predictions.',
 'psychic)',
 'real',
 'real.',
 'record.',
 'regards',
 'set',
 'show,',
 'shows',
 'social',
 'spanish',
 'supposedly',
 'tampered',
 'television',
 'that',
 'the',
 'this',
 'to',
 'video',
 'video,',
 'which',
 'with',
 'woman',
 'world',
 'world.'}def jaccard_similarity(query, document):
    intersection = set(query).intersection(set(document))
    union = set(query).union(set(document))
    return len(intersection)/len(union)

jaccard_similarity(tokenized_documents[0],tokenized_documents[1])0.8108108108108109all_documents = [document_1_0, document_2_0]

tokenized_documents = [tokenize(d) for d in all_documents] # tokenized docs
all_tokens_set = set([item for sublist in tokenized_documents for item in sublist])

jaccard_similarity(tokenized_documents[0],tokenized_documents[1])0.09345794392523364
```

通过简单地将真实新闻集中的正面词转换为负面词，我们不能通过雅克第相似性来区分它们

## 第二条

```
all_documents = [document_2_0, document_2_1]

tokenized_documents = [tokenize(d) for d in all_documents] # tokenized docs
all_tokens_set = set([item for sublist in tokenized_documents for item in sublist])

jaccard_similarity(tokenized_documents[0],tokenized_documents[1])0.9090909090909091
```

类似的情况在这里上面作为倒装句

## 第三条

```
all_documents = [document_3_0, document_3_1]

tokenized_documents = [tokenize(d) for d in all_documents] # tokenized docs
all_tokens_set = set([item for sublist in tokenized_documents for item in sublist])

jaccard_similarity(tokenized_documents[0],tokenized_documents[1])0.9791666666666666
```

## 第四条

```
all_documents = [document_4_0, document_4_1]

tokenized_documents = [tokenize(d) for d in all_documents] # tokenized docs
all_tokens_set = set([item for sublist in tokenized_documents for item in sublist])

jaccard_similarity(tokenized_documents[0],tokenized_documents[1])0.35877862595419846
```

在这里，我们现在已经改变了这个词的上下文，因此我们现在看到了不同之处

## 第五条

```
all_documents = [document_5_0, document_5_1]

tokenized_documents = [tokenize(d) for d in all_documents] # tokenized docs
all_tokens_set = set([item for sublist in tokenized_documents for item in sublist])

jaccard_similarity(tokenized_documents[0],tokenized_documents[1])0.2753623188405797
```

## 第六条

```
all_documents = [document_6_0, document_6_1]

tokenized_documents = [tokenize(d) for d in all_documents] # tokenized docs
all_tokens_set = set([item for sublist in tokenized_documents for item in sublist])

jaccard_similarity(tokenized_documents[0],tokenized_documents[1])0.3918918918918919
```

## 第七条

```
all_documents = [document_7_0, document_7_1]

tokenized_documents = [tokenize(d) for d in all_documents] # tokenized docs
all_tokens_set = set([item for sublist in tokenized_documents for item in sublist])

jaccard_similarity(tokenized_documents[0],tokenized_documents[1])0.3409090909090909
```

## 我们可以说，如果假新闻中的词汇只是简单地与真实新闻中的词汇相对照，那么 Jaccardian 测度就无法发现差异。但是一旦我们改变了新闻文章的上下文，我们就会发现相似性的价值降低了

# 余弦相似性

余弦相似性是一种度量，用于确定文档的相似程度，而不考虑它们的大小。在数学上，它测量的是在多维空间中投影的两个向量之间的角度余弦。在这个上下文中，我所说的两个向量是包含两个文档字数的数组。余弦相似度作为一种相似度度量，和常用词的数量有什么不同？当绘制在多维空间上时，其中每个维度对应于文档中的一个单词，余弦相似性捕捉文档的方向(角度)而不是大小。如果你想知道大小，计算欧几里得距离。余弦相似性是有利的，因为即使两个相似的文档由于大小而相距欧几里德距离很远，它们之间仍然可以有较小的角度。角度越小，相似度越高。

## 第一条

```
documents = [document_1_0, document_1_1]
# Scikit Learn
from sklearn.feature_extraction.text import CountVectorizer
import pandas as pd

# Create the Document Term Matrix
count_vectorizer = CountVectorizer(stop_words='english')

sparse_matrix = count_vectorizer.fit_transform(documents)

# OPTIONAL: Convert Sparse Matrix to Pandas Dataframe if you want to see the word frequencies.
doc_term_matrix = sparse_matrix.todense()
df = pd.DataFrame(doc_term_matrix, 
                  columns=count_vectorizer.get_feature_names(), 
                  index=['true', 'false'])
df
```

![](img/342b8aba0138aab950caa2cd97072274.png)

```
# Compute Cosine Similarity
from sklearn.metrics.pairwise import cosine_similarity
print(cosine_similarity(df, df))[[1\.        0.9111977]
 [0.9111977 1\.       ]]
```

## 第二条

```
documents = [document_2_0, document_2_1]
# Create the Document Term Matrix
count_vectorizer = CountVectorizer(stop_words='english')
count_vectorizer = CountVectorizer()
sparse_matrix = count_vectorizer.fit_transform(documents)

# OPTIONAL: Convert Sparse Matrix to Pandas Dataframe if you want to see the word frequencies.
doc_term_matrix = sparse_matrix.todense()
df = pd.DataFrame(doc_term_matrix, 
                  columns=count_vectorizer.get_feature_names(), 
                  index=['true', 'false'])
# Compute Cosine Similarity
from sklearn.metrics.pairwise import cosine_similarity
print(cosine_similarity(df, df))[[1\.         0.86279596]
 [0.86279596 1\.        ]]
```

## 第三条

```
documents = [document_3_0, document_3_1]
# Create the Document Term Matrix
count_vectorizer = CountVectorizer(stop_words='english')
count_vectorizer = CountVectorizer()
sparse_matrix = count_vectorizer.fit_transform(documents)

# OPTIONAL: Convert Sparse Matrix to Pandas Dataframe if you want to see the word frequencies.
doc_term_matrix = sparse_matrix.todense()
df = pd.DataFrame(doc_term_matrix, 
                  columns=count_vectorizer.get_feature_names(), 
                  index=['true', 'false'])
# Compute Cosine Similarity
from sklearn.metrics.pairwise import cosine_similarity
print(cosine_similarity(df, df))[[1\.         0.98319208]
 [0.98319208 1\.        ]]
```

## 第四条

```
documents = [document_4_0, document_4_1]
# Create the Document Term Matrix
count_vectorizer = CountVectorizer(stop_words='english')
count_vectorizer = CountVectorizer()
sparse_matrix = count_vectorizer.fit_transform(documents)

# OPTIONAL: Convert Sparse Matrix to Pandas Dataframe if you want to see the word frequencies.
doc_term_matrix = sparse_matrix.todense()
df = pd.DataFrame(doc_term_matrix, 
                  columns=count_vectorizer.get_feature_names(), 
                  index=['true', 'false'])
# Compute Cosine Similarity
from sklearn.metrics.pairwise import cosine_similarity
print(cosine_similarity(df, df))[[1\.        0.7974359]
 [0.7974359 1\.       ]]
```

## 第五条

```
documents = [document_5_0, document_5_1]
# Create the Document Term Matrix
count_vectorizer = CountVectorizer(stop_words='english')
count_vectorizer = CountVectorizer()
sparse_matrix = count_vectorizer.fit_transform(documents)

# OPTIONAL: Convert Sparse Matrix to Pandas Dataframe if you want to see the word frequencies.
doc_term_matrix = sparse_matrix.todense()
df = pd.DataFrame(doc_term_matrix, 
                  columns=count_vectorizer.get_feature_names(), 
                  index=['true', 'false'])
# Compute Cosine Similarity
from sklearn.metrics.pairwise import cosine_similarity
print(cosine_similarity(df, df))[[1\.         0.71691335]
 [0.71691335 1\.        ]]
```

## 第六条

```
documents = [document_6_0, document_6_1]
# Create the Document Term Matrix
count_vectorizer = CountVectorizer(stop_words='english')
count_vectorizer = CountVectorizer()
sparse_matrix = count_vectorizer.fit_transform(documents)

# OPTIONAL: Convert Sparse Matrix to Pandas Dataframe if you want to see the word frequencies.
doc_term_matrix = sparse_matrix.todense()
df = pd.DataFrame(doc_term_matrix, 
                  columns=count_vectorizer.get_feature_names(), 
                  index=['true', 'false'])
# Compute Cosine Similarity
from sklearn.metrics.pairwise import cosine_similarity
print(cosine_similarity(df, df))[[1\.         0.73389937]
 [0.73389937 1\.        ]]
```

## 第七条

```
documents = [document_7_0, document_7_1]
# Create the Document Term Matrix
count_vectorizer = CountVectorizer(stop_words='english')
count_vectorizer = CountVectorizer()
sparse_matrix = count_vectorizer.fit_transform(documents)

# OPTIONAL: Convert Sparse Matrix to Pandas Dataframe if you want to see the word frequencies.
doc_term_matrix = sparse_matrix.todense()
df = pd.DataFrame(doc_term_matrix, 
                  columns=count_vectorizer.get_feature_names(), 
                  index=['true', 'false'])
# Compute Cosine Similarity
from sklearn.metrics.pairwise import cosine_similarity
print(cosine_similarity(df, df))[[1\.         0.62881668]
 [0.62881668 1\.        ]]documents = [document_4_0, document_5_0, document_6_0, document_7_0]
# Create the Document Term Matrix
count_vectorizer = CountVectorizer(stop_words='english')
count_vectorizer = CountVectorizer()
sparse_matrix = count_vectorizer.fit_transform(documents)

# OPTIONAL: Convert Sparse Matrix to Pandas Dataframe if you want to see the word frequencies.
doc_term_matrix = sparse_matrix.todense()
df = pd.DataFrame(doc_term_matrix, 
                  columns=count_vectorizer.get_feature_names(), 
                  index=['Set 4', 'Set 5', 'Set 6','Set 7'])
# Compute Cosine Similarity
from sklearn.metrics.pairwise import cosine_similarity
print(cosine_similarity(df, df))[[1\.         0.55025685 0.43467788 0.35961785]
 [0.55025685 1\.         0.38752486 0.31582201]
 [0.43467788 0.38752486 1\.         0.38250284]
 [0.35961785 0.31582201 0.38250284 1\.        ]]documents = [document_4_0, document_5_1, document_6_1, document_7_1]
# Create the Document Term Matrix
count_vectorizer = CountVectorizer(stop_words='english')
count_vectorizer = CountVectorizer()
sparse_matrix = count_vectorizer.fit_transform(documents)

# OPTIONAL: Convert Sparse Matrix to Pandas Dataframe if you want to see the word frequencies.
doc_term_matrix = sparse_matrix.todense()
df = pd.DataFrame(doc_term_matrix, 
                  columns=count_vectorizer.get_feature_names(), 
                  index=['Set 4', 'Set 5', 'Set 6','Set 7'])
# Compute Cosine Similarity
from sklearn.metrics.pairwise import cosine_similarity
print(cosine_similarity(df, df))[[1\.         0.61857347 0.45259309 0.55249671]
 [0.61857347 1\.         0.44449298 0.53149684]
 [0.45259309 0.44449298 1\.         0.43816624]
 [0.55249671 0.53149684 0.43816624 1\.        ]]
```

# 软余弦相似度

两个向量之间的软余弦或(“软”相似性)考虑特征对之间的相似性。传统的余弦相似度认为向量空间模型(VSM)特征是独立的或完全不同的，而软余弦度量提出考虑 VSM 特征的相似度，这有助于推广余弦(和软余弦)的概念以及(软)相似的思想。例如，在自然语言处理(NLP)领域，特征之间的相似性是非常直观的。诸如单词、n 元语法或句法 n 元语法之类的特征可能非常相似，尽管在形式上它们被认为是 VSM 中的不同特征。例如，单词“play”和“game”是不同的单词，因此映射到 VSM 的不同点；然而它们在语义上是相关的。在 n 元语法或句法 n 元语法的情况下，可以应用 Levenshtein 距离(事实上，Levenshtein 距离也可以应用于单词)。为了计算软余弦，矩阵 s 用于指示特征之间的相似性。它可以通过 Levenshtein 距离、WordNet 相似性或其他相似性度量来计算。然后我们乘以这个矩阵。

## 第一条

```
import gensim
documents = [document_1_0, document_1_1]
from gensim.matutils import softcossim 
from gensim import corpora
import gensim.downloader as api
from gensim.utils import simple_preprocess
fasttext_model300 = api.load('fasttext-wiki-news-subwords-300')[==================================================] 100.0% 958.5/958.4MB downloaded

/usr/local/lib/python3.6/dist-packages/smart_open/smart_open_lib.py:254: UserWarning: This function is deprecated, use smart_open.open instead. See the migration notes for details: https://github.com/RaRe-Technologies/smart_open/blob/master/README.rst#migrating-to-the-new-open-function
  'See the migration notes for details: %s' % _MIGRATION_NOTES_URL# Prepare a dictionary and a corpus.
dictionary = corpora.Dictionary([simple_preprocess(doc) for doc in documents])

# Prepare the similarity matrix
similarity_matrix = fasttext_model300.similarity_matrix(dictionary, tfidf=None, threshold=0.0, exponent=2.0, nonzero_limit=100)
print(similarity_matrix)

# Convert the sentences into bag-of-words vectors.
sent_1 = dictionary.doc2bow(simple_preprocess(document_1_0))
sent_2 = dictionary.doc2bow(simple_preprocess(document_1_1))
# Compute soft cosine similarity
print(softcossim(sent_1, sent_2, similarity_matrix))(0, 0)	1.0
  (1, 0)	0.057132058
  (2, 0)	0.10670497
  (3, 0)	0.12314428
  (4, 0)	0.07843615
  (5, 0)	0.17492798
  (6, 0)	0.13644238
  (7, 0)	0.16955109
  (8, 0)	0.07055851
  (9, 0)	0.05062564
  (11, 0)	0.07319155
  (12, 0)	0.008594441
  (13, 0)	0.077509716
  (14, 0)	0.17697306
  (15, 0)	0.07584241
  (16, 0)	0.035799537
  (17, 0)	0.14308827
  (18, 0)	0.079878114
  (19, 0)	0.047306582
  (20, 0)	0.10933455
  (21, 0)	0.053965475
  (22, 0)	0.07189872
  (23, 0)	0.057720024
  (24, 0)	0.10238695
  (25, 0)	0.13781747
  :	:
  (40, 65)	0.08728125
  (41, 65)	0.16906132
  (42, 65)	0.13730161
  (43, 65)	0.35975838
  (44, 65)	0.24721034
  (45, 65)	0.18764678
  (46, 65)	0.14564325
  (47, 65)	0.10063066
  (48, 65)	0.14522117
  (49, 65)	0.12855464
  (50, 65)	0.15765215
  (51, 65)	0.1680025
  (52, 65)	0.1930339
  (53, 65)	0.21249226
  (54, 65)	0.16988975
  (55, 65)	0.22988792
  (56, 65)	0.15349543
  (57, 65)	0.07669388
  (58, 65)	0.18887833
  (59, 65)	0.09025496
  (60, 65)	0.16519293
  (61, 65)	0.14934474
  (62, 65)	0.18598081
  (63, 65)	0.10408251
  (64, 65)	0.15317246
0.9907975401106488

/usr/local/lib/python3.6/dist-packages/gensim/matutils.py:737: FutureWarning: Conversion of the second argument of issubdtype from `int` to `np.signedinteger` is deprecated. In future, it will be treated as `np.int64 == np.dtype(int).type`.
  if np.issubdtype(vec.dtype, np.int):
```

## 第二条

```
documents = [document_2_0, document_2_1]
# Prepare a dictionary and a corpus.
dictionary = corpora.Dictionary([simple_preprocess(doc) for doc in documents])

# Prepare the similarity matrix
similarity_matrix = fasttext_model300.similarity_matrix(dictionary, tfidf=None, threshold=0.0, exponent=2.0, nonzero_limit=100)

# Convert the sentences into bag-of-words vectors.
sent_1 = dictionary.doc2bow(simple_preprocess(document_2_0))
sent_2 = dictionary.doc2bow(simple_preprocess(document_2_1))
# Compute soft cosine similarity
print(softcossim(sent_1, sent_2, similarity_matrix))0.9825814076550279

/usr/local/lib/python3.6/dist-packages/gensim/matutils.py:737: FutureWarning: Conversion of the second argument of issubdtype from `int` to `np.signedinteger` is deprecated. In future, it will be treated as `np.int64 == np.dtype(int).type`.
  if np.issubdtype(vec.dtype, np.int):
```

## 第三条

```
documents = [document_3_0, document_3_1]
# Prepare a dictionary and a corpus.
dictionary = corpora.Dictionary([simple_preprocess(doc) for doc in documents])

# Prepare the similarity matrix
similarity_matrix = fasttext_model300.similarity_matrix(dictionary, tfidf=None, threshold=0.0, exponent=2.0, nonzero_limit=100)

# Convert the sentences into bag-of-words vectors.
sent_1 = dictionary.doc2bow(simple_preprocess(document_3_0))
sent_2 = dictionary.doc2bow(simple_preprocess(document_3_1))
# Compute soft cosine similarity
print(softcossim(sent_1, sent_2, similarity_matrix))0.9977103651306122

/usr/local/lib/python3.6/dist-packages/gensim/matutils.py:737: FutureWarning: Conversion of the second argument of issubdtype from `int` to `np.signedinteger` is deprecated. In future, it will be treated as `np.int64 == np.dtype(int).type`.
  if np.issubdtype(vec.dtype, np.int):
```

## 第四条

```
documents = [document_4_0, document_4_1]
# Prepare a dictionary and a corpus.
dictionary = corpora.Dictionary([simple_preprocess(doc) for doc in documents])

# Prepare the similarity matrix
similarity_matrix = fasttext_model300.similarity_matrix(dictionary, tfidf=None, threshold=0.0, exponent=2.0, nonzero_limit=100)

# Convert the sentences into bag-of-words vectors.
sent_1 = dictionary.doc2bow(simple_preprocess(document_4_0))
sent_2 = dictionary.doc2bow(simple_preprocess(document_4_1))
# Compute soft cosine similarity
print(softcossim(sent_1, sent_2, similarity_matrix))/usr/local/lib/python3.6/dist-packages/gensim/matutils.py:737: FutureWarning: Conversion of the second argument of issubdtype from `int` to `np.signedinteger` is deprecated. In future, it will be treated as `np.int64 == np.dtype(int).type`.
  if np.issubdtype(vec.dtype, np.int):

0.8949769387024548
```

## 第五条

```
documents = [document_5_0, document_5_1]
# Prepare a dictionary and a corpus.
dictionary = corpora.Dictionary([simple_preprocess(doc) for doc in documents])

# Prepare the similarity matrix
similarity_matrix = fasttext_model300.similarity_matrix(dictionary, tfidf=None, threshold=0.0, exponent=2.0, nonzero_limit=100)

# Convert the sentences into bag-of-words vectors.
sent_1 = dictionary.doc2bow(simple_preprocess(document_5_0))
sent_2 = dictionary.doc2bow(simple_preprocess(document_5_1))
# Compute soft cosine similarity
print(softcossim(sent_1, sent_2, similarity_matrix))0.9460392429972865

/usr/local/lib/python3.6/dist-packages/gensim/matutils.py:737: FutureWarning: Conversion of the second argument of issubdtype from `int` to `np.signedinteger` is deprecated. In future, it will be treated as `np.int64 == np.dtype(int).type`.
  if np.issubdtype(vec.dtype, np.int):
```

## 第六条

```
documents = [document_6_0, document_6_1]
# Prepare a dictionary and a corpus.
dictionary = corpora.Dictionary([simple_preprocess(doc) for doc in documents])

# Prepare the similarity matrix
similarity_matrix = fasttext_model300.similarity_matrix(dictionary, tfidf=None, threshold=0.0, exponent=2.0, nonzero_limit=100)

# Convert the sentences into bag-of-words vectors.
sent_1 = dictionary.doc2bow(simple_preprocess(document_6_0))
sent_2 = dictionary.doc2bow(simple_preprocess(document_6_1))
# Compute soft cosine similarity
print(softcossim(sent_1, sent_2, similarity_matrix))0.9642978369414005

/usr/local/lib/python3.6/dist-packages/gensim/matutils.py:737: FutureWarning: Conversion of the second argument of issubdtype from `int` to `np.signedinteger` is deprecated. In future, it will be treated as `np.int64 == np.dtype(int).type`.
  if np.issubdtype(vec.dtype, np.int):documents = [document_7_0, document_7_1]
# Prepare a dictionary and a corpus.
dictionary = corpora.Dictionary([simple_preprocess(doc) for doc in documents])

# Prepare the similarity matrix
similarity_matrix = fasttext_model300.similarity_matrix(dictionary, tfidf=None, threshold=0.0, exponent=2.0, nonzero_limit=100)

# Convert the sentences into bag-of-words vectors.
sent_1 = dictionary.doc2bow(simple_preprocess(document_7_0))
sent_2 = dictionary.doc2bow(simple_preprocess(document_7_1))
# Compute soft cosine similarity
print(softcossim(sent_1, sent_2, similarity_matrix))/usr/local/lib/python3.6/dist-packages/gensim/matutils.py:737: FutureWarning: Conversion of the second argument of issubdtype from `int` to `np.signedinteger` is deprecated. In future, it will be treated as `np.int64 == np.dtype(int).type`.
  if np.issubdtype(vec.dtype, np.int):

0.9505847949707352documents = [document_1_0, document_1_1,document_2_0, document_2_1,document_3_0, document_3_1]
# Prepare a dictionary and a corpus.
dictionary = corpora.Dictionary([simple_preprocess(doc) for doc in documents])

# Prepare the similarity matrix
similarity_matrix = fasttext_model300.similarity_matrix(dictionary, tfidf=None, threshold=0.0, exponent=2.0, nonzero_limit=100)
print(similarity_matrix)
# Convert the sentences into bag-of-words vectors.
sent_1 = dictionary.doc2bow(simple_preprocess(document_1_0))
sent_2 = dictionary.doc2bow(simple_preprocess(document_1_1))
sent_3 = dictionary.doc2bow(simple_preprocess(document_2_0))
sent_4 = dictionary.doc2bow(simple_preprocess(document_2_1))
sent_5 = dictionary.doc2bow(simple_preprocess(document_3_0))
sent_6 = dictionary.doc2bow(simple_preprocess(document_3_1))
# Compute soft cosine similarity
print('Similarity between set 1 real and set 1 fake: ',softcossim(sent_1, sent_2, similarity_matrix))
print('Similarity between set 1 real and set 2 real: ',softcossim(sent_1, sent_3, similarity_matrix))
print('Similarity between set 1 real and set 2 fake: ',softcossim(sent_1, sent_4, similarity_matrix))
print('Similarity between set 1 real and set 3 real: ',softcossim(sent_1, sent_5, similarity_matrix))
print('Similarity between set 1 real and set 3 fake: ',softcossim(sent_1, sent_6, similarity_matrix))/usr/local/lib/python3.6/dist-packages/gensim/matutils.py:737: FutureWarning: Conversion of the second argument of issubdtype from `int` to `np.signedinteger` is deprecated. In future, it will be treated as `np.int64 == np.dtype(int).type`.
  if np.issubdtype(vec.dtype, np.int):

  (0, 0)	1.0
  (53, 0)	0.269355
  (1, 1)	1.0
  (56, 1)	0.47188094
  (58, 1)	0.38057277
  (3, 1)	0.3184986
  (25, 1)	0.35255837
  (57, 1)	0.32696036
  (130, 1)	0.25129354
  (2, 2)	1.0
  (5, 2)	0.43318766
  (6, 2)	0.40915966
  (28, 2)	0.43435976
  (45, 2)	0.42125136
  (61, 2)	0.5979465
  (3, 2)	0.27391726
  (3, 3)	1.0
  (1, 3)	0.3184986
  (2, 3)	0.27391726
  (7, 3)	0.34076366
  (24, 3)	0.28623286
  (28, 3)	0.29178333
  (31, 3)	0.2750326
  (51, 3)	0.2794037
  (56, 3)	0.28585052
  :	:
  (37, 123)	0.3409985
  (119, 123)	0.34883913
  (124, 124)	1.0
  (3, 124)	0.2793383
  (5, 124)	0.49403647
  (7, 124)	0.41360554
  (32, 124)	0.37957755
  (48, 124)	0.43871945
  (125, 125)	1.0
  (126, 126)	1.0
  (113, 126)	0.413245
  (127, 127)	1.0
  (128, 128)	1.0
  (106, 128)	0.40852967
  (111, 128)	0.46465328
  (129, 129)	1.0
  (102, 129)	0.43781716
  (130, 130)	1.0
  (1, 130)	0.25129354
  (58, 130)	0.21334913
  (131, 131)	1.0
  (52, 131)	0.44526622
  (53, 131)	0.40351504
  (120, 131)	0.34769118
  (132, 132)	1.0
Similarity between set 1 real and set 1 fake:  0.9561104452967236
Similarity between set 1 real and set 2 real:  0.6064600254922445
Similarity between set 1 real and set 2 fake:  0.6401801333554172
Similarity between set 1 real and set 3 real:  0.7197187246530167
Similarity between set 1 real and set 3 fake:  0.7329004394401343documents = [document_4_0, document_4_1,document_5_0, document_5_1,document_6_0, document_6_1,document_7_0, document_7_1]
# Prepare a dictionary and a corpus.
dictionary = corpora.Dictionary([simple_preprocess(doc) for doc in documents])

# Prepare the similarity matrix
similarity_matrix = fasttext_model300.similarity_matrix(dictionary, tfidf=None, threshold=0.0, exponent=2.0, nonzero_limit=100)
print(similarity_matrix)
# Convert the sentences into bag-of-words vectors.
sent_1 = dictionary.doc2bow(simple_preprocess(document_4_0))
sent_2 = dictionary.doc2bow(simple_preprocess(document_4_1))
sent_3 = dictionary.doc2bow(simple_preprocess(document_5_0))
sent_4 = dictionary.doc2bow(simple_preprocess(document_5_1))
sent_5 = dictionary.doc2bow(simple_preprocess(document_6_0))
sent_6 = dictionary.doc2bow(simple_preprocess(document_6_1))
sent_7 = dictionary.doc2bow(simple_preprocess(document_7_0))
sent_8 = dictionary.doc2bow(simple_preprocess(document_7_1))
# Compute soft cosine similarity
print('Similarity between set 1 real and set 1 fake: ',softcossim(sent_1, sent_2, similarity_matrix))
print('Similarity between set 1 real and set 2 real: ',softcossim(sent_1, sent_3, similarity_matrix))
print('Similarity between set 1 real and set 2 fake: ',softcossim(sent_1, sent_4, similarity_matrix))
print('Similarity between set 1 real and set 3 real: ',softcossim(sent_1, sent_5, similarity_matrix))
print('Similarity between set 1 real and set 3 fake: ',softcossim(sent_1, sent_6, similarity_matrix))/usr/local/lib/python3.6/dist-packages/gensim/matutils.py:737: FutureWarning: Conversion of the second argument of issubdtype from `int` to `np.signedinteger` is deprecated. In future, it will be treated as `np.int64 == np.dtype(int).type`.
  if np.issubdtype(vec.dtype, np.int):

  (0, 0)	1.0
  (6, 0)	0.34844103
  (75, 0)	0.38856554
  (93, 0)	0.3464246
  (105, 0)	0.3964237
  (129, 0)	0.37776864
  (56, 0)	0.3360912
  (107, 0)	0.33096197
  (139, 0)	0.33437905
  (237, 0)	0.3299397
  (1, 1)	1.0
  (2, 2)	1.0
  (35, 2)	0.33962697
  (84, 2)	0.31973574
  (143, 2)	0.2928415
  (3, 3)	1.0
  (118, 3)	0.44548658
  (125, 3)	0.542848
  (254, 3)	0.37505317
  (24, 3)	0.311034
  (164, 3)	0.3202444
  (4, 4)	1.0
  (36, 4)	0.36854532
  (56, 4)	0.34207016
  (93, 4)	0.4323508
  :	:
  (49, 251)	0.35305354
  (201, 251)	0.3053905
  (249, 251)	0.3628248
  (252, 252)	1.0
  (129, 252)	0.40784162
  (253, 253)	1.0
  (239, 253)	0.3485727
  (254, 254)	1.0
  (3, 254)	0.37505317
  (125, 254)	0.39192784
  (255, 255)	1.0
  (36, 255)	0.39253923
  (45, 255)	0.5456714
  (107, 255)	0.34599632
  (139, 255)	0.42906368
  (148, 255)	0.3516806
  (164, 255)	0.26543584
  (208, 255)	0.40348202
  (237, 255)	0.43203592
  (76, 255)	0.38168862
  (93, 255)	0.34062588
  (256, 256)	1.0
  (257, 257)	1.0
  (19, 257)	0.3910559
  (20, 257)	0.5127834
Similarity between set 1 real and set 1 fake:  0.8949769387024548
Similarity between set 1 real and set 2 real:  0.7253979310460288
Similarity between set 1 real and set 2 fake:  0.7909116399656686
Similarity between set 1 real and set 3 real:  0.7092782752937434
Similarity between set 1 real and set 3 fake:  0.7230690011066724
```

这是余弦和软余弦的主要区别。软余弦相似性还包括特征之间的相似性。如果所有特征之间的相似性为 1，则软余弦将表现为余弦相似性方法。