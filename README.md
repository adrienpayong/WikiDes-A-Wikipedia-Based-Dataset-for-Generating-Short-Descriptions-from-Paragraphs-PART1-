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

- **Two-phase summarization approaches**
