## Review - WikiDes: A Wikipedia-Based Dataset for Generating Short Descriptions from Paragraphs(PART1)

## Introduction

The process of text summarizing entails reducing a lengthy document to its important points. The task can be monolingual or cross-lingual. The monolingual task has been handled for languages other than English. A dataset is build  by matching a document with a summary; the length of each might vary depending on the intended use. Free online resources like Wikipedia and Wikidata provide large-size and diversified material to collect information for summarizing tasks. Wikidata entries are distinguished from one another by a brief description phrase that serves to differentiate across entries with the same or similar labels. We observe a high correlation between Wikidata descriptions and Wikipedia articles, especially in the first paragraphs. Thus, we want to create a unique dataset called WikiDes to generate short descriptions as summaries from the first paragraphs as document. WikiDes is a monolingual dataset with over 80k English samples with 6987 instances as topics, extracted data from both Wikipedia and Wikidata.

## Why WikiDes ?

Since Wikipedia and Wiki-data have grown so rapidly in recent years, editors have been slammed with the enormous task of constantly updating the site with fresh material, tailoring it to the needs of its users, and monitoring its large database of information.
So, using natural language processing and deep learning to address these issues is critical. In this paper, the provide a WikiDes-trained summarization strategy that generates missing descriptions in thousands of Wikidata items, speeding up content generation while reducing human involvement. Instead of having to start from scratch, you can just have the summarizer create descriptions while humans act as quality controllers.

## Different types of summarization

In their research-based overviews of text summarizing systems, several authors have alluded to the fact that there are many types of summarization that rely on user needs. There are two types of summarization that may be categorized by the information they provide:

- **Indicative summarization**: Indicative summarization methods typically extract between 5 and 10 percent of a document's content as its central idea. Due to the limited scope of a summary of this kind, it is intended to pique the reader's interest enough to keep them reading.

- **Informative summarization**: Informative summarization systems provide a brief version that may stand in for the original document. Here, you can find a publicly-accessible English dataset where the input is the first paragraphs of Wikipedia articles and the output is the corresponding Wikidata description.

## Two-phase summarization approaches

To further enhance the generation performance afforded by contrastive learning and beam search, the researchers use a two-phase summarization strategy consisting of description generation and candidate ranking. Consequently, the summary task is less "severe" since the resulting descriptions capture more of the essential information from paragraphs.

## The Main Contributions

