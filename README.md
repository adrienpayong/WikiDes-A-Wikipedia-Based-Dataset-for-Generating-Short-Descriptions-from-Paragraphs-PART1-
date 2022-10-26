## Review - WikiDes: A Wikipedia-Based Dataset for Generating Short Descriptions from Paragraphs(PART1)

##Introduction

The process of text summarizing entails reducing a lengthy document to its essential points. The task can be monolingual or cross-lingual. The monolingual job has been handled for languages other than English. A dataset is constructed by matching a document with a summary; the length of each might vary depending on the intended use. Free online resources like Wikipedia and Wikidata provide large-size and diversified material to collect information for summarizing jobs. Wikidata entries are distinguished from one another by a brief description phrase that serves to differentiate across entries with identical or almost identical labels. We find that the initial paragraphs of Wikidata descriptions and Wikipedia articles are highly correlated.

Thus, we want to create a unique dataset called WikiDes to generate concise summaries from the initial paragraphs of a document. WikiDes is a monolingual dataset with over 80k English samples with 6987 instances as topics, extracted data from both Wikipedia and Wikidata.

## Why WikiDes ?

Since Wikipedia and Wiki-data have grown so rapidly in recent years, editors have been slammed with the enormous task of constantly updating the site with fresh material, tailoring it to the needs of its users, and monitoring its large database of information.
So, using natural language processing and deep learning to address these issues is critical. In this paper, we provide a WikiDes-trained summarization strategy that generates missing descriptions in thousands of Wikidata items, speeding up content generation while reducing human involvement. Instead of having to start from scratch, you can just have the summarizer create descriptions while humans act as quality controllers.

## Different types of summarization

In their research-based overviews of text summarizing systems, several authors have alluded to the fact that there are many types of summarization that rely on user needs. There are two types of summarization that may be categorized by the information they provide:

- **Indicative summarization**: Indicative summarization methods typically extract between 5 and 10 percent of a document's content as its central idea. Due to the limited scope of a summary of this kind, it is intended to pique the reader's interest enough to keep them reading..

- **Informative summarization**: Informative summarization systems provide a brief version that may stand in for the original document. Here, you can find a publicly-accessible English dataset where the input is the first paragraphs of Wikipedia articles and the output is the corresponding Wikidata description.

## Two-phase summarization approaches

To further enhance the generation performance afforded by contrastive learning and beam search, the researchers use a two-phase summarization strategy consisting of description generation and candidate ranking. Consequently, the summary task is less "severe" since the resulting descriptions capture more of the essential information from paragraphs.

## The Main Contributions

- **Dataset creation**: For anyone interested in researching Wikipedia summarization, researchers have made a dataset available on GitHub.
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

Pseudo-crosslingual summarization data can be generated by machine translation systems to convert a single-language dataset into a multilingual one. The translation procedure introduces potential noise into the data, hence it is preferable to generate cross-lingual datasets without translation. The translation procedure introduces potential noise into the data, hence it is preferable to generate cross-lingual datasets without translation.

- [Mehwish and Strube](https://aclanthology.org/2021.newsum-1.5.pdf) gathered a bilingual corpus of 51,312 English and German scientific articles from the Spektrum der Wissenschaft and the Wikipedia Science Portals (WSP).
- Using Wikipedia's body paragraphs and leading paragraphs as document-summary pairs, [Laura and Lapata](https://aclanthology.org/2021.emnlp-main.742.pdf) created the cross-lingual dataset XWikis, which includes 12 languages.
- Over time, [Pavel and Malykh](https://arxiv.org/pdf/2204.11104.pdf) collected quality content from Wikipedia to create WikiMulti. Each article begins with a brief synopsis, and the rest of it is a document. WikiMulti contains 22,061 unique English articles and9,639 articles on average in other languages that align with English articles.