- **Dataset creation**: For anyone interested in researching Wikipedia summarization, researchers have made a dataset available on [GitHub](https://github.com/declare-lab/WikiDes).
Setting up a trending approach: To enhance the caliber of the generated summaries, they use a two-stage summary strategy, consisting of description generation and candidate ranking.

- **Sentiment correlation**: They measure the correlations of the generated descriptions versus the paragraphs and the gold descriptions by comparing their sentiment polarities on cumulative distribution and the Kolmogorov-Smirnov test.

## Related Works

Here we describe current datasets and deep learning algorithms for text summarization, not only in wiki text but in various areas. Some noteworthy methods for incorporating sentiment analysis into text summarizing are also described.

### Datasets Extracted from Wikipedia and Wikidata

- Datasets may be either monolingual or multilingual, and both gather information from Wikipedia and Wikidata in the form of articles and knowledge graphs represented as RDF triples. Since millions of editors worked together to create the English Wikipedia, it is the language most often used for monolingual datasets. Another argument is that, as Wikipedia is available in up to 327 different languages, multilingual datasets accurately reflect the encyclopedia's multilingual strength. Monolingual datasets are built from several popular languages, of which English and German are two typical examples.
- To create a dataset in English, Anjalie et al. collected 14.4M articles with section titles and their content. The purpose of the summary task is to build a title out of the content in a specific section.
- A substantial corpus of 240,000 texts from the German Wikipedia was gathered by [Frefel](https://aclanthology.org/2020.lrec-1.821.pdf). The first paragraph of each article was considered as a summary, while the remaining content as an actual document.
- WIKIREF is a large query-focused summarization dataset collected from Wikipedia articles by [Haichao et al](https://arxiv.org/abs/1911.03324). The dataset contains more than 280,000 examples. The information synthesis approach used by Wikipedia editors is useful to this study.

Some monolingual datasets have multi-document summarization (MDS). A new heterogeneous and multi-genre corpus for MDS was suggested by [Zopf et al](https://aclanthology.org/C16-1145.pdf). The same author improved upon this paper by creating auto-MDS, a multilingual multi-document summarization (MMS) dataset.

### The Need of Cross-lingual Datasets

Pseudo-crosslingual summarization data can be generated by machine translation systems to convert a single-language dataset into a multilingual one. The translation procedure introduces potential noise into the data, hence it is preferable to generate cross-lingual datasets without translation. 
- [Mehwish and Strube](https://aclanthology.org/2021.newsum-1.5.pdf) gathered a bilingual corpus of 51,312 English and German scientific articles from the Spektrum der Wissenschaft and the Wikipedia Science Portals (WSP).
- Using Wikipedia's body paragraphs and leading paragraphs as document-summary pairs, [Laura and Lapata](https://aclanthology.org/2021.emnlp-main.742.pdf) created the cross-lingual dataset XWikis, which includes 12 languages.
- Over time, [Pavel and Malykh](https://arxiv.org/pdf/2204.11104.pdf) collected quality content from Wikipedia to create WikiMulti. Each article begins with a brief synopsis, and the rest of it is a document. WikiMulti contains 22,061 unique English articles and9,639 articles on average in other languages that align with English articles.

## Other Summarization Datasets
The Document Understanding Conference (DUC) and the Text Analysis Conference (TAC) datasets created by NIST are among the earliest and most significant.

- **DUC**: [DUC](https://aclanthology.org/W05-0909/) had a series from 2001–2007, then became a Summarization track of TAC in 2008. They both focused on generic and question summaries of English newspapers and newswire articles. DUC contains two evaluation methods: a baseline by an automatic system in NIST and human evaluation by the linguistic quality and conciseness
- **Gigaword**: Gigaword is an available large-scale corpus of English news with nearly 10 million documents from seven news outlets.
- **New York Times**: [NYT(New York Times)](https://catalog.ldc.upenn.edu/LDC2008T19) has over 65,0000 articles-summary pairs while CNN/DailyMail newspapers(or CNN/DM) is more popular and contain 93K articles from CNN (Cable News Network) and 220K articles from DailyMail.
- **Newsroom**: [Newsroom](https://arxiv.org/abs/1804.11283) is another large-scale dataset in the news domain, with 1.3 million summaries collected from 38 news publishers.
- **XSum**: [XSum](https://arxiv.org/pdf/1808.08745.pdf) is similar to our dataset WikiDes in terms of extreme summarization when generating a short, one-sentence news summary that just answers the question "What is the article about?". n our case, we generate a short description that can represent a given paragraph by taking the salient information.
- **WikiHow**: [WikiHow](https://arxiv.org/abs/1810.09305) is a huge database with about 230,000 unique article-summary pairs. WikiHow's reference summaries and their corresponding source articles have few n-gram features. A high-quality summary is more challenging to produce when there are more differences (in terms of n-grams) between the reference summary and the original source articles.
- **Arxiv and PubMed**: In the academic domain, Arxiv and [PubMed](https://arxiv.org/abs/1710.06071) are summarization datasets with coherent paragraph summaries in scientific writing styles, and the document length is significantly longer than the one in the news domain. The content of arXiv and PubMed was retrieved from scientific papers on arXiv.org and PubMed.com.
- **BIGPATENT**: [BIGPATENT](https://aclanthology.org/P19-1212/)) contains 1.3 million records of U.S. patent documents and human-written abstractive summaries.
- **Multi-XScience**: [Multi-XScience](https://arxiv.org/abs/2010.14235) is also a large-scale MDS dataset collected from scientific articles. It brings a challenge for the MDS task: given a paper, generate a related-work section from the paper abstract and the abstracts of reference pieces.

## Deep Learning Approaches for Text Summarization

Since its inception, text summarization has been an established NLP task, inspiring various solutions to the challenges it presents. Some well-known approaches include: Statistical-based approaches, topic-based approaches:

- [LSA](https://www.researchgate.net/publication/220017752_Using_Latent_Semantic_Analysis_in_Text_Summarization_and_Summary_Evaluation)
- [topic themes](https://dl.acm.org/doi/10.1145/1076034.1076071)

graphs-based approaches:

- [LexRank](https://arxiv.org/abs/1109.2128)
- [TextRank](https://aclanthology.org/W04-3252/)
- [Opinosis](https://aclanthology.org/C10-1039/)
- [GraphSum](https://core.ac.uk/download/pdf/76522123.pdf)
- [Approaches based on machine learning](https://dl.acm.org/doi/10.1007/s10462-016-9475-9)

- **Encode-decoder architectures**: Various deep learning techniques use encoder-decoder architectures for summarization tasks. In abstractive summarization, an attention-based encoder-decoder model was employed by [Alexander M. et al.](https://aclanthology.org/D15-1044.pdf) and [Ramesh et al.](https://aclanthology.org/K16-1028.pdf) Reproduction of inaccurate factual facts and repeated text chunks are two common problems that arise when using a neural sequence-to-sequence model.

- To address these issues, [See et al.](https://aclanthology.org/P17-1099/) proposed a pointer-generator network (PGN) to point to copy words from the source documents, which would aid in the reproduction of accurate information and help to prevent unnecessary repetition when keeping track of the sentences discussed in the document.
- **Gated Recurrent Unit(GRU)** recurrent neural network-based (RNN): Ramesh et al. introduced a two-layer bidirectional Gated Recurrent Unit (GRU) recurrent neural network-based (RNN) classifier to generate the extractive summary according to the content richness of each sentence and saliency according to the overall document.
- **convolutional neural networks(CNN)**: With the use of convolutional neural networks, [Narayanet al.](https://arxiv.org/abs/1808.08745) developed a topic-conditioned neural model (CNN). Convolution layers, in contrast to RNNs, are better at preserving long-range dependencies between words and enabling inference, abstraction, and paraphrasing at the document level.
- Transformers:[Transformers](https://aclanthology.org/2020.emnlp-demos.6.pdf) has emerged as a powerful tool for building high-capacity models using transformer architecture and applying pretraining to a wide range of natural language processing (NLP) tasks, including text summarization. This library provides various pre-trained models for text summarizing, including:

- [BERT](https://arxiv.org/abs/1903.10318)
- [BART](https://arxiv.org/abs/1910.13461)
- [T5](https://arxiv.org/pdf/1910.10683.pdf)
- [PEGASUS](https://arxiv.org/pdf/1912.08777.pdf)

This enables researchers to broaden their training on text summarization datasets beyond academia and into the industry. Some works used transfer learning from these pre-trained models to do downstream tasks, rather than spending additional effort training datasets. Shusheng et al. used contrastive learning in summarization tasks by maximizing the similarities of the same semantic meaning articles.

To enhance the quality of the output texts, [Liu and Liu](https://arxiv.org/abs/2106.01890) used BART and RoBERTa in a two-phase summarization process to build and score candidate summaries that were produced using [diverse beam search](https://arxiv.org/abs/1610.02424).
Two-phase summarization's strength resides in its decoding technique, which makes use of beam search and other superior methods such as [nucleus sampling]( https://arxiv.org/abs/1904.09751) where diverse data creates more opportunities to search for an "ideal" candidate. In one of the most recent works, [Liu et al.](https://aclanthology.org/2022.acl-long.207/) followed a new training paradigm that assigns probabilities of candidate summaries concerning to their quality in contrastive learning. Different summarizing works using contrastive learning have been done. In addition, there are different approaches, including:

1- [few-shot and zero-shot learning](https://dl.acm.org/doi/abs/10.1016/j.csl.2021.101276)
2- [reinforcement learning](https://dl.acm.org/doi/abs/10.1016/j.csl.2021.101276)
3- [prompting](https://arxiv.org/abs/2107.06955)
4- [prefix-tuning on massive-scale models (GTP-2)](https://arxiv.org/abs/2101.00190)
5- hybrid approaches

### Sentiment Analysis in Text Summarization

The purpose of a conventional and ideal summary is to convey the most important points of a document. However, the document's emotional tone, which is essential in datasets like IMDB's movie reviews, may be missing.
Sentiment analysis is integrated into text summarization models to better capture sentiment. Extracting negative, neutral, and positive sentiment polarity from texts is one method of integration that enables us to turn sentiment analysis into a problem of text sentiment classification.

- Aspect-based sentiment summarization (ABSA) is another method for integrating sentiment analysis into text summary; it consists of two tasks: aspect identification with mention extraction and sentiment classification.
- A concept called Aspect-based Opinion Summarization (AOS) was mentioned by [Wu et al.](https://arxiv.org/abs/1511.09128) which performs the same functions as ASBA.
- [Titov and McDonald](https://aclanthology.org/P08-1036/) proposed a joint model of text and aspect ratings which use the Multi-Aspect Sentiment model (MAS) to form representative aspects as topics and a set of sentiment predictors to illustrate topic-aspect correlations.
- In another work, [Dhanush et al.](https://www.ijert.org/aspect-based-sentiment-summarization-with-deep-neural-networks) designed an RNN for extracting aspects with contexts in a sentence and a CNN for sentiment classification at the sentence level.
- [Nishikawa et al.](https://aclanthology.org/P10-2060/) addressed informativeness and readability in restaurant reviews. They set up an algorithm to create a summary by choosing and arranging sentences by informativeness and readability scores.
- Since many texts in WikiDes are neutral due to Wikipedia's neutrality policy, researchers use cumulative distribution and the [Kolmogorov-Smirnov test](https://r-forge.r-project.org/scm/viewvc.php/*checkout*/pkg/literature/1951-jamsta-massey-kolmsmirntest.pdf?root=glogis) to establish whether or not descriptions and paragraphs share a similar sentiment polarity rather than relying on sentiment summarization methods.
- The Kolmogorov-Smirnov test is not the only approach for comparing distributions across multiple sets; the [chi-squared test](https://floppybunny.org/robin/web/virtualclassroom/stats/basics/articles/chi_square/chi_square_review_plackett_1983.pdf), the [Mann-Whitney U test](https://onlinelibrary.wiley.com/doi/abs/10.1002/9780470479216.corpsy0524), and the Fisher's z-test are other valid alternatives.

## Data creation

JSON data were gathered using the APIs of Wikidata and English Wikipedia. To counteract the use of topic bias in WikiDes, Algorithm 1 randomly selects samples. To determine the topic of Wikidata items, the researchers look at their is-a or instance-of attribute. Because there are no related articles in Wikipedia, they remove the Wikidata items for the following topics:

- Scholarly article
- Wikimedia disambiguation page
- Wikinews article

### Description of the Algorithm

- A while loop is used to get output samples S, where N is the required number of samples.
- An id between 1 and 99 million is created at random for each iteration.
- If the id is not found in list K, then you should proceed to gather data from Wikidata and Wikipedia to build a sample.
- The sample is then checked for validity using criteria such as paragraph and description lengths.
- If it's a representative sample, put it in S. Otherwise, the algorithm will keep iterating through the while loop until the total number of samples, S, is equal to the input value, N.
- For each item in Wikidata, the crawler extracts a label, a short description, instances, and a site link or interwiki link. This link leads to an article in English Wikipedia, where the crawler can gather the first paragraph.
- Because it is expected that special symbols and unnecessary spaces do not significantly contribute to the model performance during description generation, the researchers apply a few pre-processing techniques to paragraphs and descriptions to eliminate them. Samples with empty descriptions or paragraphs with less than 10 tokens are also thrown out.

![source](https://github.com/adrienpayong/object-detection/blob/main/algo.png)

- Articles that redirect to a representative article that doesn't cover the same subject in its first paragraph are removed.
- The researchers use the package NLTK punkt to extract the first sentences from the first paragraphs. Since they needed to access APIs online, they set the crawler's max workers to 8 to increase its throughput. 
- The dataset for this research was collected in less than 72 hours, and it contains 81,418 English samples over 6,987 topics.

## The Research Objective

Figure 1 depicts a typical sample, which consists of the Wikidata description "river system in North America" and the first paragraph of the related Wikipedia article: "The Mississippi River is the second-longest river and chief river of the second largest drainage system in North America…" The goal of the challenge is to generate this description using the provided paragraph.

![source](https://github.com/adrienpayong/object-detection/blob/main/objective.PNG)

## Conclusion

In this paper, we introduced WikiDes, a novel summarization dataset with over 80k samples on 6987 topics created by collecting data from Wikipedia and Wikidata. The dataset aims to produce short descriptions
from the given paragraphs. We have described current datasets and deep learning algorithms for text summarization, not only in wiki text but in various domains. Some noteworthy methods for incorporating sentiment analysis into text summarizing were also described. In the next article, we will explain how analyses on WikiDes were performed.

## Reference

Wikipedia-Based Dataset for Generating Short Descriptions
from Paragraphs: https://arxiv.org/pdf/2209.13101v1.pdf


